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
ms.openlocfilehash: 009a17342cb92025d67bf2fe0df1b9d5c7c0c6f0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373951"
---
# <a name="cevent-class"></a>CEvent 類別

表示事件,它是一個同步物件,使一個線程能夠通知另一個線程發生了事件。

## <a name="syntax"></a>語法

```
class CEvent : public CSyncObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[活動::CEvent](#cevent)|建構 `CEvent` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[活動::Pulse事件](#pulseevent)|將事件設置為可用(信號),釋放等待線程,並將事件設置為不可用(非信號)。|
|[活動::重置事件](#resetevent)|將事件設置為不可用(非信號)。|
|[活動::設定事件](#setevent)|將事件設置為可用(信號),並釋放任何等待線程。|
|[活動::解鎖](#unlock)|釋放事件物件。|

## <a name="remarks"></a>備註

當線程必須知道何時執行其任務時,事件很有用。 例如,當有新數據可用時,必須通知將數據複製到數據存檔的線程。 通過使用`CEvent`物件在新數據可用時通知複製線程,線程可以儘快執行其任務。

`CEvent`物件有兩種類型:手動和自動。

釋放至少`CEvent`一個線程后,自動物件將自動返回到非信號(不可用)狀態。 預設情況下,`CEvent`除非在建構期間`TRUE`傳遞*bManualReset*參數,否則物件是自動的。

手動`CEvent`物件將保持[SetEvent](#setevent)或[ResetEvent](#resetevent)設置的狀態,直到調用其他函數。 要建立手動`CEvent`物件,請`TRUE``bManualReset`在建構期間傳遞參數。

要使用`CEvent`物件`CEvent`, 在需要物件時建構該物件。 指定要等待的事件的名稱,並指定應用程式最初應擁有它。 然後,當構造函數返回時,可以訪問該事件。 呼叫[SetEvent](#setevent)以發出事件物件信號(使事件物件可用),然後在訪問受控資源後呼叫[「解鎖](#unlock)」。

使用`CEvent`物件的替代方法是將類型`CEvent`的 變數作為數據成員添加到要控制的類中。 在建構受控物件期間,調用`CEvent`資料成員的構造函數並指定事件最初是否發出信號,並指定所需的事件物件類型、事件的名稱(如果它將跨進程邊界使用)以及所需的任何安全屬性。

要以這種方式存`CEvent`取 由物件控制的資源,請首先在資源的存取方法中創建[CSingleLock](../../mfc/reference/csinglelock-class.md)類型的變數或[CMultiLock](../../mfc/reference/cmultilock-class.md)類型的變數。 然後調用鎖`Lock`物件的方法(例如[,CMultiLock::鎖定](../../mfc/reference/cmultilock-class.md#lock))。 此時,線程將獲取對資源的訪問,等待資源被釋放並獲取訪問許可權,或者等待資源釋放、超時,並且無法訪問資源。 在任何情況下,您的資源都以線程安全的方式訪問。 要釋放資源,請調用`SetEvent`事件物件信號,然後使用鎖定`Unlock`物件 的方法(例如[,CMultiLock::解鎖](../../mfc/reference/cmultilock-class.md#unlock)),或讓鎖定物件退出範圍。

有關如何使用`CEvent`物件的詳細資訊,請參閱[多線程:如何使用同步類](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。

## <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#45](../../mfc/codesnippet/cpp/cevent-class_1.cpp)]

[!code-cpp[NVC_MFC_Utilities#46](../../mfc/codesnippet/cpp/cevent-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CEvent`

## <a name="requirements"></a>需求

**標題:** afxmt.h

## <a name="ceventcevent"></a><a name="cevent"></a>活動::CEvent

建構命名或未命名`CEvent`的物件。

```
CEvent(
    BOOL bInitiallyOwn = FALSE,
    BOOL bManualReset = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>參數

*b 初始擁有*<br/>
如果為 TRUE,則`CMultilock``CSingleLock`啟用 或物件的線程。 否則,所有想要訪問資源的線程都必須等待。

*b 手動重置*<br/>
如果 TRUE,則指定事件對像是手動事件,否則事件物件是自動事件。

*lpsz名稱*<br/>
`CEvent` 物件的名稱。 如果要跨進程邊界使用該物件,則必須提供該物件。 如果名稱與現有事件匹配,則建構函數將生成一個新`CEvent`物件,該物件引用該名稱的事件。 如果名稱與現有不是事件的同步物件匹配,則構造將失敗。 如果為 NULL,則名稱將為空。

*lpsa 屬性*<br/>
事件物件的安全屬性。 有關此結構的完整說明,請參閱 Windows SDK 中的[SECURITY_ATTRIBUTES。](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))

### <a name="remarks"></a>備註

要存取`CEvent`或釋放物件,請創建[CMultiLock](../../mfc/reference/cmultilock-class.md)或[CSingleLock](../../mfc/reference/csinglelock-class.md)物件,並調用其[鎖定](../../mfc/reference/csinglelock-class.md#lock)和[解鎖](../../mfc/reference/csinglelock-class.md#unlock)成員函數。

要將`CEvent`物件的狀態更改為訊號(線程不必等待),請呼叫[SetEvent](#setevent)或[PulseEvent](#pulseevent)。 要將`CEvent`物件的狀態設定為非信號狀態(線程必須等待),請呼叫[ResetEvent](#resetevent)。

> [!IMPORTANT]
> 創建物件後`CEvent`,請使用[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)確保互斥體不存在。 如果互斥體確實意外存在,則可能表示惡意進程正在蹲下,並且可能打算惡意使用互斥體。 在這種情況下,建議的安全意識過程是關閉句柄並繼續,就像創建物件時失敗一樣。

## <a name="ceventpulseevent"></a><a name="pulseevent"></a>活動::Pulse事件

將事件的狀態設置為信號(可用),釋放任何等待的線程,並自動將其重置為非信號(不可用)。

```
BOOL PulseEvent();
```

### <a name="return-value"></a>傳回值

如果函數成功,則非零;否則 0。

### <a name="remarks"></a>備註

如果事件是手動的,則釋放所有等待線程,將事件設置為非信號,然後`PulseEvent`返回。 如果事件是自動的,則釋放單個線程,將事件設置為非信號,然後`PulseEvent`返回。

如果沒有線程等待,或者無法立即釋放線程,則`PulseEvent`將事件的狀態設置為非信號狀態並返回。

`PulseEvent`使用基礎 Win32`PulseEvent`函數,可以通過內核模式非同步過程調用暫時從等待狀態中刪除該函數。 因此,`PulseEvent`不可靠,不應由新應用程式使用。 有關詳細資訊,請參閱[PulseEvent 函數](/windows/win32/api/winbase/nf-winbase-pulseevent)。

## <a name="ceventresetevent"></a><a name="resetevent"></a>活動::重置事件

將事件的狀態設置為非信號狀態,直到[SetEvent](#setevent)成員函數顯式設置為發出信號。

```
BOOL ResetEvent();
```

### <a name="return-value"></a>傳回值

如果函數成功,則非零;否則 0。

### <a name="remarks"></a>備註

這將導致希望訪問此事件的所有線程等待。

自動事件不使用此成員函數。

## <a name="ceventsetevent"></a><a name="setevent"></a>活動::設定事件

將事件的狀態設置為信號,釋放任何等待的線程。

```
BOOL SetEvent();
```

### <a name="return-value"></a>傳回值

如果函數成功,則非零,否則為 0。

### <a name="remarks"></a>備註

如果事件是手動的,則事件將保持信號狀態,直到調用[ResetEvent。](#resetevent) 在這種情況下,可以釋放多個線程。 如果事件是自動的,則事件將保持信號狀態,直到釋放單個線程。 然後,系統會將事件的狀態設置為非信號狀態。 如果沒有線程等待,則狀態將保持信號狀態,直到釋放一個線程。

## <a name="ceventunlock"></a><a name="unlock"></a>活動::解鎖

釋放事件物件。

```
BOOL Unlock();
```

### <a name="return-value"></a>傳回值

如果線程擁有事件物件且事件是自動事件,則非零;否則 0。

### <a name="remarks"></a>備註

如果線程的鎖物件要重用,則此成員函數由當前擁有自動事件的線程調用,以便在它們完成後釋放它。 如果不重用鎖對象,鎖定物件的析構函數將調用此函數。

## <a name="see-also"></a>另請參閱

[CSyncObject 類別](../../mfc/reference/csyncobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
