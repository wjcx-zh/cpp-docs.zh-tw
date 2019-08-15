---
title: CMutex 類別
ms.date: 11/04/2016
f1_keywords:
- CMutex
- AFXMT/CMutex
- AFXMT/CMutex::CMutex
helpviewer_keywords:
- CMutex [MFC], CMutex
ms.assetid: 6330c050-4f01-4195-a099-2029b92f8cf1
ms.openlocfilehash: 65f7f4db9489de1c9a380d760ed5cab41bfdc2ec
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504525"
---
# <a name="cmutex-class"></a>CMutex 類別

代表「mutex」—這是一個同步處理物件, 可讓一個執行緒對資源進行互斥的存取。

## <a name="syntax"></a>語法

```
class CMutex : public CSyncObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMutex::CMutex](#cmutex)|建構 `CMutex` 物件。|

## <a name="remarks"></a>備註

當一次只能有一個執行緒可修改資料或一些其他受控制的資源時, mutex 就很有用。 例如, 將節點加入至連結清單, 是一次只能由一個執行緒允許的進程。 藉由使用`CMutex`物件來控制連結清單, 一次只能有一個執行緒可以取得清單的存取權。

若要使用`CMutex`物件, 請在`CMutex`需要時建立物件。 指定您想要等候的 mutex 名稱, 並讓您的應用程式一開始就擁有它。 然後, 當此函式傳回時, 您就可以存取 mutex。 當您完成存取受控制的資源時, 請呼叫[CSyncObject:: Unlock](../../mfc/reference/csyncobject-class.md#unlock) 。

使用`CMutex`物件的替代方法是將類型`CMutex`的變數當做資料成員加入至您要控制的類別。 在結構控制物件的建立期間, 呼叫`CMutex`資料成員的函式, 以指定是否一開始擁有 mutex、mutex 的名稱 (如果它將跨進程界限使用), 以及所需的安全性屬性。

若要以這種`CMutex`方式存取物件所控制的資源, 請先在資源的存取成員函式中建立類型為[CSingleLock](../../mfc/reference/csinglelock-class.md)或類型為[CMultiLock](../../mfc/reference/cmultilock-class.md)的變數。 然後呼叫鎖定物件的`Lock`成員函式 (例如[CSingleLock:: lock](../../mfc/reference/csinglelock-class.md#lock))。 此時, 您的執行緒會取得資源的存取權、等待資源釋放並取得存取權, 或等待資源釋放並超時, 而無法取得資源的存取權。 在任何情況下, 您的資源都是以執行緒安全的方式存取。 若要釋放資源, 請使用鎖定物件的`Unlock`成員函式 (例如, [CSingleLock:: Unlock](../../mfc/reference/csinglelock-class.md#unlock)), 或允許鎖定物件超出範圍。

如需使用`CMutex`物件的詳細資訊, 請參閱[多執行緒:如何使用同步處理類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CMutex`

## <a name="requirements"></a>需求

**標頭:** afxmt。h

##  <a name="cmutex"></a>CMutex::CMutex

構造已命名或未`CMutex`命名的物件。

```
CMutex(
    BOOL bInitiallyOwn = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>參數

*bInitiallyOwn*<br/>
指定建立`CMutex`物件的執行緒一開始是否具有 mutex 所控制之資源的存取權。

*lpszName*<br/>
`CMutex` 物件的名稱。 如果有其他同名的 mutex 存在, 則如果物件將跨進程界限使用, 則必須提供*lpszName* 。 如果是**Null**, 則 mutex 將為未命名。 如果名稱符合現有的 mutex, 則此函式會建立`CMutex`新的物件, 參考該名稱的 mutex。 如果名稱符合不是 mutex 的現有同步處理物件, 則結構將會失敗。

*lpsaAttribute*<br/>
Mutex 物件的安全性屬性。 如需此結構的完整說明, 請參閱 Windows SDK 中的[security attributes 這個](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))。

### <a name="remarks"></a>備註

若要存取或釋放`CMutex`物件, 請建立[CMultiLock](../../mfc/reference/cmultilock-class.md)或[CSingleLock](../../mfc/reference/csinglelock-class.md)物件, 並呼叫其[Lock](../../mfc/reference/csinglelock-class.md#lock)和[Unlock](../../mfc/reference/csinglelock-class.md#unlock)成員函式。 如果物件`CMutex`是獨立使用的, 請呼叫其`Unlock`成員函式來釋放它。

> [!IMPORTANT]
>  建立`CMutex`物件之後, 請使用[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)來確保 mutex 不存在。 如果 mutex 意外存在, 可能表示有惡意的進程佔用, 而且可能會有意使用此 mutex。 在此情況下, 建議的安全性意識程式是關閉控制碼, 並繼續執行, 就像建立物件失敗一樣。

## <a name="see-also"></a>另請參閱

[CSyncObject 類別](../../mfc/reference/csyncobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
