---
title: CMutex 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMutex
- AFXMT/CMutex
- AFXMT/CMutex::CMutex
dev_langs:
- C++
helpviewer_keywords:
- CMutex [MFC], CMutex
ms.assetid: 6330c050-4f01-4195-a099-2029b92f8cf1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 23270275103faac3af48a3627a5f5833140645e2
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066734"
---
# <a name="cmutex-class"></a>CMutex 類別

代表 「 mutex 」 — 可讓一個執行緒互斥資源的存取權的同步處理物件。

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

可允許一次只有一個執行緒修改資料或其他一些受控制的資源時，Mutex 會很有用。 例如，將節點新增至連結的清單是應該只能由一個執行緒使用，一次的處理程序。 使用`CMutex`控制連結的清單中，只有一次一個執行緒可以存取清單的物件。

若要使用`CMutex`物件，建構`CMutex`物件時需要它。 指定您想要等候的 mutex 的名稱和您的應用程式應該一開始所擁有。 然後，建構函式傳回時，您可以存取 mutex。 呼叫[CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock)完成時存取控制的資源。

使用替代方法`CMutex`物件是新增類型的變數`CMutex`以您想要控制的類別資料成員。 在建構期間之受控制的物件，呼叫的建構函式`CMutex`資料成員指定是否 mutex 一開始擁有，mutex （如果它將會使用跨處理序界限）、 名稱和所需的安全性屬性。

存取控制的資源`CMutex`物件，如此一來，在第一次建立的其中一種類型的變數[CSingleLock](../../mfc/reference/csinglelock-class.md)或型別[CMultiLock](../../mfc/reference/cmultilock-class.md)在您的資源存取成員函式。 然後呼叫之鎖定物件的`Lock`成員函式 (例如[CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock))。 此時，您的執行緒會取得資源的存取權，等待資源釋出，並存取應用程式，或等候的資源釋出和逾時，無法取得資源的存取權。 在任何情況下，您的資源已存取具備執行緒安全的方式。 若要釋放資源，使用 鎖定物件的`Unlock`成員函式 (例如[CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock))，或允許超出範圍的鎖定物件。

如需有關使用`CMutex`物件，請參閱文章[多執行緒： 如何使用同步類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CMutex`

## <a name="requirements"></a>需求

**標頭：** afxmt.h

##  <a name="cmutex"></a>  CMutex::CMutex

建構具名或未命名`CMutex`物件。

```
CMutex(
    BOOL bInitiallyOwn = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>參數

*bInitiallyOwn*<br/>
指定如果執行緒建立`CMutex`物件一開始會有由 mutex 控制資源的存取權。

*lpszName*<br/>
`CMutex` 物件的名稱。 另一個具有相同名稱的 mutex 已存在，如果*lpszName*必須提供，如果該物件會使用跨處理序界限。 如果**NULL**，mutex 會是未命名。 如果名稱符合現有的 mutex，建構函式會建置新`CMutex`參考該名稱的 mutex 物件。 如果名稱符合現有的同步處理物件，都不是 mutex，建構將會失敗。

*lpsaAttribute*<br/>
Mutex 物件的安全性屬性。 如需這個結構的完整說明，請參閱[SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) Windows SDK 中。

### <a name="remarks"></a>備註

存取或釋放`CMutex`物件，建立[CMultiLock](../../mfc/reference/cmultilock-class.md)或[CSingleLock](../../mfc/reference/csinglelock-class.md)物件並呼叫其[鎖定](../../mfc/reference/csinglelock-class.md#lock)並[解除鎖定](../../mfc/reference/csinglelock-class.md#unlock)成員函式。 如果`CMutex`物件正在使用獨立的工作，請呼叫其`Unlock`釋放它的成員函式。

> [!IMPORTANT]
>  在建立後`CMutex`物件，請使用[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)以確保該 mutex 不存在。 如果存在非預期地 mutex，可能表示處理序會佔用，而且可能會想要進行惡意使用 mutex。 在此情況下，建議的注重安全性的程序會關閉控制代碼，並繼續如同在建立物件時發生失敗。

## <a name="see-also"></a>另請參閱

[CSyncObject 類別](../../mfc/reference/csyncobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)

