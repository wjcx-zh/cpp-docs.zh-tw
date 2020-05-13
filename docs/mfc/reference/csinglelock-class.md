---
title: CSingleLock 類別
ms.date: 11/04/2016
f1_keywords:
- CSingleLock
- AFXMT/CSingleLock
- AFXMT/CSingleLock::CSingleLock
- AFXMT/CSingleLock::IsLocked
- AFXMT/CSingleLock::Lock
- AFXMT/CSingleLock::Unlock
helpviewer_keywords:
- CSingleLock [MFC], CSingleLock
- CSingleLock [MFC], IsLocked
- CSingleLock [MFC], Lock
- CSingleLock [MFC], Unlock
ms.assetid: 7dae7288-8066-4a3e-85e0-78d28bfc6bc8
ms.openlocfilehash: 231397228d94e58665602453b5d377571e24a967
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318263"
---
# <a name="csinglelock-class"></a>CSingleLock 類別

代表多執行緒程式用來控制單一資源存取的存取控制機制。

## <a name="syntax"></a>語法

```
class CSingleLock
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[單一鎖:C單鎖](#csinglelock)|建構 `CSingleLock` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[單一鎖定鎖定](#islocked)|確定物件是否鎖定。|
|[單鎖:鎖定](#lock)|在同步物件上等待。|
|[單鎖:解鎖](#unlock)|釋放同步物件。|

## <a name="remarks"></a>備註

`CSingleLock`沒有基類。

為了使用同步類[CSemaphore、CMutex、C](../../mfc/reference/csemaphore-class.md)[關鍵節](../../mfc/reference/ccriticalsection-class.md)和[CEvent,](../../mfc/reference/cevent-class.md)必須創建一個`CSingleLock`或[CMultiLock](../../mfc/reference/cmultilock-class.md)物件[CMutex](../../mfc/reference/cmutex-class.md)來等待並釋放同步物件。 在`CSingleLock`一次只需等待一個物件時使用。 `CMultiLock`當在特定時間可以使用多個物件時使用。

要使用`CSingleLock`物件,請將其建構函數調用受控資源類中的成員函數內。 然後調用[IsLocked](#islocked)成員函數以確定資源是否可用。 如果是,請繼續執行成員函數的其餘部分。 如果資源不可用,請等待指定的時間量以釋放資源,或返回失敗。 資源使用完成後,如果要再次使用該物件,[Unlock](#unlock)`CSingleLock`則調用 Unlock 函數,或者`CSingleLock`允許銷毀 該物件。

`CSingleLock`物件需要存在從[CSyncObject](../../mfc/reference/csyncobject-class.md)派生的物件。 這通常是受控資源類的數據成員。 有關如何使用`CSingleLock`物件的詳細資訊,請參閱"[多線程:如何使用同步類](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)「一文。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CSingleLock`

## <a name="requirements"></a>需求

**標題:** afxmt.h

## <a name="csinglelockcsinglelock"></a><a name="csinglelock"></a>單一鎖:C單鎖

建構 `CSingleLock` 物件。

```
explicit CSingleLock(
    CSyncObject* pObject,
    BOOL bInitialLock = FALSE);
```

### <a name="parameters"></a>參數

*pObject*<br/>
指向要訪問的同步物件。 不能是 NULL。

*b 初始鎖定*<br/>
指定是否最初嘗試訪問提供的物件。

### <a name="remarks"></a>備註

此函數通常從受控資源的訪問成員函數內調用。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#19](../../mfc/codesnippet/cpp/csinglelock-class_1.h)]

## <a name="csinglelockislocked"></a><a name="islocked"></a>單一鎖定鎖定

確定與`CSingleLock`物件關聯的物件是否非信號(不可用)。

```
BOOL IsLocked();
```

### <a name="return-value"></a>傳回值

如果物件已鎖定,則非零;否則 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#20](../../mfc/codesnippet/cpp/csinglelock-class_2.h)]

## <a name="csinglelocklock"></a><a name="lock"></a>單鎖:鎖定

調用此函數以造訪由提供`CSingleLock`給建構函數的同步物件控制的資源。

```
BOOL Lock(DWORD dwTimeOut = INFINITE);
```

### <a name="parameters"></a>參數

*dwTimeOut*<br/>
指定等待同步物件可用(信號)的時間量。 如果 INFINITE,`Lock`將等待物件發出信號後再返回。

### <a name="return-value"></a>傳回值

如果函數成功,則非零;否則 0。

### <a name="remarks"></a>備註

如果同步物件發出信號,`Lock`將成功返回,並且線程現在擁有該物件。 如果同步物件是非信號(不可用),`Lock`則將等待同步物件發出信號,最多達到*dwTimeOut*參數中指定的毫秒數。 如果同步物件未在指定的時間內發出信號,則`Lock`返回失敗。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]

## <a name="csinglelockunlock"></a><a name="unlock"></a>單鎖:解鎖

釋放 擁有`CSingleLock`的同步物件。

```
BOOL Unlock();

BOOL Unlock(
    LONG lCount,
    LPLONG lPrevCount = NULL);
```

### <a name="parameters"></a>參數

*l. Count*<br/>
要釋放的訪問數。 必須大於 0。 如果指定量將導致物件的計數超過其最大值,則計數不會更改,並且函數將返回 FALSE。

*lPrev( A) Count*<br/>
指向變數以接收同步物件的上一個計數。 如果為 NULL,則不返回以前的計數。

### <a name="return-value"></a>傳回值

如果函數成功,則非零;否則 0。

### <a name="remarks"></a>備註

此函數由`CSingleLock`析構函數調用。

如果需要釋放信號量的多個訪問計數,請使用`Unlock`第 二種形式並指定要釋放的訪問數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CMultiLock 類別](../../mfc/reference/cmultilock-class.md)
