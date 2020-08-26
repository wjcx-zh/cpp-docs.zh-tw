---
title: list&lt;&gt;
ms.date: 11/04/2016
f1_keywords:
- <list>
helpviewer_keywords:
- list header
ms.assetid: 2345823b-5612-44d8-95d3-aa96ed076d17
ms.openlocfilehash: cbc93500c3fe61b2a4640008b869f3a6b71b5c6c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833305"
---
# <a name="ltlistgt"></a>list&lt;&gt;

定義容器類別範本清單以及數個支援的範本。

## <a name="syntax"></a>語法

```cpp
#include <list>
```

> [!NOTE]
> 連結 \<list> 庫也會使用 `#include <initializer_list>` 語句。

## <a name="members"></a>成員

### <a name="operators"></a>運算子

|名稱|描述|
|-|-|
|[operator！ =](../standard-library/list-operators.md#op_neq)|測試運算子左邊的清單物件是否不等於右邊的清單物件。|
|[運算子<](../standard-library/list-operators.md#op_lt)|測試運算子左邊的清單物件是否小於右邊的清單物件。|
|[運算元\<=](../standard-library/list-operators.md#op_gt_eq)|測試運算子左邊的清單物件是否小於或等於右邊的清單物件。|
|[operator = =](../standard-library/list-operators.md#op_eq_eq)|測試運算子左邊的清單物件是否等於右邊的清單物件。|
|[運算子>](../standard-library/list-operators.md#op_gt)|測試運算子左邊的清單物件是否大於右邊的清單物件。|
|[運算子>=](../standard-library/list-operators.md#op_gt_eq)|測試運算子左邊的清單物件是否大於或等於右邊的清單物件。|

### <a name="functions"></a>Functions

|名稱|描述|
|-|-|
|[交換](../standard-library/list-functions.md#swap)|交換兩個清單的項目。|

### <a name="classes"></a>類別

|名稱|描述|
|-|-|
|[list 類別](../standard-library/list-class.md)|順序容器的類別範本，以線性相片順序維護其元素，並允許在序列內的任何位置有效率地插入及刪除。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)
