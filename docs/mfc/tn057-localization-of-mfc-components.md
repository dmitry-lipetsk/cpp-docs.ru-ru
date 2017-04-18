---
title: "TN057. Локализация компонентов MFC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.components"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "компоненты [MFC], локализация"
  - "DLL-библиотеки [C++], локализация MFC"
  - "локализация [C++], компоненты MFC"
  - "локализация [C++], ресурсы MFC"
  - "локализация [C++], ресурсы"
  - "библиотеки DLL MFC [C++], локализация"
  - "ресурсы [MFC], локализация"
  - "TN057"
ms.assetid: 5376d329-bd45-41bd-97f5-3d895a9a0af5
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# TN057. Локализация компонентов MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  Следующее техническое примечание не было обновлено, поскольку сначала оно было включено в электронную документацию.  В результате некоторые процедуры и разделы могут быть устаревшими или неверными.  Для получения последних сведений рекомендуется выполнить поиск интересующей темы в алфавитном указателе документации в Интернете.  
  
 Эта заметка описываются некоторые разработки и процедуры можно использовать для локализации компонент, если манифест приложения или элемента управления OLE или DLL, которое использует MFC.  
  
## Обзор  
 Действительно 2 проблемы, которые следует разрешить локализация компонент, который использует MFC.  Сначала нужно локализовать собственные ресурсы — строки, диалоговые окна и другие ресурсы, указанные в компонент.  Большинство компонентов, построенные с помощью MFC также включают и используют несколько ресурсов, определенные MFC.  Необходимо предоставить локализованные ресурсы MFC также.  Удачно, несколько языков уже предоставляемых MFC самим.  
  
 Кроме того, компонент должен быть создан для выполнения своей среде целевого объекта \(европейской или DBCS\- доступной среде\).  В большинстве случаев это зависит от приложения обработки символов с sr бит, правильно и обработки строк с двухбайтовыми знаков.  MFC включен по умолчанию для всех этих сред, так, что можно иметь одно всемирное бинарный, используется на всех платформах, просто различные ресурсы в заткнутые во время установки.  
  
## Локализация ресурсов компонента  
 Локализация приложения или DLL должен включать просто заменить ресурсы с ресурсами, которые соответствуют целевому языку и региональным параметрам.  Для собственных ресурсов это относительно просто: правка ресурсы в редакторе ресурсов и построения приложения.  Если код написан правильно, будут отсутствуют строки или текст, который вы хотите локализации жестко заданное в исходный код C\+\+ — все локализация может быть создана только изменять ресурсы.  Фактически, можно реализовать пользовательский компонент так, что является предоставление локализованной версии даже не включает построение исходного кода.  Это более сложное, но рекомендуется затраты на его и механизм выбранный для самого MFC.  Также можно локализовать приложение путем загрузки файла EXE или DLL в редактор ресурсов и изменения ресурсов непосредственно.  При возможности, необходимые переприменения этих изменений при каждом построении новую версию приложения.  
  
 Одним из способов избежать, найти все ресурсы в отдельной библиотеки DLL, иногда называемый спутниковым библиотеки DLL.  Затем эта библиотека DLL загружается динамически во время выполнения и ресурсы загружаются из этого DLL вместо из главного модуля с во всем коде.  MFC непосредственно поддерживает этот подход.  Рассмотрим приложение с именем MYAPP.EXE; оно может иметь все его ресурсов, расположенных в вызываемом библиотеки DLL MYRES.DLL.  В `InitInstance` приложения, он выполняет следующие действия для загрузки библиотеки DLL, и заставить MFC загрузка ресурсов из этого расположения.  
  
```  
CMyApp::InitInstance()  
{  
   // one of the first things in the init code  
   HINSTANCE hInst = LoadLibrary("myres.dll");  
   if (hInst != NULL)  
      AfxSetResourceHandle(hInst);  
  
   // other initialization code would follow  
   .  
   .  
   .  
}  
```  
  
 С этого момента, загружает из этого ресурсы MFC DLL вместо из myapp.exe.  Все ресурсы, однако должны присутствовать в этом DLL; MFC не ищет экземпляр приложения в поисках данного ресурса.  Этот метод применяется с тем же успехом в обычной библиотеке DLL, так и элементам управления OLE.  Программа установки копироватьTfа, соответствующую версию MYRES.DLL в зависимости от которого языковой стандарт пользователя ресурсов, который был бы.  
  
 Относительно легко создать библиотеку DLL только ресурса.  Создается проект библиотеки DLL, добавьте в него свой rc\-файл и добавление необходимых ресурсов.  Если имеется существующий проект, не использует этот метод можно копировать ресурсы из этого проекта.  После добавления в проект файл ресурсов, будут практически готовы к построения проекта.  Изменяется только необходимо сделать имеет параметры компоновщика включить  **\/NOENTRY**.  Это означает, что библиотека DLL компоновщик не имеет точки входа, поскольку он не имеет код, он не имеет точки входа.  
  
> [!NOTE]
>  Редактор ресурсов в Visual C\+\+ 4.0 и более поздних версий поддерживают несколько языков в rc\-файл.  Это может сделать его очень легко управлять, локализация в отдельном проекте.  Ресурсы для каждого языка управляются директивами препроцессора полученными редактора ресурсов.  
  
## Использование, предоставляемые локализованные ресурсы MFC  
 Любое приложение MFC, построение которой выполняется повторяющихся использования 2 действия на основе MFC: код и ресурсы.  То есть MFC имеет различные сообщения об ошибках, встроенные диалоговые окна и другие ресурсы, используемые классами MFC.  Полностью для локализации приложения необходимо локализовать не только ресурсы приложения, но и ресурсы, полученные непосредственно из MFC.  MFC предоставляет несколько файлов ресурсов для другого языка автоматически, поэтому если язык, выбранная будет один из языков MFC уже поддерживает, нужно просто необходимо убедиться, что использует эти локализованные ресурсы.  
  
 Начиная с этого материала, MFC поддерживает набор, немецкого языка, испанского языка, французский, итальянского языка, японского и корейской.  Файлы, содержащие эти локализованные версии в каталогах MFC\\INCLUDE\\L.\* \(«L» требуется для локализованный\).  Немецкие файлы в MFC\\INCLUDE\\L.DEU, например.  Чтобы обеспечить приложению использовать эти файлы RC вместо расположение файлов в MFC\\INCLUDE добавьте `/IC:\PROGRAM FILES\MICROSOFT VISUAL STUDIO .NET 2003\VC7\MFC\INCLUDE\L.DEU` в командной строке RC \(это просто пример; необходимо заменить его языковой стандарт варианта, так и каталога, в котором установлен Visual C\+\+\).  
  
 Вышеописанные инструкции будут работать, если ссылается приложения статически с MFC.  Большинство приложений динамически ссылку \(поскольку значение по умолчанию AppWizard\).  В этом сценарии, не только код динамически связывается — таким образом ресурсы.  В результате можно локализовать ресурсы в приложении, но ресурсы реализации MFC будут загружаться из MFC7x.DLL \(или более поздней версии\) или из MFC7xLOC.DLL, если он существует.  Этот подход можно из 2 различных углами.  
  
 Более сложный подход выдать одно из локализованного MFC7xLOC.DLLs \(например, MFC7xDEU для немецкого языка, MFC7xESP.DLL для испанского языка и т д\) или более позднюю версию, и установит соответствующее MFC7xLOC.DLL в системный каталог, когда пользователь установит приложение.  Это может быть очень сложно как для разработчиков, так и для пользователя и как таковой не рекомендуется.  Дополнительные сведения см. в разделе [Техническое примечание 56](../Topic/TN056:%20Installation%20of%20Localized%20MFC%20Components.md) в этом методе и его предостережениях.  
  
 Самым простым и безопасный способ включения локализованных ресурсов в приложении MFC DLL или убывания \(или его вспомогательной библиотеке DLL при использовании единица\).  Это позволяет избежать проблем установки MFC7xLOC.DLL правильно.  Чтобы сделать это, действуют те же инструкции для статического случай заданную выше \(установка командную строку RC правильно для указания на локализованные ресурсы\), за исключением того, что необходимо удалить `/D_AFXDLL` определяется, добавленные AppWizard.  При `/D_AFXDLL` определяется, AFXRES.H \(и другие файлы MFC RC\) фактически не указываются \(ресурсы, поскольку они будут взяты из библиотеки DLL MFC вместо\).  
  
## См. также  
 [Технические примечания по номеру](../mfc/technical-notes-by-number.md)   
 [Технические примечания по категории](../mfc/technical-notes-by-category.md)