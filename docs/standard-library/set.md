---
title: '&lt;set&gt;'
ms.date: 11/04/2016
f1_keywords:
- <set>
helpviewer_keywords:
- set header
ms.assetid: 43cb1ab2-6383-48cf-8bdc-2b96d7203596
ms.openlocfilehash: 1bf5663d3e6891d45e2139c612d8e16860b6cace
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246389"
---
# <a name="ltsetgt"></a>&lt;set&gt;

定義容器範本類別 set 和 multiset，以及其支援的範本。

## <a name="requirements"></a>需求

**標頭：** \<set>

**命名空間：** std

> [!NOTE]
> \<設定 > 文件庫也會使用`#include <initializer_list>`陳述式。

## <a name="members"></a>成員

### <a name="operators"></a>運算子

|set 版本|multiset 版本|說明|
|-|-|-|
|[operator!= (set)](../standard-library/set-operators.md#op_neq)|[operator!= (multiset)](../standard-library/set-operators.md#op_neq)|測試運算子左邊的 set 或 multiset 物件是否不等於右邊的 set 或 multiset 物件。|
|[operator< (set)](../standard-library/set-operators.md#op_lt)|[operator< (multiset)](../standard-library/set-operators.md#op_lt_multiset)|測試運算子左邊的 set 或 multiset 物件是否小於右邊的 set 或 multiset 物件。|
|[operator<= (set)](../standard-library/set-operators.md#op_lt_eq)|[operator\<= (multiset)](../standard-library/set-operators.md#op_lt_eq_multiset)|測試運算子左邊的 set 或 multiset 物件是否小於或等於右邊的 set 或 multiset 物件。|
|[operator== (set)](../standard-library/set-operators.md#op_eq_eq)|[operator== (multiset)](../standard-library/set-operators.md#op_eq_eq_multiset)|測試運算子左邊的 set 或 multiset 物件是否等於右邊的 set 或 multiset 物件。|
|[operator> (set)](../standard-library/set-operators.md#op_gt)|[operator> (multiset)](../standard-library/set-operators.md#op_gt_multiset)|測試運算子左邊的 set 或 multiset 物件是否大於右邊的 set 或 multiset 物件。|
|[operator>= (set)](../standard-library/set-operators.md#op_gt_eq)|[operator>= (multiset)](../standard-library/set-operators.md#op_gt_eq_multiset)|測試運算子左邊的 set 或 multiset 物件是否大於或等於右邊的 set 或 multiset 物件。|

### <a name="specialized-template-functions"></a>特製化樣板函式

|set 版本|multiset 版本|描述|
|-|-|-|
|[swap](../standard-library/set-functions.md#swap)|[swap (multiset)](../standard-library/set-functions.md#swap_multiset)|交換兩個 set 或 multiset 的項目。|

### <a name="classes"></a>類別

|||
|-|-|
|[set 類別](../standard-library/set-class.md)|用於在集合中儲存和擷取資料，集合中包含的項目值是唯一的，而且這些項目值做為索引鍵值，據此自動排序資料。|
|[multiset 類別](../standard-library/multiset-class.md)|用於在集合中儲存和擷取資料，集合中包含的項目值不須是唯一的，而且這些項目值做為索引鍵值，據此自動排序資料。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>
