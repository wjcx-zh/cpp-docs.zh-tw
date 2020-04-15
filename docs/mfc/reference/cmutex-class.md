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
ms.openlocfilehash: 2d6f637ab4828b3e70df205ebf359ae45a940d60
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363288"
---
# <a name="cmutex-class"></a>CMutex 類別

表示"互斥"-允許一個線程相互獨佔的資源的同步物件。

## <a name="syntax"></a>語法

```
class CMutex : public CSyncObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMutex:CMutex](#cmutex)|建構 `CMutex` 物件。|

## <a name="remarks"></a>備註

當一次只允許一個線程修改數據或其他受控資源時,Mutexs 非常有用。 例如,將節點添加到連結清單是一個一次只能由一個線程允許的過程。 通過使用`CMutex`物件來控制連結清單,一次只能訪問一個線程。

要使用`CMutex`物件`CMutex`, 在需要物件時建構該物件。 指定要等待的互斥體的名稱,並且應用程式最初應擁有它。 然後,當構造函數返回時,可以訪問互斥體。 呼叫[CSyncObject::存取](../../mfc/reference/csyncobject-class.md#unlock)受控資源後解鎖。

使用`CMutex`物件的替代方法是將類型`CMutex`的 變數作為數據成員添加到要控制的類中。 在建構受控物件期間,調用`CMutex`資料成員的構造函數,指定互斥體最初是否擁有、互斥體的名稱(如果它將跨進程邊界使用)以及所需的安全屬性。

要以這種方式存取`CMutex`受 物件控制的資源,請首先在資源的訪問成員函數中創建[CSingleLock](../../mfc/reference/csinglelock-class.md)類型或[CMultiLock](../../mfc/reference/cmultilock-class.md)類型的變數。 然後調用鎖對`Lock`象的成員函數(例如[,CSingleLock::鎖定](../../mfc/reference/csinglelock-class.md#lock))。 此時,線程將獲取對資源的訪問,等待資源被釋放並獲取訪問許可權,或者等待資源釋放和超時,無法訪問資源。 在任何情況下,您的資源都以線程安全的方式訪問。 要釋放資源,請使用鎖定對`Unlock`象的成員函數(例如[,CSingleLock::解鎖](../../mfc/reference/csinglelock-class.md#unlock)),或允許鎖定物件退出範圍。

有關使用`CMutex`物件的詳細資訊,請參閱"[多線程:如何使用同步類](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)「一文。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CMutex`

## <a name="requirements"></a>需求

**標題:** afxmt.h

## <a name="cmutexcmutex"></a><a name="cmutex"></a>CMutex:CMutex

建構命名或未命名`CMutex`的物件。

```
CMutex(
    BOOL bInitiallyOwn = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>參數

*b 初始擁有*<br/>
指定創建`CMutex`物件的線程最初是否有權訪問由互斥體控制的資源。

*lpsz名稱*<br/>
`CMutex` 物件的名稱。 如果存在另一個同名的互斥體,則必須提供*lpszName,* 如果物件將跨進程邊界使用。 如果**NULL**,則互斥體將未命名。 如果名稱與現有互斥體匹配,則構造函數將生成一`CMutex`個新物件,該物件引用該名稱的互斥體。 如果名稱與現有不是互斥體的同步物件匹配,則構造將失敗。

*lpsa 屬性*<br/>
互斥體的安全屬性。 有關此結構的完整說明,請參閱 Windows SDK 中的[SECURITY_ATTRIBUTES。](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))

### <a name="remarks"></a>備註

要存取`CMutex`或釋放物件,請創建[CMultiLock](../../mfc/reference/cmultilock-class.md)或[CSingleLock](../../mfc/reference/csinglelock-class.md)物件,並調用其[鎖定](../../mfc/reference/csinglelock-class.md#lock)和[解鎖](../../mfc/reference/csinglelock-class.md#unlock)成員函數。 如果對`CMutex`像是獨立使用的,請調用其成員`Unlock`函數以釋放它。

> [!IMPORTANT]
> 創建物件後`CMutex`,請使用[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)確保互斥體不存在。 如果互斥體確實意外存在,則可能表示惡意進程正在蹲下,並且可能打算惡意使用互斥體。 在這種情況下,建議的安全意識過程是關閉句柄並繼續,就像創建物件時失敗一樣。

## <a name="see-also"></a>另請參閱

[CSyncObject 類別](../../mfc/reference/csyncobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
