---
title: is_trivially_constructible 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_constructible
helpviewer_keywords:
- is_trivially_constructible
ms.assetid: 3fa918c1-e66f-4d0e-a11b-be1fb2c02e7b
ms.openlocfilehash: c83bea8be5c88876ffa25337464caa62b998ab45
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628835"
---
# <a name="istriviallyconstructible-class"></a>is_trivially_constructible 類別

測試類型在使用指定引數類型的情況下，是否是可透過極簡方式建構的類型。

## <a name="syntax"></a>語法

```cpp
template <class T, class... Args>
struct is_trivially_constructible;
```

### <a name="parameters"></a>參數

*T*<br/>
要查詢的類型。

*Args*<br/>
引數類型的建構函式中要比對*T*。

## <a name="remarks"></a>備註

如果型別述詞的執行個體保留 true 型別*T*是可透過極簡方式建構使用中的引數型別*Args*，否則為 false。 型別*T*是可透過極簡方式建構如果變數定義`T t(std::declval<Args>()...);`而言是否格式正確，且已知呼叫任何非 trivial 作業。 兩者*T*和中的所有型別*Args*必須是完整類型**void**，或界限未知的陣列。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
