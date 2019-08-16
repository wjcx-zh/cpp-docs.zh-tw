---
title: CEvent 類別
ms.date: 11/04/2016
f1_keywords:
- CEvent
- AFXMT/CEvent
- AFXMT/CEvent::CEvent
- AFXMT/CEvent::PulseEvent
- AFXMT/CEvent::ResetEvent
- AFXMT/CEvent::SetEvent
- AFXMT/CEvent::Unlock
helpviewer_keywords:
- CEvent [MFC], CEvent
- CEvent [MFC], PulseEvent
- CEvent [MFC], ResetEvent
- CEvent [MFC], SetEvent
- CEvent [MFC], Unlock
ms.assetid: df676042-ce27-4702-800a-e73ff4f44395
ms.openlocfilehash: fbf2d834163199107aae44bd5723ceff79e36f91
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506682"
---
# <a name="cevent-class"></a>CEvent 類別

表示事件, 這是一個同步處理物件, 可讓一個執行緒通知另一個事件已發生。

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
|[CEvent::PulseEvent](#pulseevent)|將事件設定為 [可用 (已通知)]、[釋放等待的執行緒], 並將事件設定為 [無法使用] (未收到信號)。|
|[CEvent::ResetEvent](#resetevent)|將事件設定為無法使用 (未收到信號)。|
|[CEvent::SetEvent](#setevent)|將事件設定為 [可用 (已通知)], 並釋放任何等候中的執行緒。|
|[CEvent::Unlock](#unlock)|釋放事件物件。|

## <a name="remarks"></a>備註

當執行緒必須知道何時執行其工作時, 事件會很有用。 例如, 將資料複製到資料封存的執行緒必須在有新資料可用時收到通知。 藉由使用`CEvent`物件, 在有新的資料可用時通知複製執行緒, 執行緒可以儘快執行其工作。

`CEvent`物件有兩種類型: [手動] 和 [自動]。

自動`CEvent`物件會在至少釋放一個執行緒後, 自動返回非信號 (無法使用) 的狀態。 根據預設, 除非`CEvent`您在結構中傳遞`TRUE` *bManualReset*參數, 否則物件會是自動的。

手動`CEvent`物件會維持在[SetEvent](#setevent)或[ResetEvent](#resetevent)所設定的狀態, 直到呼叫另一個函式為止。 若要建立手動`CEvent`物件, 請`TRUE`在結構`bManualReset`中傳遞參數。

若要使用`CEvent`物件, 請在`CEvent`需要時建立物件。 指定您想要等候的事件名稱, 同時指定您的應用程式一開始應該擁有它。 接著, 您可以在此函式傳回時存取事件。 呼叫[SetEvent](#setevent)以表示 (提供) 事件物件, 然後在您完成存取受控制的資源時呼叫[解除鎖定](#unlock)。

使用`CEvent`物件的替代方法是將類型`CEvent`的變數當做資料成員加入至您要控制的類別。 在結構控制物件的建立期間, 呼叫`CEvent`資料成員的函式, 並指定是否一開始會發出事件的信號, 以及 specifythe 您想要的事件物件的類型, 也就是事件的名稱 (如果它將跨進程使用的話)界限), 以及您想要的任何安全性屬性。

若要以這種方式存取`CEvent`物件所控制的資源, 請先在資源的存取方法中, 建立類型為[CSingleLock](../../mfc/reference/csinglelock-class.md)或類型為[CMultiLock](../../mfc/reference/cmultilock-class.md)的變數。 然後呼叫`Lock` lock 物件的方法 (例如, [CMultiLock:: lock](../../mfc/reference/cmultilock-class.md#lock))。 此時, 您的執行緒將會取得資源的存取權、等待資源釋放並取得存取權, 或等待資源釋放、超時, 而且無法存取資源。 在任何情況下, 您的資源都是以執行緒安全的方式存取。 若要釋放資源, 請`SetEvent`呼叫來表示事件物件, 然後使用鎖定物件`Unlock`的方法 (例如, [CMultiLock:: Unlock](../../mfc/reference/cmultilock-class.md#unlock)), 或讓鎖定物件超出範圍。

如需如何使用`CEvent`物件的詳細資訊, 請參閱[多執行緒:如何使用同步處理類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。

## <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#45](../../mfc/codesnippet/cpp/cevent-class_1.cpp)]

[!code-cpp[NVC_MFC_Utilities#46](../../mfc/codesnippet/cpp/cevent-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CEvent`

## <a name="requirements"></a>需求

**標頭:** afxmt。h

##  <a name="cevent"></a>CEvent::CEvent

構造已命名或未`CEvent`命名的物件。

```
CEvent(
    BOOL bInitiallyOwn = FALSE,
    BOOL bManualReset = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>參數

*bInitiallyOwn*<br/>
如果為 TRUE, 則表示已`CMultilock`啟用`CSingleLock`或物件的執行緒。 否則, 所有想要存取資源的執行緒都必須等候。

*bManualReset*<br/>
若為 TRUE, 則指定事件物件為手動事件, 否則事件物件為自動事件。

*lpszName*<br/>
`CEvent` 物件的名稱。 如果物件將跨進程界限使用, 則必須提供。 如果名稱與現有的事件相符, 則此函式會`CEvent`建立參考該名稱之事件的新物件。 如果名稱符合不是事件的現有同步處理物件, 則結構將會失敗。 如果是 Null, 此名稱將會是 null。

*lpsaAttribute*<br/>
事件物件的安全性屬性。 如需此結構的完整說明, 請參閱 Windows SDK 中的[security attributes 這個](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))。

### <a name="remarks"></a>備註

若要存取或釋放`CEvent`物件, 請建立[CMultiLock](../../mfc/reference/cmultilock-class.md)或[CSingleLock](../../mfc/reference/csinglelock-class.md)物件, 並呼叫其[Lock](../../mfc/reference/csinglelock-class.md#lock)和[Unlock](../../mfc/reference/csinglelock-class.md#unlock)成員函式。

若要將`CEvent`物件的狀態變更為已發出信號 (執行緒不需要等候), 請呼叫[SetEvent](#setevent)或[PulseEvent](#pulseevent)。 若要將`CEvent`物件的狀態設定為未收到信號 (執行緒必須等候), 請呼叫[ResetEvent](#resetevent)。

> [!IMPORTANT]
>  建立`CEvent`物件之後, 請使用[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)來確保 mutex 尚未存在。 如果 mutex 意外存在, 可能表示有惡意的進程佔用, 而且可能會有意使用此 mutex。 在此情況下, 建議的安全性意識程式是關閉控制碼, 並繼續執行, 就像建立物件失敗一樣。

##  <a name="pulseevent"></a>CEvent::P ulseEvent

將事件的狀態設定為 [已通知 (可用)]、釋放任何等待中的執行緒, 並自動將它重設為 [未收到信號 (無法使用)]。

```
BOOL PulseEvent();
```

### <a name="return-value"></a>傳回值

如果函式成功, 則為非零;否則為0。

### <a name="remarks"></a>備註

如果事件是手動, 則會釋放所有等候中的執行緒、將事件設定為未收到信號, `PulseEvent`然後傳回。 如果事件是自動的, 則會釋放單一線程, 事件會設定為未收到信號, 並`PulseEvent`傳回。

如果沒有線程在等候中, 或沒有任何執行緒可以立即釋放`PulseEvent` , 會將事件的狀態設定為未收到信號, 並傳回。

`PulseEvent`會使用基礎 Win32 `PulseEvent`函式, 該函數可以透過核心模式非同步程序呼叫, 從等候狀態中暫時移除。 因此, `PulseEvent`不可靠, 而且不應該供新的應用程式使用。 如需詳細資訊, 請參閱[PulseEvent 函數](/windows/win32/api/winbase/nf-winbase-pulseevent)。

##  <a name="resetevent"></a>CEvent::ResetEvent

將事件的狀態設定為未收到信號, 直到明確設定為由[SetEvent](#setevent)成員函式發出信號為止。

```
BOOL ResetEvent();
```

### <a name="return-value"></a>傳回值

如果函式成功, 則為非零;否則為0。

### <a name="remarks"></a>備註

這會導致所有想要存取此事件的執行緒等待。

自動事件不會使用這個成員函式。

##  <a name="setevent"></a>CEvent::SetEvent

將事件的狀態設定為已發出信號, 並釋放任何等候中的執行緒。

```
BOOL SetEvent();
```

### <a name="return-value"></a>傳回值

如果函式成功, 則為非零, 否則為0。

### <a name="remarks"></a>備註

如果事件是手動的, 事件會保持信號, 直到呼叫[ResetEvent](#resetevent)為止。 在此情況下, 可以釋放一個以上的執行緒。 如果事件是自動的, 事件會保持信號, 直到單一執行緒釋放為止。 然後, 系統會將事件的狀態設定為未收到信號。 如果沒有線程在等候, 則狀態會保持為信號, 直到釋放一個執行緒為止。

##  <a name="unlock"></a>CEvent:: Unlock

釋放事件物件。

```
BOOL Unlock();
```

### <a name="return-value"></a>傳回值

如果執行緒擁有事件物件, 而事件是自動事件, 則為非零。否則為0。

### <a name="remarks"></a>備註

目前擁有自動事件的執行緒會呼叫這個成員函式, 以便在完成之後釋放, 如果要重複使用它們的鎖定物件的話。 如果不要重複使用鎖定物件, 則鎖定物件的析構函式將會呼叫這個函數。

## <a name="see-also"></a>另請參閱

[CSyncObject 類別](../../mfc/reference/csyncobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
