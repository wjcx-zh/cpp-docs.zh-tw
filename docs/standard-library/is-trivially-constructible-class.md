---
title: is_trivially_constructible 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_constructible
ms.assetid: 3fa918c1-e66f-4d0e-a11b-be1fb2c02e7b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 757a5eb526bc8d4294a64cbdc9645e72285162ce
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="istriviallyconstructible-class"></a>is_trivially_constructible 類別

測試類型在使用指定引數類型的情況下，是否是可透過極簡方式建構的類型。

## <a name="syntax"></a>語法

```cpp
template <class T, class... Args>
struct is_trivially_constructible;
```

### <a name="parameters"></a>參數

`T` 要查詢的類型。

`Args` 引數類型的建構函式中要比對`T`。

## <a name="remarks"></a>備註

如果類型 `T` 是可藉由使用 `Args` 中的引數類型透過極簡方式建構的類型，類型述詞執行個體的值就會是 true，否則會是 false。 如果變數定義 `T t(std::declval<Args>()...);` 格式正確，且已知不會呼叫任何非極簡作業，類型 `T` 便是可透過極簡方式建構的類型。 `T` 和 `Args` 中的所有類型必須都是完整類型 `void`，或是界限未知的陣列。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
