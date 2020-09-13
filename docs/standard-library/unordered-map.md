---
title: '&lt;unordered_map&gt;'
description: C + + 標準程式庫容器類別的 API 總覽 `map` 。
ms.date: 11/04/2016
f1_keywords:
- <unordered_map>
helpviewer_keywords:
- unordered_map header
ms.assetid: eb90ecb2-250a-4be1-83d2-f66b2917edde
ms.openlocfilehash: 6a25b69155f5428a7269ea35f104f30df0b61877
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90042135"
---
# <a name="ltunordered_mapgt"></a>&lt;unordered_map&gt;

定義容器類別範本 [unordered_map](../standard-library/unordered-map-class.md) 和 [unordered_multimap](../standard-library/unordered-multimap-class.md) 及其支援的範本。

## <a name="syntax"></a>語法

```cpp
#include <unordered_map>
```

> [!NOTE]
> 連結 \<unordered_map> 庫也會使用 `#include <initializer_list>` 語句。

### <a name="classes"></a>類別

|類別|描述|
|-|-|
|[unordered_map 類別](../standard-library/unordered-map-class.md)|儲存 {key, mapped} 配對的雜湊表。|
|[unordered_multimap 類別](../standard-library/unordered-multimap-class.md)|儲存 {key, mapped} 配對的雜湊表。|

### <a name="functions"></a>函式

|函式|描述|
|-|-|
|[operator！ =](../standard-library/unordered-map-operators.md#op_neq)|測試運算子左邊的 unordered_map 物件是否不等於右邊的 unordered_map 物件。|
|[operator = =](../standard-library/unordered-map-operators.md#op_eq_eq)|測試運算子左邊的 unordered_map 物件是否等於右邊的 unordered_map 物件。|
|[swap 函式 (unordered_map)](../standard-library/unordered-map-functions.md#swap)|交換兩個對應。|
|[operator！ =](../standard-library/unordered-map-operators.md#op_neq)|測試運算子左邊的 unordered_multimap 物件是否不等於右邊的 unordered_multimap 物件。|
|[operator = =](../standard-library/unordered-map-operators.md#op_eq_eq)|測試運算子左邊的 unordered_multimap 物件是否等於右邊的 unordered_multimap 物件。|
|[swap 函式 (unordered_map)](../standard-library/unordered-map-functions.md#swap)|交換兩個多重對應。|

## <a name="see-also"></a>另請參閱

[unordered_multiset 類別](../standard-library/unordered-multiset-class.md)\
[unordered_set 類別](../standard-library/unordered-set-class.md)
