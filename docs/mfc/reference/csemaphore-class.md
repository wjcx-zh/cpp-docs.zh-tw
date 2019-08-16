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
ms.openlocfilehash: d5a0e4187107aaab7cedf4e7a0e2fc47b9f9f305
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502588"
---
# <a name="csemaphore-class"></a>CSemaphore 類別

類別`CSemaphore`的物件代表「信號」, 這是一個或多個處理常式中允許有限數目的執行緒來存取的同步處理物件, 它會維護目前存取指定資源的執行緒數目計數。

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

信號在控制共用資源的存取時很有用, 只支援數量有限的使用者。 `CSemaphore`物件的目前計數是允許的其他使用者數目。 當計數達到零時, 所有使用`CSemaphore`物件所控制之資源的嘗試都會插入到系統佇列中, 並等到其超時或計數高於0為止。 在`CSemaphore`物件的結構中, 會指定一次可存取受控制資源的使用者數目上限。

若要使用`CSemaphore`物件, 請在`CSemaphore`需要時建立物件。 指定您想要等候的信號名稱, 並讓您的應用程式一開始就擁有它。 接著, 您可以在此函式傳回時存取信號。 當您完成存取受控制的資源時, 請呼叫[CSyncObject:: Unlock](../../mfc/reference/csyncobject-class.md#unlock) 。

使用`CSemaphore`物件的替代方法是將類型`CSemaphore`的變數當做資料成員加入至您要控制的類別。 在結構控制物件的建立期間, 呼叫`CSemaphore`資料成員的函式, 以指定初始存取計數、最大存取計數、信號名稱 (如果它將跨進程界限使用), 以及所需的安全性屬性。

若要以這種`CSemaphore`方式存取物件所控制的資源, 請先在資源的存取成員函式中建立類型為[CSingleLock](../../mfc/reference/csinglelock-class.md)或類型為[CMultiLock](../../mfc/reference/cmultilock-class.md)的變數。 然後呼叫鎖定物件的`Lock`成員函式 (例如[CSingleLock:: lock](../../mfc/reference/csinglelock-class.md#lock))。 此時, 您的執行緒會取得資源的存取權、等待資源釋放並取得存取權, 或等待資源釋放並超時, 而無法取得資源的存取權。 在任何情況下, 您的資源都是以執行緒安全的方式存取。 若要釋放資源, 請使用鎖定物件的`Unlock`成員函式 (例如, [CSingleLock:: Unlock](../../mfc/reference/csinglelock-class.md#unlock)), 或允許鎖定物件超出範圍。

或者, 您可以建立獨立`CSemaphore`的物件, 並明確地存取它, 然後再嘗試存取受控制的資源。 這個方法雖然對閱讀原始程式碼的人更清楚, 但更容易發生錯誤。

如需如何使用`CSemaphore`物件的詳細資訊, 請參閱[多執行緒:如何使用同步處理類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CSemaphore`

## <a name="requirements"></a>需求

**標頭:** afxmt。h

##  <a name="csemaphore"></a>CSemaphore::CSemaphore

構造已命名或未`CSemaphore`命名的物件。

```
CSemaphore(
    LONG lInitialCount = 1,
    LONG lMaxCount = 1,
    LPCTSTR pstrName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttributes = NULL);
```

### <a name="parameters"></a>參數

*lInitialCount*<br/>
信號的初始使用計數。 必須大於或等於 0, 且小於或等於*lMaxCount*。

*lMaxCount*<br/>
信號的最大使用量計數。 必須大於 0。

*pstrName*<br/>
信號的名稱。 如果要跨進程界限存取信號, 就必須提供。 如果`NULL`為, 則物件將為未命名。 如果名稱符合現有的信號, 則此函式會建立`CSemaphore`參考該名稱之信號的新物件。 如果名稱符合不是信號的現有同步處理物件, 則結構將會失敗。

*lpsaAttributes*<br/>
信號物件的安全性屬性。 如需此結構的完整說明, 請參閱 Windows SDK 中的[security attributes 這個](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))。

### <a name="remarks"></a>備註

若要存取或釋放`CSemaphore`物件, 請建立[CMultiLock](../../mfc/reference/cmultilock-class.md)或[CSingleLock](../../mfc/reference/csinglelock-class.md)物件, 並呼叫其[Lock](../../mfc/reference/csinglelock-class.md#lock)和[Unlock](../../mfc/reference/csinglelock-class.md#unlock)成員函式。

> [!IMPORTANT]
>  建立`CSemaphore`物件之後, 請使用[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)來確保 mutex 不存在。 如果 mutex 意外存在, 可能表示有惡意的進程佔用, 而且可能會有意使用此 mutex。 在此情況下, 建議的安全性意識程式是關閉控制碼, 並繼續執行, 就像建立物件失敗一樣。

## <a name="see-also"></a>另請參閱

[CSyncObject 類別](../../mfc/reference/csyncobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
