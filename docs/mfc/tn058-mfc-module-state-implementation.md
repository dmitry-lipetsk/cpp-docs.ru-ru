---
title: "TN058: Реализация состояния модуля MFC | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.implementation
dev_langs: C++
helpviewer_keywords:
- thread state [MFC]
- module states [MFC], managing state data
- TN058
- MFC, managing state data
- module states [MFC], switching
- DLLs [MFC], module states
- process state [MFC]
ms.assetid: 72f5b36f-b3da-4009-a144-24258dcd2b2f
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ed7bc195c771026ff3e58d53f9e3936791810e76
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="tn058-mfc-module-state-implementation"></a>TN058. Реализация состояния модуля MFC
> [!NOTE]
>  Следующее техническое примечание не было обновлено, поскольку сначала оно было включено в электронную документацию. В результате некоторые процедуры и разделы могут быть устаревшими или неверными. Для получения последних сведений рекомендуется выполнить поиск интересующей темы в алфавитном указателе документации в Интернете.  
  
 Это техническое Примечание описывается реализация конструкции «Состояния модуля MFC». Понимание реализация состояния модуля является критическим, с помощью MFC общих библиотек DLL из библиотеки DLL (или внутрипроцессный OLE-сервер).  
  
 Перед прочтением этого примечание, ссылается на «Управление данными о состоянии модулей MFC» в [создание новых документов, окон и представлений](../mfc/creating-new-documents-windows-and-views.md). Эта статья содержит важные сведения по использованию и общие сведения по этой теме.  
  
## <a name="overview"></a>Обзор  
 Существует три вида сведения о состоянии MFC: состояние модуля, состояние процесса и состояние потока. Иногда эти типы состояния могут быть объединены. Например схемы дескриптор MFC являются локального модуля и локальных для потока. Это позволяет двух разных модулях на разных картах в каждой из своих потоков.  
  
 Состояние процесса и состояние потока похожи. Эти элементы данных являются вещей, которые традиционно глобальные переменные, но имеют должны различаться для каждого процесса или потока для поддерживает правильную Win32s или правильную многопоточности. Какой категории элемента данных помещается в зависит от этого элемента и его семантику относительно границ процессов и потоков.  
  
 Состояние модуля является уникальным в том, что он может содержать действительно глобальное состояние или состояние, которое является локальный процесс или поток локальной. Кроме того он может быстро переключаться.  
  
## <a name="module-state-switching"></a>Переключение состояния модуля  
 Каждый поток содержит указатель на состояние «текущая» или «активный» модуль (не удивительно, что указатель является частью локального состояния потока MFC). Этот указатель изменяется, когда границы модуля, например вызов элемента управления OLE или библиотеку DLL или элемента управления OLE обратный вызов приложения приложение передает поток выполнения.  
  
 Текущее состояние модуля стала путем вызова **AfxSetModuleState**. В большинстве случаев никогда не будет работать непосредственно с помощью API. MFC, во многих случаях будет вызывать его для вас (на WinMain точки входа OLE, **AfxWndProc**и т. д.). Это делается в любом компоненте письма, статическая компоновка в специальном **WndProc**и специальный `WinMain` (или `DllMain`), которому известны состояние модуля, которое должно быть текущей. Для проверки этого кода DLLMODUL. CPP или APPMODUL. CPP в каталоге MFC\SRC.  
  
 Очень редко, необходимо задать для состояния модуля и не определен обратно. В большинстве случаев требуется собственный модуль «push» состояний в качестве текущего и затем, после завершения «pop» исходного контекста обратно. Это можно сделать, макрос [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) и специальным классом **AFX_MAINTAIN_STATE**.  
  
 `CCmdTarget`имеет специальные функции для поддержки переключения состояния модуля. В частности `CCmdTarget` является корневой класс используется для автоматизации OLE и OLE COM точки входа. Как и любые другие точки входа открыты для системы, эти точки входа необходимо задать верное состояние модуля. Как does данного `CCmdTarget` знать, что модуль «правильный» состояние должно быть ответ — что он «запоминаются» Каково состояние «текущая» модуля при построении, таким образом, что его можно задать текущее состояние модуля, «сохраненных» называется значение, когда он является более поздней версии. В результате модуль состояния данного `CCmdTarget` объект связан с находится в состоянии модуля, которая была текущей во объект был создан. Рассмотрим простой примера загрузки сервера INPROC, для создания объекта и вызвав его методы.  
  
1.  Библиотека DLL загружается с OLE с помощью **LoadLibrary**.  
  
2. **RawDllMain** сначала вызывается. Он устанавливает состояние модуля в состояние известного статического модуля для DLL-файла. По этой причине **RawDllMain** статически компонуемые библиотеки DLL.  
  
3.  Вызов конструктора для класса фабрики, связанных с нашей объектом. `COleObjectFactory`является производным от `CCmdTarget` и в результате запоминает в состояние, которое модуль был создан. Это важно, когда фабрика класса получит запрос на создание объектов, он знает, теперь какое состояние модуля необходимо сделать текущим.  
  
4. `DllGetClassObject`вызывается для получения фабрики класса. MFC выполняет поиск в списке фабрики класса, связанный с данным модулем и возвращает его.  
  
5. **COleObjectFactory::XClassFactory2::CreateInstance** вызывается. До создания объекта и возвращением, эта функция устанавливает состояние модуля состояния модуля, которая была текущей на шаге 3 (которая была текущей при `COleObjectFactory` был создан). Это выполняется внутри [METHOD_PROLOGUE](com-interface-entry-points.md).  
  
6.  При создании объекта слишком бывает `CCmdTarget` класс, производный от и таким же образом `COleObjectFactory` запомнить, какое состояние модуля был активен, также возрастает этот новый объект. Теперь объект знает, какое состояние модуля переключиться на каждый раз, когда он вызывается.  
  
7.  Клиент вызывает функцию для COM OLE-объект, полученный от его `CoCreateInstance` вызова. При вызове объекта он использует `METHOD_PROLOGUE` для переключения состояния модуля так же, как `COleObjectFactory` does.  
  
 Как видите, состояние модуля распространяется от объекта к объекту при их создании. Это важно, чтобы состояние модуля, заданное соответствующим образом. Если не указано, DLL или COM-объект может плохо взаимодействовать с приложение MFC, вызывает его или не удается найти собственными ресурсами может завершиться ошибкой по-другому плохо.  
  
 Обратите внимание, что некоторые виды библиотек DLL, специально «Модуля MFC» библиотеки DLL не переключения состояния модуля в их **RawDllMain** (на самом деле, они обычно даже не **RawDllMain**). Это так, как они предназначены для функционируют «как» фактически они находились в приложение, которое использует их. Они являются существенно частью приложения, на котором работает, и это выполняемое Изменение глобального состояния данного приложения.  
  
 Элементы управления OLE и других библиотек DLL сильно отличаются. Они не требуется изменять состояние вызывающего приложения; приложения, которое вызывает их могут даже не приложения MFC и поэтому может существовать без состояния для изменения. Это происходит по причине, что переключение состояния модуля и, следовательно.  
  
 Экспортируемые функции из DLL, например, диалоговое окно «» в библиотеке DLL необходимо добавить следующий код в начало функции:  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState())  
```  
  
 Это меняет текущего состояния модуля с состоянием, возвращенные [AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate) до конца текущей области.  
  
 Проблемы с ресурсами в библиотеках DLL будет возникать, если `AFX_MODULE_STATE` макрос не используется. По умолчанию MFC использует дескриптор ресурса основного приложения для загрузки шаблона ресурсов. Этот шаблон хранится в библиотеке DLL. Основной причиной является сведения о состоянии модуля MFC не была переключена с `AFX_MODULE_STATE` макрос. Дескриптор ресурса будет восстановлена из состояния модуля MFC. Переключение состояния модуля не вызывает ресурсов неправильный дескриптор для использования.  
  
 `AFX_MODULE_STATE`не требуется помещать в каждой функции в DLL. Например `InitInstance` может быть вызван кодом MFC в приложении без `AFX_MODULE_STATE` поскольку MFC автоматически переключается в состояние модуля перед `InitInstance` и затем коммутаторы ее снова после `InitInstance` возвращает. То же самое верно для всех обработчиков сообщений карты. Обычные библиотеки DLL MFC фактически иметь специальное окно главную процедуру автоматического переключения состояния модуля перед отправкой сообщения.  
  
## <a name="process-local-data"></a>Локальные данные процесса  
 Локальные данные процесса будут такие большую важность оно не выполнялось для сложность модели Win32s DLL. В Win32s все DLL-библиотеки используют их как глобальные данные, даже в том случае, если загрузить несколькими приложениями. Этот процесс сильно отличается от «real» DLL-Библиотеки Win32 модели данных, где каждой библиотеки DLL, получает отдельную копию пространства данных каждого процесса, который присоединяется к библиотеке DLL. Добавление к сложности, данных, размещенных в куче в библиотеку DLL, одна из систем Win32 — на самом деле процесс конкретных (по крайней мере насколько становится владельцем). Рассмотрим следующие данные и код.  
  
```  
static CString strGlobal; // at file scope  
 
__declspec(dllexport)   
void SetGlobalString(LPCTSTR lpsz)  
{  
    strGlobal = lpsz;  
}  
 
__declspec(dllexport)  
void GetGlobalString(LPCTSTR lpsz,
    size_t cb)  
{  
    StringCbCopy(lpsz,
    cb,
    strGlobal);

}  
```  
  
 Рассмотрим, что произойдет, если приведенный выше код в находится в библиотеке DLL и загрузку DLL двумя процессами A и B (он может на самом деле быть двух экземпляров одного приложения). Вызовы `SetGlobalString("Hello from A")`. В результате выделить память для `CString` данных в контексте процесса, а. Имейте в виду, что `CString` сам является глобальным и доступен для обоих A и B. B вызывает `GetGlobalString(sz, sizeof(sz))`. B сможет просматривать данные, задать значение. Это так, как одна из систем Win32 не обеспечивает защиту между процессами в стиле Win32. Это первая проблема; Во многих случаях это не желательно одного приложения, которые влияют на глобальные данные, которые считаются владеют в другом приложении.  
  
 Существуют также дополнительные проблемы. Предположим, что теперь завершает работу. При завершении объект памяти, используемой "`strGlobal`" строка станет доступным в системе, то есть всю память, выделяемая процесс A освобождается автоматически операционной системой. Он не будет освобожден, так как `CString` вызывается деструктор; он не был вызван. Она не будет освобождена просто так, как приложение, которое его покинул сцены. Теперь при вызове B `GetGlobalString(sz, sizeof(sz))`, он не может получить допустимые данные. Другое приложение может использовать эту память-нибудь еще.  
  
 Четко возникла проблема. MFC 3.x используется метод, называемый локальное хранилище потока (TLS). MFC 3.x будет выделить индекс TLS, что в Win32s действует как в индексе, процесс локальной памяти, несмотря на то, что он не вызывается и затем предоставить ссылки, все данные на основе этого индекса TLS. Это похоже на TLS индекс, который был использован для хранения локальных данных потока в Win32 (см. ниже дополнительные сведения по этой теме). Это вызвано каждой библиотеки DLL MFC использовать по крайней мере два TLS индексы каждого процесса. Если учетная запись для многих OLE управления библиотеки DLL, загружаемые (OCX), быстро исчерпании индексов TLS (доступно только в 64). Кроме того для размещения этих данных в одном месте, в одной структуре было MFC. Он не был значительно расширяемый и не оптимально по отношению к его использование индексов TLS.  
  
 MFC 4.x решает эту проблему с набором шаблонов классов, можно «создать оболочку» вокруг данных, который должен быть локальный процесс. Например упомянутых выше проблему можно исправить, записи:  
  
```  
struct CMyGlobalData : public CNoTrackObject  
{  
    CString strGlobal;  
};  
CProcessLocal<CMyGlobalData> globalData;  
 
__declspec(dllexport)   
void SetGlobalString(LPCTSTR lpsz)  
{  
    globalData->strGlobal = lpsz;  
}  
 
__declspec(dllexport)  
void GetGlobalString(LPCTSTR lpsz, size_t cb)  
{  
    StringCbCopy(lpsz, cb, globalData->strGlobal);

}  
```  
  
 Это реализация MFC в два этапа. Во-первых, есть слоя поверх Win32 **Tls\***  API-интерфейсы (**TlsAlloc**, **TlsSetValue**, **TlsGetValue**, т. д.) что Используйте только два TLS индексы каждого процесса, независимо от того, сколько библиотек DLL. Во-вторых, `CProcessLocal` шаблон предоставляется доступ к этим данным. Переопределяет оператор ->, который является то, что позволяет интуитивно понятный синтаксис приведены выше. Все объекты, которые являются оболочкой для `CProcessLocal` должен быть производным от `CNoTrackObject`. `CNoTrackObject`предоставляет распределителя более низкого уровня (**LocalAlloc**/**LocalFree**) и виртуальный деструктор таким образом, что MFC автоматически может уничтожить локальных объектов процесса, когда процесс завершен. Такие объекты могут иметь пользовательский деструктор, если требуется дополнительные действия по очистке. Приведенный выше пример не требуется, так как компилятор создает деструктор по умолчанию для уничтожения встроенный `CString` объекта.  
  
 Существуют другие интересные преимущества этого подхода. Не только находятся все `CProcessLocal` объекты удаляются автоматически, они не создается, пока они нужны. `CProcessLocal::operator->`Создает экземпляр связанного объекта он вызывается при первом запуске и не может быть выполнено. В приведенном выше примере, это означает, что "`strGlobal`' строка не создается до момента первого **SetGlobalString** или **GetGlobalString** вызывается. В некоторых случаях это может снизить время запуска библиотеки DLL.  
  
## <a name="thread-local-data"></a>Локальных данных потока  
 Как и для обработки локальных данных, локальных данных потока используется при данные должны быть локальным для данного потока. То есть требуется отдельный экземпляр данных для каждого потока, который обращается к этим данным. Это многократно используется вместо механизмов широко синхронизации. Если данные не нужно совместно используется несколькими потоками, механизмов, может быть дорогостоящим и ненужные. Предположим, что мы должны были `CString` объектов (наподобие приведенного выше примера). Сделать ее потоков локального путем упаковывания их с `CThreadLocal` шаблона:  
  
```  
struct CMyThreadData : public CNoTrackObject  
{  
    CString strThread;  
};  
CThreadLocal<CMyThreadData> threadData;  
 
void MakeRandomString()  
{ *// a kind of card shuffle (not a great one)  
    CString& str = threadData->strThread;  
    str.Empty();
while (str.GetLength() != 52)  
 {  
    unsigned int randomNumber;  
    errno_t randErr;  
    randErr = rand_s(&randomNumber);

    if (randErr == 0)  
 {  
    TCHAR ch = randomNumber % 52 + 1;  
    if (str.Find(ch) <0)  
    str += ch; // not found, add it  
 }  
 }  
}  
```  
  
 Если `MakeRandomString` был вызван из двух различных потоков, каждый будет» в случайном порядке» строки по-разному не конфликтуют с другими. Это вызвано отсутствием фактически `strThread` экземпляра для каждого потока, а не только один глобальный экземпляр.  
  
 Обратите внимание на то, как ссылка используется для записи `CString` адрес один раз вместо после каждой итерации цикла. Цикл код можно было бы записать с `threadData->strThread` everywhere "`str`" используется, но код будет работать намного медленнее при выполнении. Рекомендуется кэшировать ссылку на данные, такие ссылки, происходящие в циклах.  
  
 `CThreadLocal` Шаблона класса использует те же механизмы, `CProcessLocal` не, а также те же способы реализации.  
  
## <a name="see-also"></a>См. также  
 [Технические примечания по номеру](../mfc/technical-notes-by-number.md)   
 [Технические примечания по категории](../mfc/technical-notes-by-category.md)

