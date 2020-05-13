---
title: CSemaphore 類別
ms.date: 11/04/2016
f1_keywords:
- CSemaphore
- AFXMT/CSemaphore
- AFXMT/CSemaphore::CSemaphore
helpviewer_keywords:
- CSemaphore [MFC], CSemaphore
ms.assetid: 385fc7e4-8f86-4be2-85e1-d23b38c12f7f
ms.openlocfilehash: 26e1fd55d321b221f4732874d57d02a79c4c6398
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318505"
---
# <a name="csemaphore-class"></a>CSemaphore 類別

類`CSemaphore`的物件表示"信號量",即允許一個或多個進程中有限數量的線程訪問維護當前訪問指定資源的線程數的同步物件。

## <a name="syntax"></a>語法

```
class CSemaphore : public CSyncObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CSemaphore:CSemaphore](#csemaphore)|建構 `CSemaphore` 物件。|

## <a name="remarks"></a>備註

Semaphores 在控制對只能支援有限數量的用戶的共享資源的訪問方面非常有用。 `CSemaphore`對象的當前計數是允許的其他用戶數。 當計數達到零時,所有嘗試使用`CSemaphore`物件控制的資源的嘗試都將插入到系統佇列中,並等待超時或計數上升到 0 以上。 在構建`CSemaphore`對象期間,指定一次可以訪問受控資源的最大用戶數。

要使用`CSemaphore`物件`CSemaphore`, 在需要物件時建構該物件。 指定要等待的信號量的名稱,並且應用程式最初應擁有它。 然後,當構造函數返回時,可以訪問信號量。 呼叫[CSyncObject::存取](../../mfc/reference/csyncobject-class.md#unlock)受控資源後解鎖。

使用`CSemaphore`物件的替代方法是將類型`CSemaphore`的 變數作為數據成員添加到要控制的類中。 在建構受控物件期間,調用`CSemaphore`資料成員的構造函數,指定初始存取計數、最大存取計數、信號量的名稱(如果它將跨進程邊界使用)和所需的安全屬性。

要以這種方式存取`CSemaphore`受 物件控制的資源,請首先在資源的訪問成員函數中創建[CSingleLock](../../mfc/reference/csinglelock-class.md)類型或[CMultiLock](../../mfc/reference/cmultilock-class.md)類型的變數。 然後調用鎖對`Lock`象的成員函數(例如[,CSingleLock::鎖定](../../mfc/reference/csinglelock-class.md#lock))。 此時,線程將獲取對資源的訪問,等待資源被釋放並獲取訪問許可權,或者等待資源釋放和超時,無法訪問資源。 在任何情況下,您的資源都以線程安全的方式訪問。 要釋放資源,請使用鎖定對`Unlock`象的成員函數(例如[,CSingleLock::解鎖](../../mfc/reference/csinglelock-class.md#unlock)),或允許鎖定物件退出範圍。

或者,您可以創建獨立`CSemaphore`物件,並在嘗試訪問受控資源之前顯式訪問它。 此方法雖然對讀取原始程式碼的人更清晰,但更容易出錯。

有關如何使用`CSemaphore`物件的詳細資訊,請參閱"[多線程:如何使用同步類](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)「一文。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CSemaphore`

## <a name="requirements"></a>需求

**標題:** afxmt.h

## <a name="csemaphorecsemaphore"></a><a name="csemaphore"></a>CSemaphore:CSemaphore

建構命名或未命名`CSemaphore`的物件。

```
CSemaphore(
    LONG lInitialCount = 1,
    LONG lMaxCount = 1,
    LPCTSTR pstrName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttributes = NULL);
```

### <a name="parameters"></a>參數

*l 初始計數*<br/>
信號量的初始使用計數。 必須大於或等於 0,小於或等於*lMaxCount*。

*LMax( L) Count*<br/>
信號量的最大使用計數。 必須大於 0。

*pstrName*<br/>
信號量的名稱。 如果信號量將跨進程邊界訪問,則必須提供信號量。 如果`NULL`,物件將未命名。 如果名稱與現有信號量匹配,建構函數將生成一個新`CSemaphore`物件,引用該名稱的信號量。 如果名稱與現有不是信號量的同步物件匹配,則構造將失敗。

*lpsa 屬性*<br/>
信號量物件的安全屬性。 有關此結構的完整說明,請參閱 Windows SDK 中的[SECURITY_ATTRIBUTES。](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))

### <a name="remarks"></a>備註

要存取`CSemaphore`或釋放物件,請創建[CMultiLock](../../mfc/reference/cmultilock-class.md)或[CSingleLock](../../mfc/reference/csinglelock-class.md)物件,並調用其[鎖定](../../mfc/reference/csinglelock-class.md#lock)和[解鎖](../../mfc/reference/csinglelock-class.md#unlock)成員函數。

> [!IMPORTANT]
> 創建物件後`CSemaphore`,請使用[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)確保互斥體不存在。 如果互斥體確實意外存在,則可能表示惡意進程正在蹲下,並且可能打算惡意使用互斥體。 在這種情況下,建議的安全意識過程是關閉句柄並繼續,就像創建物件時失敗一樣。

## <a name="see-also"></a>另請參閱

[CSyncObject 類別](../../mfc/reference/csyncobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
