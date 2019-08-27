---
title: '&lt;deque&gt;'
ms.date: 11/04/2016
f1_keywords:
- <deque>
helpviewer_keywords:
- deque header
ms.assetid: 4521fe92-5a91-4853-9e9f-59600bf9e46f
ms.openlocfilehash: 145ce22091ea1a42619ad7b1fd25507c6315a9ec
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454490"
---
# <a name="ltdequegt"></a>&lt;deque&gt;

定義容器範本類別 deque，以及數個支援的範本。

## <a name="requirements"></a>需求

**標頭**：\<deque>

> [!NOTE]
> Deque > 程式庫也會`#include <initializer_list>`使用語句。 \<

## <a name="members"></a>成員

### <a name="operators"></a>運算子

|||
|-|-|
|[operator!=](../standard-library/deque-operators.md#op_neq)|測試運算子左邊的 deque 物件是否不等於右邊的 deque 物件。|
|[operator<](../standard-library/deque-operators.md#op_lt)|測試運算子左邊的 deque 物件是否小於右邊的 deque 物件。|
|[operator\<=](../standard-library/deque-operators.md#op_gt_eq)|測試運算子左邊的 deque 物件是否小於或等於右邊的 deque 物件。|
|[operator==](../standard-library/deque-operators.md#op_eq_eq)|測試運算子左邊的 deque 物件是否等於右邊的 deque 物件。|
|[operator>](../standard-library/deque-operators.md#op_gt)|測試運算子左邊的 deque 物件是否大於右邊的 deque 物件。|
|[operator>=](../standard-library/deque-operators.md#op_gt_eq)|測試運算子左邊的 deque 物件是否大於或等於右邊的 deque 物件。|

### <a name="functions"></a>函式

|||
|-|-|
|[swap](../standard-library/deque-functions.md#swap)|交換兩個 deque 的項目。|

### <a name="classes"></a>類別

|||
|-|-|
|[deque 類別](../standard-library/deque-class.md)|序列容器的範本類別，以線性排列方式排列指定類型的項目，並且像向量一樣允許快速隨機存取任何項目，可有效率地在容器背面插入和刪除。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)
