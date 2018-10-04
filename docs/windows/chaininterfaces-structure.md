---
title: ChainInterfaces 結構 |Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces
- implements/Microsoft::WRL::ChainInterfaces::CanCastTo
- implements/Microsoft::WRL::ChainInterfaces::CastToUnknown
- implements/Microsoft::WRL::ChainInterfaces::FillArrayWithIid
- implements/Microsoft::WRL::ChainInterfaces::IidCount
- implements/Microsoft::WRL::ChainInterfaces::Verify
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::ChainInterfaces structure
- Microsoft::WRL::ChainInterfaces::CanCastTo method
- Microsoft::WRL::ChainInterfaces::CastToUnknown method
- Microsoft::WRL::ChainInterfaces::FillArrayWithIid method
- Microsoft::WRL::ChainInterfaces::IidCount constant
- Microsoft::WRL::ChainInterfaces::Verify method
ms.assetid: d7415b59-5468-4bef-a3fd-8d82b12f0e9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: df483f08e96f2bd479504028ce4ce17513bb7d41
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789017"
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
（必要）介面識別碼 0。

*I1*<br/>
（必要）介面識別碼為 1。

*I2*<br/>
（選擇性）介面識別碼 2。

*I3*<br/>
（選擇性）介面 ID 3。

*I4*<br/>
（選擇性）介面 ID 4。

*I5 中*<br/>
（選擇性）介面識別碼 5。

*I6*<br/>
（選擇性）介面識別碼 6。

*I7*<br/>
（選擇性）介面識別碼 7。

*I8*<br/>
（選擇性）介面識別碼 8。

*I9*<br/>
（選擇性）介面識別碼 9。

*DerivedType*<br/>
在衍生的型別。

*BaseType*<br/>
衍生型別的基底型別。

*hasImplements*<br/>
布林值，如果`true`，表示您無法使用[MixIn](../windows/mixin-structure.md)不是衍生自的類別結構[實作](../windows/implements-structure.md)結構。

## <a name="members"></a>成員

### <a name="protected-methods"></a>保護方法

名稱                                                   | 描述
------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[Chaininterfaces:: Cancastto](#cancastto)               | 指出指定的介面識別碼是否可轉換成每個所定義的特製化`ChainInterface`範本參數。
[Chaininterfaces:: Casttounknown](#casttounknown)       | 將轉換的型別所定義的介面指標*I0*樣板參數的指標`IUnknown`。
[Chaininterfaces:: Fillarraywithiid](#fillarraywithiid) | 介面 ID 所定義的存放區*I0*範本參數，以指定陣列中的介面識別碼指定的位置插入。
[Chaininterfaces:: Verify](#verify)                     | 確認每個介面定義的範本參數*I0*透過*I9*繼承`IUnknown`及/或`IInspectable`，而且*I0*繼承自*I1*透過*I9*。

### <a name="protected-constants"></a>受保護的常數

名稱                                   | 描述
-------------------------------------- | -----------------------------------------------------------------------------------------------------------------
[Chaininterfaces:: Iidcount](#iidcount) | 介面包含在範本參數所指定的介面識別碼的總數*I0*透過*I9*。

## <a name="inheritance-hierarchy"></a>繼承階層

`I0`

`ChainInterfaces`

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL

## <a name="cancastto"></a>Chaininterfaces:: Cancastto

指出指定的介面識別碼是否可轉換成每個非預設的範本參數所定義的特製化。

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
已成功轉換的最後一個介面識別碼指標。

### <a name="return-value"></a>傳回值

`true` 如果成功轉換的所有作業，否則， `false`。

## <a name="casttounknown"></a>Chaininterfaces:: Casttounknown

將轉換的型別所定義的介面指標*I0*樣板參數的指標`IUnknown`。

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>傳回值

指標`IUnknown`。

## <a name="fillarraywithiid"></a>Chaininterfaces:: Fillarraywithiid

介面 ID 所定義的存放區*I0*範本參數，以指定陣列中的介面識別碼指定的位置插入。

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>參數

*index*<br/>
到索引值的指標*iid*陣列。

*iid*<br/>
介面識別碼的陣列。

## <a name="iidcount"></a>Chaininterfaces:: Iidcount

介面包含在範本參數所指定的介面識別碼的總數*I0*透過*I9*。

```cpp
static const unsigned long IidCount = Details::InterfaceTraits<I0>::IidCount + Details::InterfaceTraits<I1>::IidCount + Details::InterfaceTraits<I2>::IidCount + Details::InterfaceTraits<I3>::IidCount + Details::InterfaceTraits<I4>::IidCount + Details::InterfaceTraits<I5>::IidCount + Details::InterfaceTraits<I6>::IidCount + Details::InterfaceTraits<I7>::IidCount + Details::InterfaceTraits<I8>::IidCount + Details::InterfaceTraits<I9>::IidCount;
```

### <a name="return-value"></a>傳回值

介面識別碼的總數。

### <a name="remarks"></a>備註

範本參數*I0*並*I1*是必要的以及參數*I2*透過*I9*是選擇性的。每個介面的 IID 計數通常是 1。

## <a name="verify"></a>Chaininterfaces:: Verify

確認每個介面定義的範本參數*I0*透過*I9*繼承`IUnknown`及/或`IInspectable`，而且*I0*繼承自*I1*透過*I9*。

```cpp
WRL_NOTHROW __forceinline static void Verify();
```

### <a name="remarks"></a>備註

如果驗證作業失敗，`static_assert`發出描述失敗的錯誤訊息。

範本參數*I0*並*I1*是必要的以及參數*I2*透過*I9*是選擇性的。
