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
ms.openlocfilehash: ccc1c43e8c68053a773883c25704cdea086bd0b1
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58784004"
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
第零個介面中。

*I1*<br/>
第一個介面。

*I2*<br/>
第二個介面中。

## <a name="remarks"></a>備註

利用`ClassFactory`以提供使用者定義的 factory 實作。

下列的程式設計模式將示範如何使用[實作](implements-structure.md)結構，以指定三個以上的介面上的 class factory。

`struct MyFactory : ClassFactory<Implements<I1, I2, I3>, I4, I5>`

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                        | 描述
------------------------------------------- | -----------
[ClassFactory::ClassFactory](#classfactory) |

### <a name="public-methods"></a>公用方法

名稱                                            | 描述
----------------------------------------------- | ----------------------------------------------------------------------------------------------------------------
[ClassFactory::AddRef](#addref)                 | 遞增參考計數目前`ClassFactory`物件。
[ClassFactory::LockServer](#lockserver)         | 遞增或遞減目前所追蹤物件數量基礎`ClassFactory`物件。
[ClassFactory::QueryInterface](#queryinterface) | 擷取指定參數的介面指標。
[ClassFactory::Release](#release)               | 遞減參考計數目前`ClassFactory`物件。

## <a name="inheritance-hierarchy"></a>繼承階層

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

**標頭：** module.h

**命名空間：** Microsoft:: wrl

## <a name="addref"></a>ClassFactory::AddRef

遞增參考計數目前`ClassFactory`物件。

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>傳回值

若成功，則為 S_OK，否則會是 HRESULT 指出失敗。

## <a name="classfactory"></a>ClassFactory::ClassFactory

```cpp
WRL_NOTHROW ClassFactory();
```

## <a name="lockserver"></a>ClassFactory::LockServer

遞增或遞減目前所追蹤物件數量基礎`ClassFactory`物件。

```cpp
STDMETHOD(
   LockServer
)(BOOL fLock);
```

### <a name="parameters"></a>參數

*fLock*<br/>
**true**遞增追蹤的物件數目。 **false**來減少追蹤的物件數目。

### <a name="return-value"></a>傳回值

如果成功則為 S_OK否則，E_FAIL。

### <a name="remarks"></a>備註

`ClassFactory` 追蹤的基礎執行個體中的物件[模組](module-class.md)類別。

## <a name="queryinterface"></a>ClassFactory::QueryInterface

擷取指定參數的介面指標。

```cpp
STDMETHOD(
   QueryInterface
)(REFIID riid, _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>參數

*riid*<br/>
介面識別碼。

*ppvObject*<br/>
這項作業完成時，參數所指定之介面指標*riid*。

### <a name="return-value"></a>傳回值

若成功，則為 S_OK，否則會是 HRESULT 指出失敗。

## <a name="release"></a>ClassFactory::Release

遞減參考計數目前`ClassFactory`物件。

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>傳回值

若成功，則為 S_OK，否則會是 HRESULT 指出失敗。
