---
title: '&lt;deque&gt;'
ms.date: 11/04/2016
f1_keywords:
- <deque>
helpviewer_keywords:
- deque header
ms.assetid: 4521fe92-5a91-4853-9e9f-59600bf9e46f
ms.openlocfilehash: a5fea8f4a1bc1612a35db71cc515ba4799e95da6
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689719"
---
# <a name="ltdequegt"></a>&lt;deque&gt;

定義容器類別範本 deque 和數個支援的範本。

## <a name="requirements"></a>需求

**標頭**：\<deque>

> [!NOTE]
> @No__t_0deque > 程式庫也會使用 `#include <initializer_list>` 語句。

## <a name="members"></a>Members

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
|[deque 類別](../standard-library/deque-class.md)|序列容器的類別樣板，以線性相片順序排列指定類型的專案，如向量，則允許快速隨機存取任何專案，並在容器的背面有效率地插入和刪除。|

## <a name="see-also"></a>請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)
