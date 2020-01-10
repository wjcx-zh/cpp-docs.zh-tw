---
title: treat_as_floating_point 結構
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::treat_as_floating_point
ms.assetid: d0a2161c-bbb2-4924-8961-7568d5ad5434
ms.openlocfilehash: add69179b23a953a937458cbfa55254b21c5ea37
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72685118"
---
# <a name="treat_as_floating_point-structure"></a>treat_as_floating_point 結構

指定是否可將 `Rep` 視為浮點類型。

## <a name="syntax"></a>語法

```cpp
template <class Rep>
struct treat_as_floating_point : is_floating_point<Rep>;
```

## <a name="remarks"></a>備註

只有在特製化 `treat_as_floating_point<Rep>` 衍生自 [true_type](../standard-library/type-traits-typedefs.md#true_type) 時，才能將 `Rep` 視為浮點類型。 類別樣板可以針對使用者定義的型別特製化。

## <a name="requirements"></a>需求

**標頭：** \<chrono >

**命名空間：** std::chrono

## <a name="see-also"></a>請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)
