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
ms.openlocfilehash: a051c6a510c53ac0c7c0a6efd8b4b5720080b264
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319718"
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
|[C 多重鎖定:C 多重鎖](#cmultilock)|建構 `CMultiLock` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[C 多重鎖定鎖定](#islocked)|確定陣列中的特定同步物件是否鎖定。|
|[C 多重鎖定鎖定](#lock)|等待同步物件的陣列。|
|[C 多重鎖定:解鎖](#unlock)|釋放任何擁有的同步物件。|

## <a name="remarks"></a>備註

`CMultiLock`沒有基類。

要使用同步類[CSemaphore、CMutex](../../mfc/reference/csemaphore-class.md)和[CEvent](../../mfc/reference/cevent-class.md),您`CMultiLock`可以建立一個或[CSingleLock](../../mfc/reference/csinglelock-class.md)物件來[CMutex](../../mfc/reference/cmutex-class.md)等待並釋放同步物件。 `CMultiLock`當在特定時間可以使用多個物件時使用。 在`CSingleLock`一次只需等待一個物件時使用。

要使用物件`CMultiLock`,請先建立要等待的同步物件的陣列。 接下來,在`CMultiLock`受控資源類中的成員函數內調用對象的構造函數。 然後調用[Lock](#lock)成員函數以確定資源是否可用(信號)。 如果是,請繼續執行成員函數的其餘部分。 如果沒有可用資源,請等待指定的時間釋放資源,或返回失敗。 資源使用完成後,如果要再次使用該物件,[Unlock](#unlock)`CMultiLock`則調用 Unlock 函數,或者`CMultiLock`允許銷毀 該物件。

`CMultiLock`當線程具有大量可以回應`CEvent`的物件時,物件最有用。 建立包含所有指標的`CEvent`陣列,並呼叫`Lock`。 這將導致線程等待,直到其中一個事件發出信號。

有關如何使用`CMultiLock`物件的詳細資訊,請參閱"[多線程:如何使用同步類](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)「一文。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CMultiLock`

## <a name="requirements"></a>需求

**標題:** afxmt.h

## <a name="cmultilockcmultilock"></a><a name="cmultilock"></a>C 多重鎖定:C 多重鎖

建構 `CMultiLock` 物件。

```
CMultiLock(
    CSyncObject* ppObjects [ ],
    DWORD dwCount,
    BOOL bInitialLock = FALSE);
```

### <a name="parameters"></a>參數

*ppObjects*<br/>
指向要等待的同步物件的指標陣列。 不能是 NULL。

*dw( Dw) Count*<br/>
*ppObjects*中的物件數。 必須大於 0。

*b 初始鎖定*<br/>
指定是否最初嘗試訪問任何提供的物件。

### <a name="remarks"></a>備註

在創建要等待的同步物件陣列後調用此函數。 它通常從線程內調用,線程必須等待其中一個同步物件變為可用。

## <a name="cmultilockislocked"></a><a name="islocked"></a>C 多重鎖定鎖定

確定指定物件是否非信號(不可用)。

```
BOOL IsLocked(DWORD dwItem);
```

### <a name="parameters"></a>參數

*dwItem*<br/>
與正在查詢其狀態的物件對應的物件陣列中的索引。

### <a name="return-value"></a>傳回值

如果指定對象被鎖定,則非零;否則 0。

## <a name="cmultilocklock"></a><a name="lock"></a>C 多重鎖定鎖定

調用此函數以造訪由提供`CMultiLock`給建構函數的同步物件控制的一個或多個資源。

```
DWORD Lock(
    DWORD dwTimeOut = INFINITE,
    BOOL bWaitForAll = TRUE,
    DWORD dwWakeMask = 0);
```

### <a name="parameters"></a>參數

*dwTimeOut*<br/>
指定等待同步物件可用(信號)的時間量。 如果 INFINITE,`Lock`將等待物件發出信號後再返回。

*bWaitForall*<br/>
指定是否等待的所有物件必須同時發出信號才能返回。 如果 FALSE,`Lock`將在等待的任何物件發出信號時返回。

*dwWakeMask*<br/>
指定允許中止等待的其他條件。 有關此參數的可用選項的完整清單,請參閱 Windows SDK 中的[MsgWaitForMulti 物件](/windows/win32/api/winuser/nf-winuser-msgwaitformultipleobjects)。

### <a name="return-value"></a>傳回值

如果`Lock`失敗,它將返回 - 1。 如果成功,它將返回以下值之一:

- 介於WAIT_OBJECT_0和WAIT_OBJECT_0 + 之間(物件數 - 1)

   如果*bWaitForAll*為 TRUE,則所有物件都發出信號(可用)。 如果*bWaitForAll*為 FALSE,則返回值 - WAIT_OBJECT_0是發出信號(可用)的物件陣列中的索引。

- WAIT_OBJECT_0 = (物件數)

   在*dwWakeMask*中指定的事件線上程的輸入佇列中可用。

- 介於WAIT_ABANDONED_0和WAIT_ABANDONED_0之間 = (物件數 - 1)

   如果*bWaitForAll*為 TRUE,則所有物件都發出信號,並且至少有一個對像是廢棄的互斥體。 如果*bWaitForAll*是 FALSE,則返回值 - WAIT_ABANDONED_0是滿足等待的廢棄互斥體物件陣列中的索引。

- WAIT_TIMEOUT

   *在 dwTimeOut*中指定的超時間隔已過期,等待時間未成功。

### <a name="remarks"></a>備註

如果*bWaitForAll*為`Lock`TRUE,則一旦所有同步物件同時發出信號,將立即成功返回。 如果*bWaitForAll*為`Lock`FALSE,則一旦一個或多個同步物件發出信號,將立即返回。

如果`Lock`無法立即返回,它將等待不超過*dwTimeOut*參數中指定的毫秒數,然後再返回。 如果*dwTimeOut*是`Lock`INFINITE,則在獲得對物件的訪問許可權或滿足*dwWakeMask*中指定的條件之前,不會返回。 否則,如果`Lock`能夠獲取同步物件,它將成功返回;否則,它將成功返回。如果不是,它將返回失敗。

## <a name="cmultilockunlock"></a><a name="unlock"></a>C 多重鎖定:解鎖

釋放 擁有`CMultiLock`的同步物件。

```
BOOL Unlock();

BOOL Unlock(
    LONG lCount,
    LPLONG lPrevCount = NULL);
```

### <a name="parameters"></a>參數

*l. Count*<br/>
要釋放的引用計數數。 必須大於 0。 如果指定量將導致物件的計數超過其最大值,則計數不會更改,並且函數將返回 FALSE。

*lPrev( A) Count*<br/>
指向變數以接收同步物件的上一個計數。 如果為 NULL,則不返回以前的計數。

### <a name="return-value"></a>傳回值

如果函數成功,則非零;否則 0。

### <a name="remarks"></a>備註

此函數由`CMultiLock`析構函數調用。

`Unlock`嘗試解鎖`CMultiLock`由管理的同步物件的第一種形式。 嘗試解鎖`Unlock``CSemaphore``CMultiLock`擁有的物件的第二種形式。 如果沒有`CMultiLock`任何`CSemaphore`鎖定的物件,函數將返回 FALSE;如果函數不具有"FALSE"功能。否則,它將返回 TRUE。 *lCount*和*lpPrevCount*與[CSingleLock 的參數完全相同::解鎖](../../mfc/reference/csinglelock-class.md#unlock)。 第二種形式`Unlock`很少適用於多鎖情況。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)
