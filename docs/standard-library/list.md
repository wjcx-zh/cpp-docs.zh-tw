---
title: list&lt;&gt;
ms.date: 11/04/2016
f1_keywords:
- <list>
helpviewer_keywords:
- list header
ms.assetid: 2345823b-5612-44d8-95d3-aa96ed076d17
ms.openlocfilehash: 6b67434d36146de87a124fc02f49971425943dc5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447270"
---
# <a name="ltlistgt"></a>list&lt;&gt;

定義容器類別範本清單和數個支援的範本。

## <a name="syntax"></a>語法

```cpp
#include <list>
```

> [!NOTE]
> \<清單 > 程式庫也會使用 `#include <initializer_list>` 語句。

## <a name="members"></a>成員

### <a name="operators"></a>操作員

|||
|-|-|
|[operator!=](../standard-library/list-operators.md#op_neq)|測試運算子左邊的清單物件是否不等於右邊的清單物件。|
|[operator<](../standard-library/list-operators.md#op_lt)|測試運算子左邊的清單物件是否小於右邊的清單物件。|
|[operator\<=](../standard-library/list-operators.md#op_gt_eq)|測試運算子左邊的清單物件是否小於或等於右邊的清單物件。|
|[operator==](../standard-library/list-operators.md#op_eq_eq)|測試運算子左邊的清單物件是否等於右邊的清單物件。|
|[operator>](../standard-library/list-operators.md#op_gt)|測試運算子左邊的清單物件是否大於右邊的清單物件。|
|[operator>=](../standard-library/list-operators.md#op_gt_eq)|測試運算子左邊的清單物件是否大於或等於右邊的清單物件。|

### <a name="functions"></a>Functions

|||
|-|-|
|[swap](../standard-library/list-functions.md#swap)|交換兩個清單的項目。|

### <a name="classes"></a>類別

|||
|-|-|
|[list 類別](../standard-library/list-class.md)|序列容器的類別樣板，以線性相片順序維護其元素，並允許在序列內的任何位置進行有效率的插入和刪除。|

## <a name="see-also"></a>另請參閱

[標頭檔參考資料](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準程式庫參考資料](../standard-library/cpp-standard-library-reference.md)
