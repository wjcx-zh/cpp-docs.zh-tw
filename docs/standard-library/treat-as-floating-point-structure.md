---
title: treat_as_floating_point 結構 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- chrono/std::chrono::treat_as_floating_point
dev_langs:
- C++
ms.assetid: d0a2161c-bbb2-4924-8961-7568d5ad5434
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 96687959ce4fdd7b5431611a64b878cf05f855ab
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="treatasfloatingpoint-structure"></a>treat_as_floating_point 結構

指定是否可將 `Rep` 視為浮點類型。

## <a name="syntax"></a>語法

```cpp
template <class Rep>
struct treat_as_floating_point : is_floating_point<Rep>;
```

## <a name="remarks"></a>備註

只有在特製化 `treat_as_floating_point<Rep>` 衍生自 [true_type](../standard-library/type-traits-typedefs.md#true_type) 時，才能將 `Rep` 視為浮點類型。 可以將樣板類別特製化以用於使用者定義類型。

## <a name="requirements"></a>需求

**標頭：** \<chrono >

**命名空間：** std::chrono

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<chrono>](../standard-library/chrono.md)<br/>
