---
title: ChainInterfaces 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces
dev_langs:
- C++
helpviewer_keywords:
- ChainInterfaces structure
ms.assetid: d7415b59-5468-4bef-a3fd-8d82b12f0e9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 88ddd3dd59000b629f6e72933b1a0b02cc582c89
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409867"
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
struct ChainInterfaces<MixIn<DerivedType, BaseType, hasImplements>, I1, I2, I3, I4, I5, I6, I7, I8, I9>;
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
布林值，如果 **，則為 true**，表示您無法使用[MixIn](../windows/mixin-structure.md)不是衍生自的類別結構[實作](../windows/implements-structure.md)結構。

## <a name="members"></a>成員

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[ChainInterfaces::CanCastTo 方法](../windows/chaininterfaces-cancastto-method.md)|指出指定的介面識別碼是否可轉換成每個所定義的特製化**ChainInterface**範本參數。|
|[ChainInterfaces::CastToUnknown 方法](../windows/chaininterfaces-casttounknown-method.md)|將轉換的型別所定義的介面指標*I0*樣板參數的指標`IUnknown`。|
|[ChainInterfaces::FillArrayWithIid 方法](../windows/chaininterfaces-fillarraywithiid-method.md)|介面 ID 所定義的存放區*I0*範本參數，以指定陣列中的介面識別碼指定的位置插入。|
|[ChainInterfaces::Verify 方法](../windows/chaininterfaces-verify-method.md)|確認每個介面定義的範本參數*I0*透過*I9*繼承`IUnknown`及/或`IInspectable`，而且*I0*繼承自*I1*透過*I9*。|

### <a name="protected-constants"></a>受保護的常數

|名稱|描述|
|----------|-----------------|
|[ChainInterfaces::IidCount 常數](../windows/chaininterfaces-iidcount-constant.md)|介面包含在範本參數所指定的介面識別碼的總數*I0*透過*I9*。|

## <a name="inheritance-hierarchy"></a>繼承階層

`I0`

`ChainInterfaces`

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)