---
title: is_constructible 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_constructible
helpviewer_keywords:
- is_constructible
ms.assetid: 7cdec5ff-73cf-4f78-a9db-ced2e9c0fd7f
ms.openlocfilehash: c921efd5b7e12873ce986952029ae39f118ad763
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658649"
---
# <a name="isconstructible-class"></a>is_constructible 類別

測試當使用指定的引數類型時，類型是否是可建構的類型。

## <a name="syntax"></a>語法

```cpp
template <class T, class... Args>
struct is_constructible;
```

### <a name="parameters"></a>參數

*T*<br/>
要查詢的類型。

*Args*<br/>
引數類型的建構函式中要比對*T*。

## <a name="remarks"></a>備註

如果型別述詞的執行個體保留 true 的型別*T*使用中的引數類型是可建構*Args*，否則為 false。 型別*T*是可建構如果變數定義`T t(std::declval<Args>()...);`而言是否格式正確。 兩者*T*和中的所有型別*Args*必須是完整類型**void**，或界限未知的陣列。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
