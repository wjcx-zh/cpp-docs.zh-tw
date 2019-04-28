---
title: ActivationFactory 類別
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory
- module/Microsoft::WRL::ActivationFactory::ActivationFactory
- module/Microsoft::WRL::ActivationFactory::AddRef
- module/Microsoft::WRL::ActivationFactory::GetIids
- module/Microsoft::WRL::ActivationFactory::GetRuntimeClassName
- module/Microsoft::WRL::ActivationFactory::GetTrustLevel
- module/Microsoft::WRL::ActivationFactory::QueryInterface
- module/Microsoft::WRL::ActivationFactory::Release
helpviewer_keywords:
- Microsoft::WRL::ActivationFactory class
- Microsoft::WRL::ActivationFactory::ActivationFactory, constructor
- Microsoft::WRL::ActivationFactory::AddRef method
- Microsoft::WRL::ActivationFactory::GetIids method
- Microsoft::WRL::ActivationFactory::GetRuntimeClassName method
- Microsoft::WRL::ActivationFactory::GetTrustLevel method
- Microsoft::WRL::ActivationFactory::QueryInterface method
- Microsoft::WRL::ActivationFactory::Release method
ms.assetid: 5faddf1f-43b6-4f8a-97de-8c9d3ae1e1ff
ms.openlocfilehash: 8e5132f4a8711f6420cd9b52751550a96d10d8fc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303886"
---
# <a name="activationfactory-class"></a>ActivationFactory 類別

讓 Windows 執行階段啟動一或多個類別。

## <a name="syntax"></a>語法

```cpp
template <
    typename I0 = Details::Nil,
    typename I1 = Details::Nil,
    typename I2 = Details::Nil
>
class ActivationFactory :
    public Details::RuntimeClass<
        typename Details::InterfaceListHelper<
            IActivationFactory,
            I0,
            I1,
            I2,
            Details::Nil
        >::TypeT,
        RuntimeClassFlags<WinRt | InhibitWeakReference>,
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

`ActivationFactory` 提供註冊方法和基本功能`IActivationFactory`介面。 `ActivationFactory` 也可讓您提供的自訂處理站實作。

下列程式碼片段以符號形式會說明如何使用 ActivationFactory。

[!code-cpp[wrl-microsoft__wrl__activationfactory#1](../codesnippet/CPP/activationfactory-class_1.cpp)]

下列程式碼片段示範如何使用[實作](implements-structure.md)結構，以指定超過三個介面 Id。

`struct MyFactory : ActivationFactory<Implements<I1, I2, I3>, I4, I5>;`

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                                       | 描述
---------------------------------------------------------- | ------------------------------------------
[ActivationFactory::ActivationFactory](#activationfactory) | 初始化`ActivationFactory`類別。

### <a name="public-methods"></a>公用方法

名稱                                                           | 描述
-------------------------------------------------------------- | --------------------------------------------------------------------------------------------
[ActivationFactory::AddRef](#addref)                           | 目前的參考計數遞增`ActivationFactory`物件。
[ActivationFactory::GetIids](#getiids)                         | 擷取實作的介面識別碼的陣列。
[ActivationFactory::GetRuntimeClassName](#getruntimeclassname) | 取得物件的執行階段類別名稱目前`ActivationFactory`具現化。
[ActivationFactory::GetTrustLevel](#gettrustlevel)             | 取得物件的信任層級，目前`ActivationFactory`具現化。
[ActivationFactory::QueryInterface](#queryinterface)           | 擷取指定之介面的指標。
[ActivationFactory::Release](#release)                         | 遞減參考計數目前的`ActivationFactory`物件。

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

`ActivationFactory`

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft:: wrl

## <a name="activationfactory"></a>ActivationFactory::ActivationFactory

初始化`ActivationFactory`類別。

```cpp
ActivationFactory();
```

## <a name="addref"></a>ActivationFactory::AddRef

目前的參考計數遞增`ActivationFactory`物件。

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>傳回值

若成功，則為 S_OK，否則會是 HRESULT 指出失敗。

## <a name="getiids"></a>ActivationFactory::GetIids

擷取實作的介面識別碼的陣列。

```cpp
STDMETHOD(
   GetIids
)(_Out_ ULONG *iidCount, _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>參數

*iidCount*<br/>
這項作業完成時中的介面識別碼的數目*iid*陣列。

*iids*<br/>
這項作業完成時，陣列就會實作的介面識別碼。

### <a name="return-value"></a>傳回值

若成功，則為 S_OK，否則會是 HRESULT 指出失敗。 E_OUTOFMEMORY 是可能的失敗 HRESULT。

## <a name="getruntimeclassname"></a>ActivationFactory::GetRuntimeClassName

取得物件的執行階段類別名稱目前`ActivationFactory`具現化。

```cpp
STDMETHOD(
   GetRuntimeClassName
)(_Out_ HSTRING* runtimeName);
```

### <a name="parameters"></a>參數

*runtimeName*<br/>
這項作業完成時，包含物件的執行階段類別名稱的字串的控制代碼的目前`ActivationFactory`具現化。

### <a name="return-value"></a>傳回值

若成功，則為 S_OK，否則會是 HRESULT 指出失敗。

## <a name="gettrustlevel"></a>ActivationFactory::GetTrustLevel

取得物件的信任層級，目前`ActivationFactory`具現化。

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

### <a name="parameters"></a>參數

*trustLvl*<br/>
這項作業完成時，執行階段的信任層級類別`ActivationFactory`具現化。

### <a name="return-value"></a>傳回值

如果成功則為 S_OK否則，會發出判斷提示錯誤以及*trustLvl*設定為`FullTrust`。

## <a name="queryinterface"></a>ActivationFactory::QueryInterface

擷取指定之介面的指標。

```cpp
STDMETHOD(
   QueryInterface
)(REFIID riid, _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>參數

*riid*<br/>
介面識別碼。

*ppvObject*<br/>
這項作業完成後，參數所指定之介面指標*riid*。

### <a name="return-value"></a>傳回值

若成功，則為 S_OK，否則會是 HRESULT 指出失敗。

## <a name="release"></a>ActivationFactory::Release

遞減參考計數目前的`ActivationFactory`物件。

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>傳回值

若成功，則為 S_OK，否則會是 HRESULT 指出失敗。
