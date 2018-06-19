---
title: is_trivially_assignable 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_assignable
ms.assetid: 1284a8f7-4093-426d-9c9a-dabb46f90d6d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b604a4c9a2fc11a9c7274d0e29ab98acfd260907
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33912650"
---
# <a name="istriviallyassignable-class"></a>is_trivially_assignable 類別

測試是否可將 `From` 類型的值透過極簡方式指派給 `To` 類型

## <a name="syntax"></a>語法

```cpp
template <class To, class From>
struct is_trivially_assignable;
```

### <a name="parameters"></a>參數

若要接收指派的物件類型。

從提供的值的物件類型。

## <a name="remarks"></a>備註

運算式 `declval<To>() = declval<From>()` 必須格式正確，且編譯器必須已知它不需要任何非極簡作業。 `From` 和 `To` 兩者必須是完整類型 `void`，或是界限未知的陣列。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
