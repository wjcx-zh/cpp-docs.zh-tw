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
- synchronization objects, event
- synchronization classes, CEvent class
- CEvent class
ms.assetid: df676042-ce27-4702-800a-e73ff4f44395
caps.latest.revision: 27
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 9edadeec87cf04ae6166c173c65463d1509eb1d8
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cevent-class"></a>CEvent 類別
表示事件，這是可讓一個執行緒通知發生事件的另一個執行緒的同步處理物件。  
  
## <a name="syntax"></a>語法  
  
```  
class CEvent : public CSyncObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CEvent::CEvent](#cevent)|建構 `CEvent` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CEvent::PulseEvent](#pulseevent)|將可用的事件 （通知），釋放等候中執行緒，並且設定為無法使用的事件 （未收到訊號）。|  
|[CEvent::ResetEvent](#resetevent)|設定為無法使用的事件 （未收到訊號）。|  
|[CEvent::SetEvent](#setevent)|設定為可用的事件 （已收到訊號），並釋放所有等候的執行緒。|  
|[CEvent::Unlock](#unlock)|釋放事件物件。|  
  
## <a name="remarks"></a>備註  
 當執行緒必須知道何時要執行其工作時，事件會相當實用。 比方說，新的資料可用時，將資料複製到資料保存在執行緒就必須收到通知。 使用`CEvent`物件以新資料可用時通知複製執行緒的執行緒可以儘快執行其工作。  
  
 `CEvent`物件有兩種類型︰ 手動和自動。  
  
 自動`CEvent`物件會自動傳回給單一執行緒的 （無法使用） 回應之後至少一個執行緒釋出。 根據預設，`CEvent`物件是自動的除非您傳遞`TRUE`的`bManualReset`在建構期間的參數。  
  
 手動`CEvent`物件會保留在所設定的狀態[SetEvent](#setevent)或[ResetEvent](#resetevent)另一個函式呼叫之前。 若要建立手動`CEvent`物件，傳遞`TRUE`的`bManualReset`在建構期間的參數。  
  
 若要使用`CEvent`物件，建構`CEvent`物件會在需要時。 指定您想要等候，以及指定您的應用程式一開始應該擁有該事件的名稱。 您接著可存取建構函式傳回時，此事件。 呼叫[SetEvent](#setevent)訊號 （方式提供） 事件物件，然後再呼叫[Unlock](#unlock)完成存取控制的資源。  
  
 使用替代方法`CEvent`物件是新增型別的變數`CEvent`以您想要控制的類別資料成員。 在受控制的物件建構期間呼叫的建構函式`CEvent`資料成員並指定是否一開始的信號事件，以及 specifythe 類型的事件物件，事件 （如果它將會使用跨處理序界限），名稱屬性的任何安全性需要。  
  
 若要存取所控制的資源`CEvent`物件以這種方式，請先建立這兩種類型的變數[CSingleLock](../../mfc/reference/csinglelock-class.md)或型別[CMultiLock](../../mfc/reference/cmultilock-class.md)中部署資源的存取方法。 然後呼叫`Lock`之鎖定物件的方法 (例如， [CMultiLock::Lock](../../mfc/reference/cmultilock-class.md#lock))。 此時，您的執行緒會存取資源等候的資源釋出，並存取應用程式，或等候的資源釋出、 逾時，並無法取得資源的存取權。 在任何情況下，您的資源已存取具備執行緒安全的方式。 若要釋放資源，呼叫`SetEvent`發出信號的事件物件，然後使用`Unlock`之鎖定物件的方法 (例如， [CMultiLock::Unlock](../../mfc/reference/cmultilock-class.md#unlock))，或讓鎖定物件超出範圍。  
  
 如需有關如何使用`CEvent`物件，請參閱[多執行緒︰ 如何使用同步類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities #&45;](../../mfc/codesnippet/cpp/cevent-class_1.cpp)]  
  
 [!code-cpp[NVC_MFC_Utilities #&46;](../../mfc/codesnippet/cpp/cevent-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CEvent`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxmt.h  
  
##  <a name="cevent"></a>CEvent::CEvent  
 建構具名或未命名的`CEvent`物件。  
  
```  
CEvent(
    BOOL bInitiallyOwn = FALSE,  
    BOOL bManualReset = FALSE,  
    LPCTSTR lpszName = NULL,  
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```  
  
### <a name="parameters"></a>參數  
 `bInitiallyOwn`  
 如果**TRUE**，如執行緒**CMultilock**或`CSingleLock`啟用物件。 否則，必須等到所有想要存取資源的執行緒。  
  
 *bManualReset*  
 如果**TRUE**，指定事件的物件，手動事件，否則事件物件是自動的事件。  
  
 `lpszName`  
 `CEvent` 物件的名稱。 如果此物件會使用跨處理序界限，必須提供。 如果名稱符合現有的事件、 建構函式會建置新`CEvent`物件會參考該名稱的事件。 如果名稱符合現有的同步處理物件不是事件，在建構將會失敗。 如果**NULL**，名稱會是 null。  
  
 `lpsaAttribute`  
 事件物件的安全性屬性。 此結構的完整說明，請參閱[ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 存取或釋放`CEvent`物件，請建立[CMultiLock](../../mfc/reference/cmultilock-class.md)或[CSingleLock](../../mfc/reference/csinglelock-class.md)物件，然後呼叫其[鎖定](../../mfc/reference/csinglelock-class.md#lock)和[Unlock](../../mfc/reference/csinglelock-class.md#unlock)成員函式。  
  
 若要變更的狀態`CEvent`物件已收到訊號 （執行緒沒有等候），呼叫[SetEvent](#setevent)或[PulseEvent](#pulseevent)。 若要設定狀態的`CEvent`物件為未收到信號 （執行緒必須等待，） 呼叫[ResetEvent](#resetevent)。  
  
> [!IMPORTANT]
>  在建立之後`CEvent`物件，請使用[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)以確保 mutex 不是已經存在。 如果存在非預期地 mutex，可能表示處理序佔用，而且可能會想要進行惡意使用 mutex。 在此情況下，建議的注重安全性的程序是關閉此控制代碼，並繼續如同在建立物件時發生錯誤。  
  
##  <a name="pulseevent"></a>CEvent::PulseEvent  
 設定之事件的狀態 （可用）、 釋放所有等候中執行緒，並將它重設為未收到信號 （無法使用） 自動。  
  
```  
BOOL PulseEvent();
```  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 如果事件為手動，會釋放所有等候中執行緒，就會設定為未收到信號，事件和`PulseEvent`傳回。 如果事件是自動的單一執行緒釋放，將事件設定為未收到信號，和`PulseEvent`傳回。  
  
 如果沒有執行緒等候，或沒有執行緒可立即釋放`PulseEvent`將事件的狀態設定為未收到信號，並傳回。  
  
 `PulseEvent`使用基本 Win32`PulseEvent`函式，可以暫時移除等候狀態從核心模式的非同步程序呼叫。 因此，`PulseEvent`不可靠，而且不能供新的應用程式。 如需詳細資訊，請參閱[PulseEvent 函式](http://msdn.microsoft.com/library/windows/desktop/ms684914)。  
  
##  <a name="resetevent"></a>CEvent::ResetEvent  
 設定事件的狀態未收到信號，直到明確設定為已收到訊號的[SetEvent](#setevent)成員函式。  
  
```  
BOOL ResetEvent();
```  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 這會導致所有想要存取這個事件，以等候的執行緒。  
  
 此成員函式不是由自動事件。  
  
##  <a name="setevent"></a>CEvent::SetEvent  
 釋放所有等候的執行緒會設定為收到信號，事件的狀態。  
  
```  
BOOL SetEvent();
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果函式成功，否則為 0。  
  
### <a name="remarks"></a>備註  
 是否手動事件，事件仍會收到信號，直到[ResetEvent](#resetevent)呼叫。 多個執行緒可以在此情況下發行。 如果自動事件，事件會保持已收到訊號，直到釋放單一執行緒。 系統接著會設定事件的狀態為未收到信號。 如果沒有執行緒等候，狀態會保留已收到訊號，直到會釋放一個執行緒。  
  
##  <a name="unlock"></a>CEvent::Unlock  
 釋放事件物件。  
  
```  
BOOL Unlock();
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果執行緒所擁有的事件物件和事件是自動的事件。否則為 0。  
  
### <a name="remarks"></a>備註  
 目前擁有自動事件來釋放之後完成，如果其鎖定的物件可重複使用的執行緒會呼叫此成員函式。 如果鎖定物件不是可重複使用，鎖定物件的解構函式會呼叫此函式。  
  
## <a name="see-also"></a>另請參閱  
 [CSyncObject 類別](../../mfc/reference/csyncobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)


