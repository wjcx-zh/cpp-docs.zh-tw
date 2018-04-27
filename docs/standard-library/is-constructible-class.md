---
title: is_constructible 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- type_traits/std::is_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_constructible
ms.assetid: 7cdec5ff-73cf-4f78-a9db-ced2e9c0fd7f
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b030d50861a207828b406bd683f02089070755be
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="isconstructible-class"></a>is_constructible 類別

測試當使用指定的引數類型時，類型是否是可建構的類型。

## <a name="syntax"></a>語法

```cpp
template <class T, class... Args>
struct is_constructible;
```

### <a name="parameters"></a>參數

`T` 要查詢的類型。

`Args` 引數類型的建構函式中要比對`T`。

## <a name="remarks"></a>備註

如果類型 `T` 是可藉由使用 `Args` 中的引數類型來建構的類型，類型述詞執行個體的值就會是 true，否則會是 false。 如果變數定義 `T t(std::declval<Args>()...);` 格式正確，類型 `T` 便是可建構的類型。 `T` 和 `Args` 中的所有類型必須都是完整類型 `void`，或是界限未知的陣列。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
