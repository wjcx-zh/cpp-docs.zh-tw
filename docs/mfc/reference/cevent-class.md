---
title: "CEvent 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CEvent
- AFXMT/CEvent
- AFXMT/CEvent::CEvent
- AFXMT/CEvent::PulseEvent
- AFXMT/CEvent::ResetEvent
- AFXMT/CEvent::SetEvent
- AFXMT/CEvent::Unlock
dev_langs:
- C++
helpviewer_keywords:
- CEvent [MFC], CEvent
- CEvent [MFC], PulseEvent
- CEvent [MFC], ResetEvent
- CEvent [MFC], SetEvent
- CEvent [MFC], Unlock
ms.assetid: df676042-ce27-4702-800a-e73ff4f44395
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0646e703f172777817aa569fa28d3430624ccae8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cevent-class"></a>CEvent 類別
表示事件，這是可讓一個執行緒通知發生事件的另一個執行緒的同步處理物件。  
  
## <a name="syntax"></a>語法  
  
```  
class CEvent : public CSyncObject  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CEvent::CEvent](#cevent)|建構 `CEvent` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CEvent::PulseEvent](#pulseevent)|設定要使用的事件 （通知），釋出等候執行緒，並將事件設定為無法使用 （未收到信號）。|  
|[CEvent::ResetEvent](#resetevent)|將事件設定為無法使用 （未收到信號）。|  
|[CEvent::SetEvent](#setevent)|設定到可用的事件 （信號），並釋放任何等候中執行緒。|  
|[CEvent::Unlock](#unlock)|釋放事件。|  
  
## <a name="remarks"></a>備註  
 當執行緒必須知道何時要執行其工作時，事件相當實用。 例如，當新的資料可用時，必須告知執行緒將資料複製到資料封存。 使用`CEvent`物件新的資料可用時通知複製執行緒的執行緒可以儘快執行其工作。  
  
 `CEvent`物件有兩種類型： 手動和自動。  
  
 自動`CEvent`物件會自動返回未收到訊號 （無法使用） 的狀態後發行至少一個執行緒。 根據預設，`CEvent`物件是自動的除非您傳遞`TRUE`如`bManualReset`在建構期間的參數。  
  
 手動`CEvent`物件停留在所設定的狀態[SetEvent](#setevent)或[ResetEvent](#resetevent)另一個函式呼叫之前。 若要建立手動`CEvent`物件，傳遞`TRUE`如`bManualReset`在建構期間的參數。  
  
 若要使用`CEvent`物件，然後建構`CEvent`物件會在需要時。 指定您想要等候，也指定您的應用程式一開始應該擁有該事件的名稱。 然後，您可以存取的建構函式傳回時的事件。 呼叫[SetEvent](#setevent)訊號 （請使用） 事件物件，然後再呼叫[Unlock](#unlock)完成時存取控制的資源。  
  
 使用替代方法`CEvent`物件是新增類型的變數`CEvent`以您想要控制的類別資料成員。 在建構期間的受控制的物件，呼叫的建構函式`CEvent`資料成員，指定是否一開始收到信號的事件，以及也 specifythe 類型的事件物件，事件 （如果它會使用於跨處理序的名稱界限），任何您想要的安全性屬性。  
  
 若要存取所控制的資源`CEvent`物件以這種方式，請先建立兩種類型的變數[CSingleLock](../../mfc/reference/csinglelock-class.md)或型別[CMultiLock](../../mfc/reference/cmultilock-class.md)中之資源的存取方法。 然後呼叫`Lock`之鎖定物件的方法 (例如， [CMultiLock::Lock](../../mfc/reference/cmultilock-class.md#lock))。 此時，您的執行緒會存取資源、 等候的資源釋出並存取應用程式，或等候的資源釋出、 逾時，並無法取得資源的存取權。 在任何情況下，您的資源已存取具備執行緒安全的方式。 若要釋放資源，呼叫`SetEvent`表示事件物件，然後使用`Unlock`之鎖定物件的方法 (例如， [CMultiLock::Unlock](../../mfc/reference/cmultilock-class.md#unlock))，或讓鎖定物件超出範圍。  
  
 如需有關如何使用`CEvent`物件，請參閱[多執行緒： 如何使用同步類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities#45](../../mfc/codesnippet/cpp/cevent-class_1.cpp)]  
  
 [!code-cpp[NVC_MFC_Utilities#46](../../mfc/codesnippet/cpp/cevent-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CEvent`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxmt.h  
  
##  <a name="cevent"></a>CEvent::CEvent  
 建構的具名或未命名`CEvent`物件。  
  
```  
CEvent(
    BOOL bInitiallyOwn = FALSE,  
    BOOL bManualReset = FALSE,  
    LPCTSTR lpszName = NULL,  
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```  
  
### <a name="parameters"></a>參數  
 `bInitiallyOwn`  
 如果**TRUE**，如執行緒**CMultilock**或`CSingleLock`啟用物件。 否則，就必須等候所有想要存取資源的執行緒。  
  
 *bManualReset*  
 如果**TRUE**，指定，事件物件的手動事件，否則事件物件是自動的事件。  
  
 `lpszName`  
 `CEvent` 物件的名稱。 如果物件會使用跨處理序界限，必須提供。 如果名稱符合現有的事件，建構函式會建置新`CEvent`物件會參考該名稱的事件。 如果名稱相符的現有同步處理物件的不是事件，建構將會失敗。 如果**NULL**，名稱會是 null。  
  
 `lpsaAttribute`  
 事件物件的安全性屬性。 此結構的完整說明，請參閱[ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) Windows SDK 中。  
  
### <a name="remarks"></a>備註  
 若要存取，或釋放`CEvent`物件，請建立[CMultiLock](../../mfc/reference/cmultilock-class.md)或[CSingleLock](../../mfc/reference/csinglelock-class.md)物件並呼叫其[鎖定](../../mfc/reference/csinglelock-class.md#lock)和[解除鎖定](../../mfc/reference/csinglelock-class.md#unlock)成員函式。  
  
 若要變更的狀態`CEvent`物件為收到信號 （執行緒不必等候），呼叫[SetEvent](#setevent)或[PulseEvent](#pulseevent)。 若要設定狀態的`CEvent`物件為未收到信號 （執行緒必須等待，） 呼叫[ResetEvent](#resetevent)。  
  
> [!IMPORTANT]
>  在建立之後`CEvent`物件，請使用[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)以確保 mutex 不是已經存在。 如果未意外存在 mutex，可能表示 rogue 程序會佔用，而且可能會想要進行惡意使用 mutex。 在此情況下，建議的注重安全性的程序是關閉此控制代碼，並繼續如同在建立物件時發生失敗。  
  
##  <a name="pulseevent"></a>CEvent::PulseEvent  
 將狀態設定為收到信號的事件 （可用）、 釋放任何等候中執行緒，並且將它重設為未收到信號 （無法使用） 會自動。  
  
```  
BOOL PulseEvent();
```  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 如果手動事件，會釋放所有等候中執行緒，事件會設定為未收到信號，和`PulseEvent`傳回。 如果事件是自動的單一執行緒釋放，事件會設定為未收到信號，和`PulseEvent`傳回。  
  
 如果沒有執行緒等候，或沒有任何執行緒可以立即釋放`PulseEvent`設定事件的狀態未收到信號，並傳回。  
  
 `PulseEvent`會使用基礎 Win32`PulseEvent`函式，可以暫時移除從等候狀態的核心模式的非同步程序呼叫。 因此，`PulseEvent`不可靠，不應由新的應用程式。 如需詳細資訊，請參閱[PulseEvent 函式](http://msdn.microsoft.com/library/windows/desktop/ms684914)。  
  
##  <a name="resetevent"></a>CEvent::ResetEvent  
 設定事件的狀態未收到信號，直到明確設定為收到信號的[SetEvent](#setevent)成員函式。  
  
```  
BOOL ResetEvent();
```  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 這會導致所有想要存取此事件，以等候的執行緒。  
  
 此成員函式不是由自動事件。  
  
##  <a name="setevent"></a>CEvent::SetEvent  
 設定為收到信號，事件的狀態，釋放任何等候中執行緒。  
  
```  
BOOL SetEvent();
```  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 如果手動事件，事件仍可保持直到收到信號[ResetEvent](#resetevent)呼叫。 多個執行緒可以在此情況下發行。 如果事件是自動的事件會保持在收到信號，直到釋放單一執行緒。 為未收到信號，系統會將事件的狀態。 如果沒有執行緒正在等待，狀態會保留信號，一個執行緒釋放之前。  
  
##  <a name="unlock"></a>CEvent::Unlock  
 釋放事件。  
  
```  
BOOL Unlock();
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果執行緒所擁有，事件物件和事件是自動的事件。否則便是 0。  
  
### <a name="remarks"></a>備註  
 目前擁有自動釋放之後完成，如果其鎖定的物件重複事件的執行緒會呼叫此成員函式。 如果鎖定物件不是可重複使用，此函式會被呼叫之鎖定物件的解構函式。  
  
## <a name="see-also"></a>請參閱  
 [CSyncObject 類別](../../mfc/reference/csyncobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)

