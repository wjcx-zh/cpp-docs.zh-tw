---
title: '&lt;set&gt;'
ms.date: 11/04/2016
f1_keywords:
- <set>
helpviewer_keywords:
- set header
ms.assetid: 43cb1ab2-6383-48cf-8bdc-2b96d7203596
ms.openlocfilehash: 4ac5c0bbf94c4d17389efb424d2e12b84717c4a9
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846221"
---
# <a name="ltsetgt"></a>&lt;set&gt;

定義已設定的容器類別範本和多重集，以及其支援的範本。

## <a name="requirements"></a>規格需求

**標頭：**\<set>

**命名空間：** std

> [!NOTE]
> 連結 \<set> 庫也會使用 `#include <initializer_list>` 語句。

## <a name="members"></a>成員

### <a name="operators"></a>運算子

|set 版本|multiset 版本|描述|
|-|-|-|
|[operator！ = (設定) ](../standard-library/set-operators.md#op_neq)|[operator！ = (多重集) ](../standard-library/set-operators.md#op_neq)|測試運算子左邊的 set 或 multiset 物件是否不等於右邊的 set 或 multiset 物件。|
|[運算子< (設定) ](../standard-library/set-operators.md#op_lt)|[運算子< (多重集) ](../standard-library/set-operators.md#op_lt_multiset)|測試運算子左邊的 set 或 multiset 物件是否小於右邊的 set 或 multiset 物件。|
|[運算子<= (設定) ](../standard-library/set-operators.md#op_lt_eq)|[operator\<= (multiset)](../standard-library/set-operators.md#op_lt_eq_multiset)|測試運算子左邊的 set 或 multiset 物件是否小於或等於右邊的 set 或 multiset 物件。|
|[operator = = (設定) ](../standard-library/set-operators.md#op_eq_eq)|[operator = = (多重集) ](../standard-library/set-operators.md#op_eq_eq_multiset)|測試運算子左邊的 set 或 multiset 物件是否等於右邊的 set 或 multiset 物件。|
|[運算子> (設定) ](../standard-library/set-operators.md#op_gt)|[運算子> (多重集) ](../standard-library/set-operators.md#op_gt_multiset)|測試運算子左邊的 set 或 multiset 物件是否大於右邊的 set 或 multiset 物件。|
|[運算子>= (設定) ](../standard-library/set-operators.md#op_gt_eq)|[operator>= (多重集) ](../standard-library/set-operators.md#op_gt_eq_multiset)|測試運算子左邊的 set 或 multiset 物件是否大於或等於右邊的 set 或 multiset 物件。|

### <a name="specialized-template-functions"></a>特製化樣板函式

|set 版本|multiset 版本|描述|
|-|-|-|
|[交換](../standard-library/set-functions.md#swap)|[swap (multiset)](../standard-library/set-functions.md#swap_multiset)|交換兩個 set 或 multiset 的項目。|

### <a name="classes"></a>類別

|名稱|描述|
|-|-|
|[set 類別](../standard-library/set-class.md)|用於在集合中儲存和擷取資料，集合中包含的項目值是唯一的，而且這些項目值做為索引鍵值，據此自動排序資料。|
|[多重集類別](../standard-library/multiset-class.md)|用於在集合中儲存和擷取資料，集合中包含的項目值不須是唯一的，而且這些項目值做為索引鍵值，據此自動排序資料。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)
