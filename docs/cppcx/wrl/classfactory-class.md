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
ms.openlocfilehash: bbf20e2269e6d62206e06e748174d7b88898cd68
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87198095"
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
預備介面。

*I1*<br/>
第一個介面。

*I2*<br/>
第二個介面。

## <a name="remarks"></a>備註

利用 `ClassFactory` 來提供使用者定義的 factory 執行。

下列程式設計模式示範如何使用[Implements](implements-structure.md)結構，在 Class Factory 上指定三個以上的介面。

`struct MyFactory : ClassFactory<Implements<I1, I2, I3>, I4, I5>`

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                        | 說明
------------------------------------------- | -----------
[ClassFactory：： ClassFactory](#classfactory) |

### <a name="public-methods"></a>公用方法

名稱                                            | 說明
----------------------------------------------- | ----------------------------------------------------------------------------------------------------------------
[ClassFactory：： AddRef](#addref)                 | 遞增目前物件的參考計數 `ClassFactory` 。
[ClassFactory：： LockServer](#lockserver)         | 遞增或遞減目前物件所追蹤的基礎物件數目 `ClassFactory` 。
[ClassFactory：： QueryInterface](#queryinterface) | 抓取參數所指定之介面的指標。
[ClassFactory：： Release](#release)               | 遞減目前物件的參考計數 `ClassFactory` 。

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

**標頭：** module. h

**命名空間：** Microsoft::WRL

## <a name="classfactoryaddref"></a><a name="addref"></a>ClassFactory：： AddRef

遞增目前物件的參考計數 `ClassFactory` 。

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>傳回值

若成功，則為 S_OK，否則會是 HRESULT 指出失敗。

## <a name="classfactoryclassfactory"></a><a name="classfactory"></a>ClassFactory：： ClassFactory

```cpp
WRL_NOTHROW ClassFactory();
```

## <a name="classfactorylockserver"></a><a name="lockserver"></a>ClassFactory：： LockServer

遞增或遞減目前物件所追蹤的基礎物件數目 `ClassFactory` 。

```cpp
STDMETHOD(
   LockServer
)(BOOL fLock);
```

### <a name="parameters"></a>參數

*fLock*<br/>
**`true`** 以遞增追蹤物件的數目。 **`false`** 以遞減已追蹤物件的數目。

### <a name="return-value"></a>傳回值

如果成功，則 S_OK;否則，E_FAIL。

### <a name="remarks"></a>備註

`ClassFactory`追蹤[模組](module-class.md)類別之基礎實例中的物件。

## <a name="classfactoryqueryinterface"></a><a name="queryinterface"></a>ClassFactory：： QueryInterface

抓取參數所指定之介面的指標。

```cpp
STDMETHOD(
   QueryInterface
)(REFIID riid, _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>參數

*riid*<br/>
介面識別碼。

*ppvObject*<br/>
當此作業完成時，為參數*riid*所指定之介面的指標。

### <a name="return-value"></a>傳回值

若成功，則為 S_OK，否則會是 HRESULT 指出失敗。

## <a name="classfactoryrelease"></a><a name="release"></a>ClassFactory：： Release

遞減目前物件的參考計數 `ClassFactory` 。

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>傳回值

若成功，則為 S_OK，否則會是 HRESULT 指出失敗。
