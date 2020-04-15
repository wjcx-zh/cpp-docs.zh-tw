---
title: ClassFactory 類別
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory
- module/Microsoft::WRL::ClassFactory::AddRef
- module/Microsoft::WRL::ClassFactory::ClassFactory
- module/Microsoft::WRL::ClassFactory::LockServer
- module/Microsoft::WRL::ClassFactory::QueryInterface
- module/Microsoft::WRL::ClassFactory::Release
helpviewer_keywords:
- Microsoft::WRL::ClassFactory class
- Microsoft::WRL::ClassFactory::AddRef method
- Microsoft::WRL::ClassFactory::ClassFactory, constructor
- Microsoft::WRL::ClassFactory::LockServer method
- Microsoft::WRL::ClassFactory::QueryInterface method
- Microsoft::WRL::ClassFactory::Release method
ms.assetid: f13e6bce-722b-4f18-b7cf-3ffa6345c1db
ms.openlocfilehash: 3b738cc8f439e6653162ab99b0a26e87aa8fee36
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372671"
---
# <a name="classfactory-class"></a>ClassFactory 類別

實作 `IClassFactory` 介面的基本功能。

## <a name="syntax"></a>語法

```cpp
template <
    typename I0 = Details::Nil,
    typename I1 = Details::Nil,
    typename I2 = Details::Nil
>
class ClassFactory :
    public Details::RuntimeClass<
        typename Details::InterfaceListHelper<
            IClassFactory,
            I0,
            I1,
            I2,
            Details::Nil
        >::TypeT,
        RuntimeClassFlags<ClassicCom | InhibitWeakReference>,
        false
    >;
```

### <a name="parameters"></a>參數

*I0*<br/>
第零個介面。

*I1*<br/>
第一個介面。

*I2*<br/>
第二個介面。

## <a name="remarks"></a>備註

利用`ClassFactory`來提供使用者定義的工廠實現。

以下程式設計模式展示如何使用[實現器](implements-structure.md)結構在類工廠上指定三個多個介面。

`struct MyFactory : ClassFactory<Implements<I1, I2, I3>, I4, I5>`

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                        | 描述
------------------------------------------- | -----------
[類工廠::類工廠](#classfactory) |

### <a name="public-methods"></a>公用方法

名稱                                            | 描述
----------------------------------------------- | ----------------------------------------------------------------------------------------------------------------
[類別工廠::新增參考](#addref)                 | 增加當前`ClassFactory`物件的引用計數。
[類別工廠::鎖伺服器](#lockserver)         | 增加或遞減當前`ClassFactory`物件跟蹤的基礎物件數。
[類工廠::查詢介面](#queryinterface) | 檢索指向參數指定的介面的指標。
[類工廠::發佈](#release)               | 取消當前`ClassFactory`物件的引用計數。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`I0`

`ChainInterfaces`

`I0`

`RuntimeClassBase`

`ImplementsHelper`

`DontUseNewUseMake`

`RuntimeClassFlags`

`RuntimeClassBaseT`

`RuntimeClass`

`ClassFactory`

## <a name="requirements"></a>需求

**標題:** 模組.h

**命名空間：** Microsoft::WRL

## <a name="classfactoryaddref"></a><a name="addref"></a>類別工廠::新增參考

增加當前`ClassFactory`物件的引用計數。

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>傳回值

若成功，則為 S_OK，否則會是 HRESULT 指出失敗。

## <a name="classfactoryclassfactory"></a><a name="classfactory"></a>類工廠::類工廠

```cpp
WRL_NOTHROW ClassFactory();
```

## <a name="classfactorylockserver"></a><a name="lockserver"></a>類別工廠::鎖伺服器

增加或遞減當前`ClassFactory`物件跟蹤的基礎物件數。

```cpp
STDMETHOD(
   LockServer
)(BOOL fLock);
```

### <a name="parameters"></a>參數

*羊群*<br/>
**true**以增加追蹤物件的數量。 **false**以減少被跟蹤物件的數量。

### <a name="return-value"></a>傳回值

S_OK如果成功;否則,E_FAIL。

### <a name="remarks"></a>備註

`ClassFactory`跟蹤[模組](module-class.md)類的基礎實例中的物件。

## <a name="classfactoryqueryinterface"></a><a name="queryinterface"></a>類工廠::查詢介面

檢索指向參數指定的介面的指標。

```cpp
STDMETHOD(
   QueryInterface
)(REFIID riid, _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>參數

*riid*<br/>
介面識別碼。

*ppvObject*<br/>
此操作完成後,指向參數*riid*指定的介面的指標。

### <a name="return-value"></a>傳回值

若成功，則為 S_OK，否則會是 HRESULT 指出失敗。

## <a name="classfactoryrelease"></a><a name="release"></a>類工廠::發佈

取消當前`ClassFactory`物件的引用計數。

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>傳回值

若成功，則為 S_OK，否則會是 HRESULT 指出失敗。
