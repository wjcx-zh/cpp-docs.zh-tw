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
ms.openlocfilehash: 107ed227c5515cbf2fcb08e957a64a4a17d8287a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57288656"
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
|[CMultiLock::IsLocked](#islocked)|決定是否陣列中特定的同步處理的物件已被鎖定。|
|[CMultiLock::Lock](#lock)|會等候同步處理物件的陣列。|
|[CMultiLock::Unlock](#unlock)|釋放任何擁有同步處理物件。|

## <a name="remarks"></a>備註

`CMultiLock` 沒有基底類別。

若要使用同步類別[CSemaphore](../../mfc/reference/csemaphore-class.md)， [CMutex](../../mfc/reference/cmutex-class.md)，並[CEvent](../../mfc/reference/cevent-class.md)，您可以建立`CMultiLock`或[CSingleLock](../../mfc/reference/csinglelock-class.md)等候，並釋放同步物件的物件。 使用`CMultiLock`時有多個物件，您可以使用特定的時間。 使用`CSingleLock`您可能只需要等候上一個物件一次。

若要使用`CMultiLock`物件，請先建立您想要等候同步處理物件的陣列。 接下來，呼叫`CMultiLock`內受控制的資源類別中的成員函式物件的建構函式。 然後呼叫[鎖定](#lock)成員函式來判斷資源是否可用 （發出訊號）。 如果其中一個，請繼續使用此成員函式的其餘部分。 如果沒有資源可用時，等候指定的發行，資源的時間量，或傳回失敗。 資源使用完畢之後，呼叫[Unlock](#unlock)函式`CMultiLock`物件是使用一次，或允許`CMultiLock`来終結物件。

`CMultiLock` 物件是最有用的當執行緒必須一大堆`CEvent`它可以回應的物件。 建立陣列，包含所有`CEvent`指標，並呼叫`Lock`。 這會導致執行緒等候，直到其中一個事件收到信號。

如需有關如何使用`CMultiLock`物件，請參閱文章[多執行緒：如何使用同步類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`CMultiLock`

## <a name="requirements"></a>需求

**標頭：** afxmt.h

##  <a name="cmultilock"></a>  CMultiLock::CMultiLock

建構 `CMultiLock` 物件。

```
CMultiLock(
    CSyncObject* ppObjects [ ],
    DWORD dwCount,
    BOOL bInitialLock = FALSE);
```

### <a name="parameters"></a>參數

*ppObjects*<br/>
等候同步處理物件的指標陣列。 不可以是 NULL。

*dwCount*<br/>
中的物件數目*ppObjects*。 必須大於 0。

*bInitialLock*<br/>
指定是否一開始嘗試存取的任何提供的物件。

### <a name="remarks"></a>備註

建立要等候的同步處理物件的陣列之後，會呼叫此函數。 它通常會從呼叫，必須等到變成可用的同步處理物件的其中一個執行緒內。

##  <a name="islocked"></a>  CMultiLock::IsLocked

判斷指定的物件是否為未收到信號 （無法使用）。

```
BOOL IsLocked(DWORD dwItem);
```

### <a name="parameters"></a>參數

*dwItem*<br/>
正在查詢其狀態的物件相對應的物件陣列中的索引。

### <a name="return-value"></a>傳回值

如果指定的物件已鎖定，則為非零否則為 0。

##  <a name="lock"></a>  CMultiLock::Lock

呼叫此函式來存取一或多個資源提供給同步處理物件所控制的`CMultiLock`建構函式。

```
DWORD Lock(
    DWORD dwTimeOut = INFINITE,
    BOOL bWaitForAll = TRUE,
    DWORD dwWakeMask = 0);
```

### <a name="parameters"></a>參數

*dwTimeOut*<br/>
指定要同步處理物件可等候的時間量 （發出訊號）。 如果是無限的`Lock`會等候，直到物件收到信號之前傳回。

*bWaitForAll*<br/>
指定是否在等候的所有物件必須變成已收到都訊號在傳回之前相同的時間。 如果為 FALSE，`Lock`等候任何的物件一個而收到信號時，會傳回。

*dwWakeMask*<br/>
指定允許中止等候其他條件。 此參數的可用選項完整清單，請參閱 < [MsgWaitForMultipleObjects](/windows/desktop/api/winuser/nf-winuser-msgwaitformultipleobjects) Windows SDK 中。

### <a name="return-value"></a>傳回值

如果`Lock`失敗，則傳回-1。 如果成功，它會傳回下列值之一：

- WAIT_OBJECT_0 和 WAIT_OBJECT_0 + （數字的物件-1）

   如果*bWaitForAll*為 TRUE 時，所有物件都收到都信號 （可用）。 如果*bWaitForAll*為 FALSE，則傳回的值為 WAIT_OBJECT_0 為收到信號 （提供） 的物件之物件的陣列中的索引。

- WAIT_OBJECT_0 + （物件的數目）

   中指定的事件*dwWakeMask*可用執行緒的輸入佇列中。

- WAIT_ABANDONED_0 和 WAIT_ABANDONED_0 + （數字的物件-1）

   如果*bWaitForAll*為 TRUE，所有物件都收到都信號，而至少其中一個物件為已放棄的 mutex 物件。 如果*bWaitForAll*為 FALSE，則傳回值-WAIT_ABANDONED_0 已放棄的 mutex 物件滿足等候條件之物件的陣列中的索引。

- WAIT_TIMEOUT

   中指定的逾時間隔*dwTimeOut*過期但不等候成功。

### <a name="remarks"></a>備註

如果*bWaitForAll*為 TRUE，`Lock`只要同步處理的所有物件變成已收到都訊號同時將成功傳回。 如果*bWaitForAll*為 FALSE，`Lock`只要一或多個同步處理物件變成發出訊號會傳回。

如果`Lock`不能立即傳回，它會等待中指定的毫秒數不超過*dwTimeOut*傳回之前的參數。 如果*dwTimeOut*為 INFINITE，`Lock`將不會傳回，直到在獲得存取物件或條件中指定*dwWakeMask*已符合。 否則，如果`Lock`已能夠取得同步處理物件，它會傳回成功; 如果沒有，它會傳回失敗。

##  <a name="unlock"></a>  CMultiLock::Unlock

釋放所擁有的同步處理物件`CMultiLock`。

```
BOOL Unlock();

BOOL Unlock(
    LONG lCount,
    LPLONG lPrevCount = NULL);
```

### <a name="parameters"></a>參數

*lCount*<br/>
參考數目計數來釋放。 必須大於 0。 如果指定的數量會導致超過其最大值的物件的計數，計數不會變更，而且函式會傳回 FALSE。

*lPrevCount*<br/>
指向接收之同步處理物件的先前計數的變數。 如果是 NULL，不會傳回上一個計數。

### <a name="return-value"></a>傳回值

如果函式時成功則為非零否則為 0。

### <a name="remarks"></a>備註

此函式會呼叫`CMultiLock`的解構函式。

第一種形式`Unlock`嘗試解除鎖定由管理的同步處理物件`CMultiLock`。 第二個形式`Unlock`嘗試解除鎖定`CSemaphore`所擁有的物件`CMultiLock`。 如果`CMultiLock`沒有任何鎖定`CSemaphore`物件，則函數會傳回 FALSE，否則它會傳回 TRUE。 *lCount*並*lpPrevCount*並完全相同的參數[CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock)。 第二個形式`Unlock`很少適用於 multilock 的情況。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)
