---
title: ChainInterfaces 結構
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces
- implements/Microsoft::WRL::ChainInterfaces::CanCastTo
- implements/Microsoft::WRL::ChainInterfaces::CastToUnknown
- implements/Microsoft::WRL::ChainInterfaces::FillArrayWithIid
- implements/Microsoft::WRL::ChainInterfaces::IidCount
- implements/Microsoft::WRL::ChainInterfaces::Verify
helpviewer_keywords:
- Microsoft::WRL::ChainInterfaces structure
- Microsoft::WRL::ChainInterfaces::CanCastTo method
- Microsoft::WRL::ChainInterfaces::CastToUnknown method
- Microsoft::WRL::ChainInterfaces::FillArrayWithIid method
- Microsoft::WRL::ChainInterfaces::IidCount constant
- Microsoft::WRL::ChainInterfaces::Verify method
ms.assetid: d7415b59-5468-4bef-a3fd-8d82b12f0e9c
ms.openlocfilehash: 48b663f2042ff0095466d83fe872ef6196112f76
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211537"
---
# <a name="chaininterfaces-structure"></a>ChainInterfaces 結構

指定可以套用至一組介面 ID 的驗證和初始化函式。

## <a name="syntax"></a>語法

```cpp
template <
    typename I0,
    typename I1,
    typename I2 = Details::Nil,
    typename I3 = Details::Nil,
    typename I4 = Details::Nil,
    typename I5 = Details::Nil,
    typename I6 = Details::Nil,
    typename I7 = Details::Nil,
    typename I8 = Details::Nil,
    typename I9 = Details::Nil
>
struct ChainInterfaces : I0;

template <
    typename DerivedType,
    typename BaseType,
    bool hasImplements,
    typename I1,
    typename I2,
    typename I3,
    typename I4,
    typename I5,
    typename I6,
    typename I7,
    typename I8,
    typename I9
>
struct ChainInterfaces<
    MixIn<
        DerivedType,
        BaseType,
        hasImplements
    >, I1, I2, I3, I4, I5, I6, I7, I8, I9
>;
```

### <a name="parameters"></a>參數

*I0*<br/>
具備介面識別碼0。

*I1*<br/>
具備介面識別碼1。

*I2*<br/>
選擇性介面識別碼2。

*I3*<br/>
選擇性介面識別碼3。

*I4*<br/>
選擇性介面識別碼4。

*I5*<br/>
選擇性介面識別碼5。

*I6*<br/>
選擇性介面識別碼6。

*I7*<br/>
選擇性介面識別碼7。

*I8*<br/>
選擇性介面識別碼8。

*I9-7xxx*<br/>
選擇性介面識別碼9。

*DerivedType*<br/>
衍生類型。

*BaseType*<br/>
衍生型別的基底型別。

*hasImplements*<br/>
布林值，如果為 **`true`** ，表示您無法將[MixIn](mixin-structure.md)結構與不是衍生自[Implements](implements-structure.md)結構的類別搭配使用。

## <a name="members"></a>成員

### <a name="protected-methods"></a>保護方法

名稱                                                   | 說明
------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ChainInterfaces：： CanCastTo](#cancastto)               | 指出指定的介面識別碼是否可以轉換成範本參數所定義的每個特製化 `ChainInterface` 。
[ChainInterfaces：： CastToUnknown](#casttounknown)       | 將*I0*範本參數所定義之類型的介面指標轉換為的指標 `IUnknown` 。
[ChainInterfaces：： FillArrayWithIid](#fillarraywithiid) | 將*I0*範本參數所定義的介面識別碼，儲存至指定之介面識別碼陣列中的指定位置。
[ChainInterfaces：： Verify](#verify)                     | 確認透過*I9-7xxx* *I0*的範本參數所定義的每個介面都繼承自 `IUnknown` 和/或 `IInspectable` ，而且該*I0*會繼承自*i9-7xxx*的*I1* 。

### <a name="protected-constants"></a>受保護的常數

名稱                                   | 說明
-------------------------------------- | -----------------------------------------------------------------------------------------------------------------
[ChainInterfaces：： IidCount](#iidcount) | 透過*I9-7xxx* *I0*的範本參數所指定之介面中包含的介面識別碼總數。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`I0`

`ChainInterfaces`

## <a name="requirements"></a>需求

**標頭：** implements。h

**命名空間：** Microsoft::WRL

## <a name="chaininterfacescancastto"></a><a name="cancastto"></a>ChainInterfaces：： CanCastTo

指出指定的介面識別碼是否可以轉換成非預設範本參數所定義的每個特製化。

```cpp
__forceinline bool CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>參數

*riid*<br/>
介面識別碼。

*ppv*<br/>
成功轉換的最後一個介面識別碼的指標。

### <a name="return-value"></a>傳回值

**`true`** 如果所有轉換作業都成功，則為，否則為 **`false`** 。

## <a name="chaininterfacescasttounknown"></a><a name="casttounknown"></a>ChainInterfaces：： CastToUnknown

將*I0*範本參數所定義之類型的介面指標轉換為的指標 `IUnknown` 。

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>傳回值

`IUnknown` 的指標。

## <a name="chaininterfacesfillarraywithiid"></a><a name="fillarraywithiid"></a>ChainInterfaces：： FillArrayWithIid

將*I0*範本參數所定義的介面識別碼，儲存至指定之介面識別碼陣列中的指定位置。

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>參數

*指數*<br/>
*Iid*陣列中的索引值指標。

*iid*<br/>
介面識別碼的陣列。

## <a name="chaininterfacesiidcount"></a><a name="iidcount"></a>ChainInterfaces：： IidCount

透過*I9-7xxx* *I0*的範本參數所指定之介面中包含的介面識別碼總數。

```cpp
static const unsigned long IidCount = Details::InterfaceTraits<I0>::IidCount + Details::InterfaceTraits<I1>::IidCount + Details::InterfaceTraits<I2>::IidCount + Details::InterfaceTraits<I3>::IidCount + Details::InterfaceTraits<I4>::IidCount + Details::InterfaceTraits<I5>::IidCount + Details::InterfaceTraits<I6>::IidCount + Details::InterfaceTraits<I7>::IidCount + Details::InterfaceTraits<I8>::IidCount + Details::InterfaceTraits<I9>::IidCount;
```

### <a name="return-value"></a>傳回值

介面識別碼的總數。

### <a name="remarks"></a>備註

範本參數*I0*和*I1*是必要的，而*透過* *i9-7xxx*的參數則是選擇性的。 每個介面的 IID 計數通常是1。

## <a name="chaininterfacesverify"></a><a name="verify"></a>ChainInterfaces：： Verify

確認透過*I9-7xxx* *I0*的範本參數所定義的每個介面都繼承自 `IUnknown` 和/或 `IInspectable` ，而且該*I0*會繼承自*i9-7xxx*的*I1* 。

```cpp
WRL_NOTHROW __forceinline static void Verify();
```

### <a name="remarks"></a>備註

如果驗證作業失敗，會 **`static_assert`** 發出描述失敗的錯誤訊息。

範本參數*I0*和*I1*是必要的，而*透過* *i9-7xxx*的參數則是選擇性的。
