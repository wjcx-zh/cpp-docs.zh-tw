---
title: CMultiLock 類別
ms.date: 11/04/2016
f1_keywords:
- CMultiLock
- AFXMT/CMultiLock
- AFXMT/CMultiLock::CMultiLock
- AFXMT/CMultiLock::IsLocked
- AFXMT/CMultiLock::Lock
- AFXMT/CMultiLock::Unlock
helpviewer_keywords:
- CMultiLock [MFC], CMultiLock
- CMultiLock [MFC], IsLocked
- CMultiLock [MFC], Lock
- CMultiLock [MFC], Unlock
ms.assetid: c5b7c78b-1f81-4387-b7dd-2c813c5b6b61
ms.openlocfilehash: b2fe3ecf2197b8edb13e89600b16e550deff9af2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504542"
---
# <a name="cmultilock-class"></a>CMultiLock 類別

代表多執行緒程式用來控制多個資源存取的存取控制機制。

## <a name="syntax"></a>語法

```
class CMultiLock
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMultiLock::CMultiLock](#cmultilock)|建構 `CMultiLock` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMultiLock::IsLocked](#islocked)|判斷陣列中的特定同步處理物件是否已鎖定。|
|[CMultiLock::Lock](#lock)|等候同步處理物件的陣列。|
|[CMultiLock::Unlock](#unlock)|釋放任何擁有的同步處理物件。|

## <a name="remarks"></a>備註

`CMultiLock`沒有基類。

若要使用同步處理類別[CSemaphore](../../mfc/reference/csemaphore-class.md)、 [CMutex](../../mfc/reference/cmutex-class.md)和[CEvent](../../mfc/reference/cevent-class.md), `CMultiLock`您可以建立或[CSingleLock](../../mfc/reference/csinglelock-class.md)物件, 以等待並釋放同步處理物件。 當`CMultiLock`有多個物件可供您在特定時間使用時, 請使用。 當`CSingleLock`您一次只需要等候一個物件時, 請使用。

若要使用`CMultiLock`物件, 請先建立您想要等候之同步處理物件的陣列。 接下來, 在`CMultiLock`受控制資源類別中的成員函式內呼叫物件的「函式」 (function)。 然後呼叫[Lock](#lock)成員函式, 以判斷是否有可用的資源 (信號)。 如果其中一個是, 請繼續進行成員函式的其餘部分。 如果沒有可用的資源, 請等候一段指定的時間來釋放資源, 或傳回失敗。 資源的使用完成後, 如果`CMultiLock`要再次使用物件`CMultiLock` , 請呼叫[Unlock](#unlock)函式, 或允許終結物件。

`CMultiLock`當執行緒具有可回應的大量`CEvent`物件時, 物件最有用。 建立包含所有指標的`CEvent`陣列, 並呼叫。 `Lock` 這會導致執行緒等待, 直到其中一個事件收到信號為止。

如需如何使用`CMultiLock`物件的詳細資訊, 請參閱[多執行緒:如何使用同步處理類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`CMultiLock`

## <a name="requirements"></a>需求

**標頭:** afxmt。h

##  <a name="cmultilock"></a>CMultiLock::CMultiLock

建構 `CMultiLock` 物件。

```
CMultiLock(
    CSyncObject* ppObjects [ ],
    DWORD dwCount,
    BOOL bInitialLock = FALSE);
```

### <a name="parameters"></a>參數

*ppObjects*<br/>
要等候之同步處理物件的指標陣列。 不可以是 NULL。

*dwCount*<br/>
*PpObjects*中的物件數目。 必須大於 0。

*bInitialLock*<br/>
指定最初是否嘗試存取任何提供的物件。

### <a name="remarks"></a>備註

建立要等候的同步處理物件陣列之後, 會呼叫這個函式。 通常是從執行緒內呼叫, 必須等候其中一個同步處理物件變成可用。

##  <a name="islocked"></a>CMultiLock:: IsLocked

判斷指定的物件是否為未收到信號 (無法使用)。

```
BOOL IsLocked(DWORD dwItem);
```

### <a name="parameters"></a>參數

*dwItem*<br/>
物件陣列中的索引, 其對應至正在查詢其狀態的物件。

### <a name="return-value"></a>傳回值

如果指定的物件已鎖定, 則為非零值;否則為0。

##  <a name="lock"></a>  CMultiLock::Lock

呼叫此函式可存取提供給`CMultiLock`此函式的同步處理物件所控制的一或多個資源。

```
DWORD Lock(
    DWORD dwTimeOut = INFINITE,
    BOOL bWaitForAll = TRUE,
    DWORD dwWakeMask = 0);
```

### <a name="parameters"></a>參數

*dwTimeOut*<br/>
指定等候同步處理物件可用的時間量 (已發出信號)。 如果是無限`Lock` , 則會等到物件收到信號後才傳回。

*bWaitForAll*<br/>
指定在傳回之前, 是否所有等待的物件都必須在同一時間收到信號。 如果為 FALSE `Lock` , 則會在任何等待的物件收到信號時傳回。

*dwWakeMask*<br/>
指定允許中止等候的其他條件。 如需此參數可用選項的完整清單, 請參閱 Windows SDK 中的[MsgWaitForMultipleObjects](/windows/win32/api/winuser/nf-winuser-msgwaitformultipleobjects) 。

### <a name="return-value"></a>傳回值

如果`Lock`失敗, 則會傳回-1。 如果成功, 則會傳回下列其中一個值:

- 介於 WAIT_OBJECT_0 和 WAIT_OBJECT_0 + (物件數目-1)

   如果*bWaitForAll*為 TRUE, 則所有物件都會收到信號 (可供使用)。 如果*bWaitForAll*為 FALSE, 則傳回值-WAIT_OBJECT_0 是已發出信號之物件的物件陣列中的索引 (可用)。

- WAIT_OBJECT_0 + (物件數目)

   在*dwWakeMask*中指定的事件可以線上程的輸入佇列中取得。

- 介於 WAIT_ABANDONED_0 和 WAIT_ABANDONED_0 + (物件數目-1)

   如果*bWaitForAll*為 TRUE, 則會發出所有物件的信號, 而且至少有一個物件是已放棄的 mutex 物件。 如果*bWaitForAll*為 FALSE, 則傳回值-WAIT_ABANDONED_0 是已放棄之 mutex 物件的物件陣列中, 滿足等候的索引。

- WAIT_TIMEOUT

   在*dwTimeOut*中指定的逾時間隔已過期, 而沒有等候成功。

### <a name="remarks"></a>備註

如果*bWaitForAll*為 TRUE, `Lock`則會在所有同步處理物件都同時發出信號時, 立即傳回成功。 如果*bWaitForAll*為 FALSE, `Lock`則會在一或多個同步處理物件變成信號時立即傳回。

如果`Lock`無法立即傳回, 它將會等候*dwTimeOut*參數中指定的毫秒數, 然後再傳回。 如果*dwTimeOut*是無限的`Lock` , 必須等到取得物件的存取權, 或符合*dwWakeMask*中指定的條件時, 才會返回。 否則, 如果`Lock`能夠取得同步處理物件, 則會成功傳回; 如果不是, 則會傳回失敗。

##  <a name="unlock"></a>  CMultiLock::Unlock

釋放所擁有`CMultiLock`的同步處理物件。

```
BOOL Unlock();

BOOL Unlock(
    LONG lCount,
    LPLONG lPrevCount = NULL);
```

### <a name="parameters"></a>參數

*lCount*<br/>
要釋放的參考計數數目。 必須大於 0。 如果指定的數量會導致物件的計數超過其最大值, 則不會變更計數, 而且函數會傳回 FALSE。

*lPrevCount*<br/>
指向變數, 以接收同步處理物件的先前計數。 如果是 Null, 則不會傳回先前的計數。

### <a name="return-value"></a>傳回值

如果函式成功, 則為非零;否則為0。

### <a name="remarks"></a>備註

這個函式是由`CMultiLock`的「析構函數」呼叫。

第一種`Unlock`形式會嘗試解除鎖定`CMultiLock`受管理的同步處理物件。 的第二種`Unlock`形式會嘗試解除`CSemaphore`鎖定所擁有`CMultiLock`的物件。 如果`CMultiLock`不擁有任何鎖定`CSemaphore`的物件, 此函式會傳回 FALSE, 否則會傳回 TRUE。 *lCount*和*lpPrevCount*與[CSingleLock:: Unlock](../../mfc/reference/csinglelock-class.md#unlock)的參數完全相同。 的第二種`Unlock`形式很少適用于 multilock 情況。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)
