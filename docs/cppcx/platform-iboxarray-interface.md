---
title: Platform::IBoxArray 介面
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Namespace not found::Platform
- VCCORLIB/Namespace not found::Platform::Value
helpviewer_keywords:
- Platform::IBoxArray
ms.assetid: 6cd82c9e-4230-4147-9edb-7a652875dbf1
ms.openlocfilehash: a35a8b7d9f23bcb624755353e27e52de4b873c5d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50497003"
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

`IBoxArray` 是 C + + /CX 名稱`Windows::Foundation::IReferenceArray`。

### <a name="members"></a>成員

`IBoxArray` 介面繼承自 `IValueType` 介面。 `IBoxArray` 也有這些成員：

|方法|描述|
|------------|-----------------|
|[值](#value)|傳回之前儲存在這個 `IBoxArray` 執行個體中的 Unboxed 陣列。|

## <a name="value"></a> Iboxarray:: Value 屬性

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

如需範例，請參閱[Boxing](../cppcx/boxing-c-cx.md)。

## <a name="see-also"></a>另請參閱

[Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)