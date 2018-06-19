---
title: is_move_constructible 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_move_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_move_constructible
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d87eac720b205560993a7d6995be8a8fe6ad6194
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33843518"
---
# <a name="ismoveconstructible-class"></a>is_move_constructible 類別

測試類型是否具有移動建構函式。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>參數

要評估的 T 類型

## <a name="remarks"></a>備註

如果類型 `T` 是可藉由使用移動作業來建構的類型，類型述詞就會評估為 true。 這個述詞相當於 `is_constructible<T, T&&>`。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
