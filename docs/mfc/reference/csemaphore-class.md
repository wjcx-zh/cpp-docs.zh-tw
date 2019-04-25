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
ms.openlocfilehash: f2a05963f39393bcc73650beb44c5dbb8e5535ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324203"
---
# <a name="csemaphore-class"></a>CSemaphore 類別

類別的物件`CSemaphore`表示 「 信號 」 — 允許有限的數目的執行緒在存取持續的一或多個處理序的目前存取指定的資源的執行緒數目的同步處理物件。

## <a name="syntax"></a>語法

```
class CSemaphore : public CSyncObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CSemaphore::CSemaphore](#csemaphore)|建構 `CSemaphore` 物件。|

## <a name="remarks"></a>備註

號誌可用於控制只能支援有限的數目的使用者共用資源的存取權。 目前的計數`CSemaphore`物件是允許其他使用者的數目。 當計數到達零時，所有嘗試使用所控制的資源`CSemaphore`物件就會插入到系統佇列，並等到它們其中一個逾時時間或計數高於 0。 在建構期間指定的使用者可以一次存取受控制的資源數目上限`CSemaphore`物件。

若要使用`CSemaphore`物件，建構`CSemaphore`物件時需要它。 指定您想要等候，號誌的名稱和您的應用程式應該一開始所擁有。 然後，建構函式傳回時，您可以存取號誌。 呼叫[CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock)完成時存取控制的資源。

使用替代方法`CSemaphore`物件是新增類型的變數`CSemaphore`以您想要控制的類別資料成員。 在建構期間之受控制的物件，呼叫的建構函式`CSemaphore`指定初始的資料成員存取計數、 最高存取權的計數、 號誌 （如果它將會使用跨處理序界限） 的名稱，以及所需的安全性屬性。

存取控制的資源`CSemaphore`物件，如此一來，在第一次建立的其中一種類型的變數[CSingleLock](../../mfc/reference/csinglelock-class.md)或型別[CMultiLock](../../mfc/reference/cmultilock-class.md)在您的資源存取成員函式。 然後呼叫之鎖定物件的`Lock`成員函式 (例如[CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock))。 此時，您的執行緒會取得資源的存取權，等待資源釋出，並存取應用程式，或等候的資源釋出和逾時，無法取得資源的存取權。 在任何情況下，您的資源已存取具備執行緒安全的方式。 若要釋放資源，使用 鎖定物件的`Unlock`成員函式 (例如[CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock))，或允許超出範圍的鎖定物件。

或者，您可以建立`CSemaphore`物件獨立的並嘗試存取受控制的資源之前明確地存取它。 此方法，並清楚給其他人讀取您的原始程式碼，是更容易發生錯誤。

如需有關如何使用`CSemaphore`物件，請參閱文章[多執行緒：如何使用同步類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CSemaphore`

## <a name="requirements"></a>需求

**標頭：** afxmt.h

##  <a name="csemaphore"></a>  CSemaphore::CSemaphore

建構具名或未命名`CSemaphore`物件。

```
CSemaphore(
    LONG lInitialCount = 1,
    LONG lMaxCount = 1,
    LPCTSTR pstrName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttributes = NULL);
```

### <a name="parameters"></a>參數

*lInitialCount*<br/>
號誌初始的使用計數。 必須是大於或等於 0，且小於或等於*lMaxCount*。

*lMaxCount*<br/>
號誌的最大使用量計數。 必須大於 0。

*pstrName*<br/>
號誌的名稱。 如果將會跨處理序界限來存取號誌，必須提供。 如果`NULL`，物件會是未命名。 如果名稱符合現有的旗號，建構函式會建置新`CSemaphore`參考該名稱的號誌的物件。 如果名稱符合現有的同步處理物件，不是號誌，建構將會失敗。

*lpsaAttributes*<br/>
號誌物件的安全性屬性。 如需這個結構的完整說明，請參閱[SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) Windows SDK 中。

### <a name="remarks"></a>備註

存取或釋放`CSemaphore`物件，建立[CMultiLock](../../mfc/reference/cmultilock-class.md)或[CSingleLock](../../mfc/reference/csinglelock-class.md)物件並呼叫其[鎖定](../../mfc/reference/csinglelock-class.md#lock)並[解除鎖定](../../mfc/reference/csinglelock-class.md#unlock)成員函式。

> [!IMPORTANT]
>  在建立後`CSemaphore`物件，請使用[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)以確保該 mutex 不存在。 如果存在非預期地 mutex，可能表示處理序會佔用，而且可能會想要進行惡意使用 mutex。 在此情況下，建議的注重安全性的程序會關閉控制代碼，並繼續如同在建立物件時發生失敗。

## <a name="see-also"></a>另請參閱

[CSyncObject 類別](../../mfc/reference/csyncobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
