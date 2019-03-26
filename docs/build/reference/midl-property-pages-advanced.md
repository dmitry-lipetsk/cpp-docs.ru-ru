---
title: 'Страницы свойств MIDL: Дополнительно'
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCMidlTool.ErrorCheckBounds
- VC.Project.VCMidlTool.ErrorCheckStubData
- VC.Project.VCMidlTool.ErrorCheckAllocations
- VC.Project.VCMidlTool.CPreprocessOptions
- VC.Project.VCMidlTool.UndefinePreprocessorDefinitions
- VC.Project.VCMidlTool.EnableErrorChecks
- VC.Project.VCMidlTool.RedirectOutputAndErrors
- VC.Project.VCMidlTool.ErrorCheckEnumRange
- VC.Project.VCMidlTool.StructMemberAlignment
- VC.Project.VCMidlTool.ErrorCheckRefPointers
- VC.Project.VCMidlTool.ValidateParameters
helpviewer_keywords:
- MIDL, property pages
ms.assetid: d1c92e01-f403-4ed6-ab45-4043a3c9c6bb
ms.openlocfilehash: 350563d140823910667812930f9283c7640cc1ff
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/14/2019
ms.locfileid: "57826776"
---
# <a name="midl-property-pages-advanced"></a>Страницы свойств MIDL: Дополнительно

Страница свойств **Дополнительно** в папке **MIDL** указывает следующие параметры компилятора MIDL:

- Разрешить проверку ошибок ([/error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- Проверка ошибок нехватки памяти ([/error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- Проверка границ ([/error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- Проверка границ перечислений ([/error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- Проверка указателей ([/error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- Проверках данных-заглушек ([/error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- Проверка параметров ([/robust](https://msdn.microsoft.com/library/windows/desktop/aa367363)) \*

- Выравнивание членов структур ([/Zp](https://msdn.microsoft.com/library/windows/desktop/aa367388))

- Перенаправить вывод ([/o](https://msdn.microsoft.com/library/windows/desktop/aa367351))

- Параметры препроцессора C ([/cpp_opt](https://msdn.microsoft.com/library/windows/desktop/aa367318))

- Отменить определения препроцессора ([/U](https://msdn.microsoft.com/library/windows/desktop/aa367373))

\* /robust предназначен для использования только при сборке для компьютера с Windows 2000 или более поздней версии. Если вы выполняете сборку проекта ATL и хотите использовать /robust, измените следующую строку в файле dlldatax.c:

```
#define _WIN32_WINNT 0x0400   //for Windows NT 4.0 or Windows 95 with DCOM
to
#define _WIN32_WINNT 0x0500   //for Windows NT 4.0 or Windows 95 with DCOM
```

Сведения о том, как получить доступ к **Дополнительно** страницы свойств в **MIDL** папки, см. в разделе [свойств компилятора и собранной задать C++ в Visual Studio](../working-with-project-properties.md).

Сведения о программном доступе к параметрам MIDL для проектов C++ см. в разделе <xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool>.

## <a name="see-also"></a>См. также

[Страницы свойств MIDL](midl-property-pages.md)