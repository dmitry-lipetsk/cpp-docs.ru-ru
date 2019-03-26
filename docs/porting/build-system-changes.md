---
title: Изменения системы сборки в Visual Studio 2010
ms.date: 11/04/2016
f1_keywords:
- vc.msbuild.changes
helpviewer_keywords:
- Build system changes, project file (.vcxprog)
- Build system changes, custom build rules
- Build system changes, MSBuild
- MSBuild, build system changes
- Build system changes, .vsprops
- Build system changes, $(Inherit)
- Build system changes, $(NoInherit)
ms.assetid: e564d95f-a6cc-4d97-b57e-1a71daf66f4a
ms.openlocfilehash: 621e62379657da66d6eaec7a3ceff780fd610066
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/14/2019
ms.locfileid: "57828180"
---
# <a name="build-system-changes"></a>Изменения системы построения

Система MSBuild используется для сборки проектов Visual C++. Однако в Visual Studio 2008 и более ранних выпусках использовалась система VCBuild. Определенные типы файлов и основные понятия, которые зависят от VCBuild, не существуют или представляются иначе в текущей системе. В этом документе описываются различия в текущей системе сборки.

## <a name="vcproj-is-now-vcxproj"></a>Вместо VCPROJ теперь используется VCXPROJ

Файлы проекта больше не имеют расширение имени файла VCPROJ. Visual Studio автоматически преобразует файлы проекта, которые были созданы в более ранней версии Visual C++, в формат, который используется в текущей системе. Дополнительные сведения о том, как вручную обновить проект, см. в разделе [/Upgrade (devenv.exe)](/visualstudio/ide/reference/upgrade-devenv-exe).

В текущем выпуске расширение имени файла для файла проекта — VCXPROJ.

## <a name="vsprops-is-now-props"></a>VSPROPS заменен на PROPS

В более ранних выпусках *страница свойств проекта* представляет собой XML-файл с расширением VSPROPS. Страница свойств проекта позволяет указывать параметры для средств сборки, например, параметры компилятора или компоновщика, и создавать пользовательские макросы.

В текущем выпуске расширение имени файла для страницы свойств проекта — PROPS.

## <a name="custom-build-rules-and-rules-files"></a>Настраиваемые правила сборки и RULES-файлы

В более ранних выпусках *файл правил* представляет собой XML-файл с расширением RULES. Файл правил позволяет определять настраиваемые правила сборки и внедрять их в процесс сборки проекта Visual C++. Настраиваемое правило сборки, которое может быть связано с одним или несколькими расширениями файлов, позволяет передавать входные файлы в средство, которое создает один или несколько выходных файлов.

В этом выпуске настраиваемые правила сборки представлены тремя типами файлов (XML, PROPS и TARGETS) вместо файла RULES. При миграции файла RULES, который был создан с помощью более ранней версии Visual C++, в текущий выпуск создаются эквивалентные файлы XML, PROPS и TARGETS, которые хранятся в проекте вместе с исходным RULES-файлом.

> [!IMPORTANT]
>  В текущем выпуске интегрированная среда разработки не поддерживает создание новых правил. По этой причине самый простой способ использования файла правил из проекта, который был создан с помощью более ранней версии Visual C++, — перенести проект в текущий выпуск.

## <a name="inheritance-macros"></a>Макросы наследования

В более ранних выпусках макрос **$(Inherit)** указывает порядок, в котором отображаются наследуемые свойства в командной строке, созданной системой сборки проекта. Макрос **$(NoInherit)** указывает, что нужно пропускать все вхождения $(Inherit) и не наследовать свойства, которые наследовались бы в противном случае. Например, по умолчанию макрос $(Inherit) добавляет к командной строке файлы, указанные с помощью параметра компилятора [/I (дополнительные каталоги включаемых файлов)](../build/reference/i-additional-include-directories.md).

В текущем выпуске наследование поддерживается с помощью значения свойства в качестве объединения одного или нескольких значений литералов и макросов свойств. Макросы **$(Inherit)** и **$(NoInherit)** не поддерживаются.

В следующем примере список с разделением точкой с запятой назначается свойству на странице свойств. Список состоит из объединения литерала *\<значения>* и значения свойства `MyProperty`, которое используется с помощью нотации макроса **$(** <em>MyProperty</em>**)**.

```
Property=<value>;$(MyProperty)
```

## <a name="vcxprojuser-files"></a>Файлы VCXPROJ.USER

Файл пользователя (VCXPROJ.USER) хранит свойства конкретного пользователя, например, параметры отладки и развертывания. Файл VCXPROJ.USER применяется ко всем проектам для конкретного пользователя.

## <a name="vcxprojfilters-file"></a>Файл VCXPROJ.FILTERS

Если для добавления файла в проект используется **обозреватель решений**, файл фильтров определяет, в какое место дерева **обозревателя решений** будет добавлен файл VCXPROJ.FILTERS, по расширению имени файла.

## <a name="vc-directories-settings"></a>Параметры каталогов VC++

Параметры каталогов Visual C++ указываются на [странице свойств каталогов VC ++](../ide/vcpp-directories-property-page.md). В более ранних выпусках Visual Studio параметры каталогов применяются для каждого пользователя, а список исключаемых каталогов указывается в файле SYSINCL.DAT.

Невозможно изменить параметры каталогов VC++ при запуске [devenv/resetsettings](/visualstudio/ide/reference/resetsettings-devenv-exe) в командной строке. Также нельзя изменить параметры в меню **Сервис**, **Импорт и экспорт параметров**, **Сбросить все параметры**.

Перенесите параметры каталогов VC++ из файла VSSETTINGS, созданного в более ранних выпусках Visual C++. Откройте меню **Сервис**, щелкните **Импорт и экспорт параметров**, выберите **Импортировать выбранные параметры среды** и следуйте указаниям мастера. Или при первом запуске Visual Studio в диалоговом окне **Выбор параметров среды по умолчанию** выберите **Перенести параметры из предыдущей версии и применить их вместе с параметрами по умолчанию, выбранными ниже**.

## <a name="see-also"></a>См. также

[MSBuild в командной строке — C++](../build/msbuild-visual-cpp.md)