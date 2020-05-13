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
ms.openlocfilehash: dd1af3fb5c1079a40d8248dc71ae4972537aa856
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372656"
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
( 必要 )介面 ID 0。

*I1*<br/>
( 必要 )介面識別碼 1。

*I2*<br/>
( 選擇性的 )介面 ID 2。

*I3*<br/>
( 選擇性的 )介面 ID 3。

*I4*<br/>
( 選擇性的 )介面 ID 4。

*I5*<br/>
( 選擇性的 )介面 ID 5。

*I6*<br/>
( 選擇性的 )介面 ID 6。

*I7*<br/>
( 選擇性的 )介面 ID 7。

*I8*<br/>
( 選擇性的 )介面 ID 8。

*I9*<br/>
( 選擇性的 )介面 ID 9。

*衍生類型*<br/>
派生類型。

*BaseType*<br/>
派生類型的基類型。

*有實現*<br/>
布爾值,如果為**true,** 則意味著不能將[MixIn](mixin-structure.md)結構與不派生自[實現](implements-structure.md)結構的類一起使用。

## <a name="members"></a>成員

### <a name="protected-methods"></a>保護方法

名稱                                                   | 描述
------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[連結口::坎卡斯特托](#cancastto)               | 指示是否可以將指定的介面 ID 強制`ChainInterface`轉換為 範本參數定義的每個專門化。
[連結埠::Castto 未知](#casttounknown)       | 將*I0*模板參數定義的類型的介面指標強制轉換為`IUnknown`指向的指標。
[連結口::填充與Iid](#fillarraywithiid) | 將*I0*模板參數定義的介面 ID 儲存在指定的介面 ID 陣列中的指定位置。
[連結埠:驗證](#verify)                     | 驗證樣本參數*I0*到*I9*定義`IUnknown`的每個介面`IInspectable`繼承和/或 ,並且*I0*繼承從*I1*到*I9*。

### <a name="protected-constants"></a>受保護的常量

名稱                                   | 描述
-------------------------------------- | -----------------------------------------------------------------------------------------------------------------
[連結口::IidCount](#iidcount) | 範本參數*I0*透過*I9*指定的介面中包含的介面 ID 總數。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`I0`

`ChainInterfaces`

## <a name="requirements"></a>需求

**標題:** 實現.h

**命名空間：** Microsoft::WRL

## <a name="chaininterfacescancastto"></a><a name="cancastto"></a>連結口::坎卡斯特托

指示是否可以將指定的介面 ID 強制轉換為非預設樣本參數定義的每個專門化。

```cpp
__forceinline bool CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>參數

*riid*<br/>
介面識別碼。

*Ppv*<br/>
指向成功強制轉換的最後一個介面 ID 的指標。

### <a name="return-value"></a>傳回值

如果所有強制轉換操作都成功,**則為 true;** 否則,**假**。

## <a name="chaininterfacescasttounknown"></a><a name="casttounknown"></a>連結埠::Castto 未知

將*I0*模板參數定義的類型的介面指標強制轉換為`IUnknown`指向的指標。

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>傳回值

`IUnknown` 的指標。

## <a name="chaininterfacesfillarraywithiid"></a><a name="fillarraywithiid"></a>連結口::填充與Iid

將*I0*模板參數定義的介面 ID 儲存在指定的介面 ID 陣列中的指定位置。

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>參數

*指數*<br/>
指向*iids*陣列中的索引值。

*伊德*<br/>
介面指示的陣列。

## <a name="chaininterfacesiidcount"></a><a name="iidcount"></a>連結口::IidCount

範本參數*I0*透過*I9*指定的介面中包含的介面 ID 總數。

```cpp
static const unsigned long IidCount = Details::InterfaceTraits<I0>::IidCount + Details::InterfaceTraits<I1>::IidCount + Details::InterfaceTraits<I2>::IidCount + Details::InterfaceTraits<I3>::IidCount + Details::InterfaceTraits<I4>::IidCount + Details::InterfaceTraits<I5>::IidCount + Details::InterfaceTraits<I6>::IidCount + Details::InterfaceTraits<I7>::IidCount + Details::InterfaceTraits<I8>::IidCount + Details::InterfaceTraits<I9>::IidCount;
```

### <a name="return-value"></a>傳回值

介面指示的總數。

### <a name="remarks"></a>備註

範本參數*I0*和*I1*是必需的,參數*I2*到*I9*是可選的。 每個介面的 IID 計數通常為 1。

## <a name="chaininterfacesverify"></a><a name="verify"></a>連結埠:驗證

驗證樣本參數*I0*到*I9*定義`IUnknown`的每個介面`IInspectable`繼承和/或 ,並且*I0*繼承從*I1*到*I9*。

```cpp
WRL_NOTHROW __forceinline static void Verify();
```

### <a name="remarks"></a>備註

如果驗證操作失敗,則發出`static_assert`描述故障的錯誤消息。

範本參數*I0*和*I1*是必需的,參數*I2*到*I9*是可選的。
