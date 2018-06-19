---
title: underlying_type 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::underlying_type
dev_langs:
- C++
helpviewer_keywords:
- underlying_type
ms.assetid: 691ddce3-2677-4480-bd35-d933fab85d3e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f45af807b37294b87920b6fabac18647f170025
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33853218"
---
# <a name="underlyingtype-class"></a>underlying_type 類別

產生列舉類型的基礎整數類型。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct underlying_type;
```

### <a name="parameters"></a>參數

`T` 要修改的類型。

## <a name="remarks"></a>備註

當 `T` 為列舉類型時，樣板類別的 `type` 成員 typedef 會命名 `T` 的基礎整數類型，否則沒有成員 typedef `type`。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
