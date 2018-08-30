---
title: CEvent 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 301549e26212448ae0392a356aa556358dcf6f47
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205459"
---
# <a name="cevent-class"></a>CEvent 類別
代表事件，也就是讓一個執行緒通知發生事件的另一個執行緒的同步處理物件。  
  
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
|[CEvent::PulseEvent](#pulseevent)|設定要使用的事件 （通知），釋放等待中執行緒，並將事件設定為 無法使用 （未收到信號）。|  
|[CEvent::ResetEvent](#resetevent)|將事件設定為無法使用 （未收到信號）。|  
|[CEvent::SetEvent](#setevent)|設定為 使用的事件 （已發出訊號），並釋放所有等候中執行緒。|  
|[CEvent::Unlock](#unlock)|釋放事件物件。|  
  
## <a name="remarks"></a>備註  
 當執行緒必須知道何時要執行其工作，則事件會很有用。 比方說，當新資料可用時，將資料複製到資料封存的執行緒就必須收到通知。 使用`CEvent`物件以新資料可用時，通知複製執行緒的執行緒可以儘速執行其工作。  
  
 `CEvent` 物件有兩種類型： 手動和自動。  
  
 自動`CEvent`物件會自動傳回為未收到信號的 （無法使用） 狀態之後至少一個執行緒釋放。 根據預設，`CEvent`物件是自動的除非您傳遞`TRUE`for *bManualReset*在建構期間的參數。  
  
 手動`CEvent`物件會留在所設定的狀態[SetEvent](#setevent)或是[ResetEvent](#resetevent)之前會呼叫其他函式。 若要建立手動`CEvent`物件，傳遞`TRUE`的`bManualReset`在建構期間的參數。  
  
 若要使用`CEvent`物件，建構`CEvent`物件會在需要時。 指定您想要等候，以及指定您的應用程式一開始應該擁有該事件的名稱。 然後，您可以存取的建構函式傳回的事件。 呼叫[SetEvent](#setevent)訊號 （供） 事件物件，然後再呼叫[Unlock](#unlock)完成時存取控制的資源。  
  
 使用替代方法`CEvent`物件是新增類型的變數`CEvent`以您想要控制的類別資料成員。 在建構期間之受控制的物件，呼叫的建構函式`CEvent`資料成員，並指定是否一開始收到信號的事件，和也 specifythe 物件型別事件要事件 （如果它將用於跨處理序的名稱界限），以及您想要的任何安全性屬性。  
  
 若要存取所控制的資源`CEvent`物件以這種方式，請先建立兩種類型的變數[CSingleLock](../../mfc/reference/csinglelock-class.md)或型別[CMultiLock](../../mfc/reference/cmultilock-class.md)您資源的存取方法中。 然後呼叫`Lock`之鎖定物件的方法 (例如[CMultiLock::Lock](../../mfc/reference/cmultilock-class.md#lock))。 此時，您的執行緒會存取資源、 釋出，並存取應用程式，或等待資源釋出資源等候、 逾時，並無法取得資源的存取權。 在任何情況下，您的資源已存取具備執行緒安全的方式。 若要釋放資源，呼叫`SetEvent`訊號事件物件，然後使用`Unlock`之鎖定物件的方法 (比方說， [CMultiLock::Unlock](../../mfc/reference/cmultilock-class.md#unlock))，或讓超出範圍的鎖定物件。  
  
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
  
##  <a name="cevent"></a>  CEvent::CEvent  
 建構具名或未命名`CEvent`物件。  
  
```  
CEvent(
    BOOL bInitiallyOwn = FALSE,  
    BOOL bManualReset = FALSE,  
    LPCTSTR lpszName = NULL,  
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```  
  
### <a name="parameters"></a>參數  
 *bInitiallyOwn*  
 如果為 TRUE，如執行緒`CMultilock`或`CSingleLock`啟用物件。 否則，必須等到所有想要存取資源的執行緒。  
  
 *bManualReset*  
 如果為 TRUE，會指定事件的物件為手動事件，否則為事件物件是自動的事件。  
  
 *lpszName*  
 `CEvent` 物件的名稱。 如果該物件會使用跨處理序界限，必須提供。 如果名稱符合現有的事件，建構函式會建置新`CEvent`物件會參考該名稱的事件。 如果名稱符合現有的同步處理物件，不是事件，建構將會失敗。 如果是 NULL，則會有名稱為 null。  
  
 *lpsaAttribute*  
 事件物件的安全性屬性。 如需這個結構的完整說明，請參閱[SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) Windows SDK 中。  
  
### <a name="remarks"></a>備註  
 存取或釋放`CEvent`物件，建立[CMultiLock](../../mfc/reference/cmultilock-class.md)或[CSingleLock](../../mfc/reference/csinglelock-class.md)物件並呼叫其[鎖定](../../mfc/reference/csinglelock-class.md#lock)並[解除鎖定](../../mfc/reference/csinglelock-class.md#unlock)成員函式。  
  
 若要變更的狀態`CEvent`物件已收到訊號 （執行緒就不必等候），呼叫[SetEvent](#setevent)或是[PulseEvent](#pulseevent)。 若要設定的狀態`CEvent`為未收到信號的物件 （執行緒就必須等候），呼叫[ResetEvent](#resetevent)。  
  
> [!IMPORTANT]
>  在建立後`CEvent`物件，請使用[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)以確保 mutex 不存在。 如果存在非預期地 mutex，可能表示處理序會佔用，而且可能會想要進行惡意使用 mutex。 在此情況下，建議的注重安全性的程序會關閉控制代碼，並繼續如同在建立物件時發生失敗。  
  
##  <a name="pulseevent"></a>  CEvent::PulseEvent  
 將狀態設定為收到信號的事件 （提供）、 釋放所有等候中執行緒，並且將它重設為未收到信號 （無法使用） 會自動。  
  
```  
BOOL PulseEvent();
```  
  
### <a name="return-value"></a>傳回值  
 如果函式時成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 如果事件為手動，會釋放所有等候中執行緒，將事件設定為未收到信號，和`PulseEvent`傳回。 如果事件是自動的在釋放單一執行緒，將事件設定為未收到信號，和`PulseEvent`傳回。  
  
 如果沒有執行緒在等候，或沒有任何執行緒可以立即釋放`PulseEvent`設定至事件的狀態為未收到訊號，並傳回。  
  
 `PulseEvent` 使用基本 Win32`PulseEvent`函式，可以暫時移除從等候狀態的核心模式的非同步程序呼叫。 因此，`PulseEvent`不可靠，而且不應由新的應用程式。 如需詳細資訊，請參閱 < [PulseEvent 函式](/windows/desktop/api/winbase/nf-winbase-pulseevent)。  
  
##  <a name="resetevent"></a>  CEvent::ResetEvent  
 設定事件的狀態未收到信號，直到明確設定 藉由為已收到訊號[SetEvent](#setevent)成員函式。  
  
```  
BOOL ResetEvent();
```  
  
### <a name="return-value"></a>傳回值  
 如果函式時成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 這會導致所有想要存取這個事件，以等候的執行緒。  
  
 此成員函式不會自動事件所使用。  
  
##  <a name="setevent"></a>  CEvent::SetEvent  
 釋放所有等候中執行緒會設定為收到信號，事件的狀態。  
  
```  
BOOL SetEvent();
```  
  
### <a name="return-value"></a>傳回值  
 非零值，如果函式成功，否則為 0。  
  
### <a name="remarks"></a>備註  
 如果事件為手動，事件會保持收到訊號的狀態，直到[ResetEvent](#resetevent)呼叫。 多個執行緒可以在此情況下發行。 如果事件是自動的事件會保持收到訊號的狀態，直到釋放單一執行緒。 為未收到信號，系統會將事件的狀態。 如果沒有執行緒在等候時，狀態會維持收到訊號的狀態，直到釋放一個執行緒。  
  
##  <a name="unlock"></a>  CEvent::Unlock  
 釋放事件物件。  
  
```  
BOOL Unlock();
```  
  
### <a name="return-value"></a>傳回值  
 非零值，如果執行緒擁有事件的物件和事件是自動的事件，否則為 0。  
  
### <a name="remarks"></a>備註  
 目前擁有自動釋放之後完成，如果其鎖定的物件可重複使用事件的執行緒會呼叫此成員函式。 鎖定物件是否不到可重複使用，鎖定物件的解構函式將會呼叫此函式。  
  
## <a name="see-also"></a>另請參閱  
 [CSyncObject 類別](../../mfc/reference/csyncobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)

