---
title: Platform::IBoxArray 介面
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::IBoxArray
- VCCORLIB/Platform::IBoxArray::Value
helpviewer_keywords:
- Platform::IBoxArray
ms.assetid: 6cd82c9e-4230-4147-9edb-7a652875dbf1
ms.openlocfilehash: 493770cab092c2bb719d47e5d3a9d6a9f0646489
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444166"
---
# <a name="platformiboxarray-interface"></a>Platform::IBoxArray 介面

`IBoxArray` 是實值類型陣列的包裝函式，這些實值類型會在不同的應用程式二進位介面 (ABI) 之間傳遞或是儲存在 `Platform::Object^` 元素的集合中，例如在 XAML 控制項中。

## <a name="syntax"></a>語法

```cpp
template <typename T>
interface class IBoxArray
```

#### <a name="parameters"></a>參數

*T*<br/>
每個陣列元素中 Boxed 值的類型。

### <a name="remarks"></a>備註

`IBoxArray` 是 `Windows::Foundation::IReferenceArray`C++的/cx 名稱。

### <a name="members"></a>成員

`IBoxArray` 介面繼承自 `IValueType` 介面。 `IBoxArray` 也有這些成員：

|方法|描述|
|------------|-----------------|
|[ReplTest1](#value)|傳回之前儲存在這個 `IBoxArray` 執行個體中的 Unboxed 陣列。|

## <a name="value"></a>IBoxArray：： Value 屬性

傳回一開始儲存在這個物件中的值。

### <a name="syntax"></a>語法

```cpp
property T Value {T get();}
```

### <a name="parameters"></a>參數

*T*<br/>
boxed 值的類型。

### <a name="property-valuereturn-value"></a>屬性值/傳回值

傳回一開始儲存在這個物件中的值。

### <a name="remarks"></a>備註

如需範例，請參閱[裝箱](../cppcx/boxing-c-cx.md)。

## <a name="see-also"></a>另請參閱

[Array 與 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)
