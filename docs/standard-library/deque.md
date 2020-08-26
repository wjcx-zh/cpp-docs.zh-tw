---
title: '&lt;deque&gt;'
ms.date: 11/04/2016
f1_keywords:
- <deque>
helpviewer_keywords:
- deque header
ms.assetid: 4521fe92-5a91-4853-9e9f-59600bf9e46f
ms.openlocfilehash: 8ecfb85fb77c6b70d1c89aa0cfe1ce76c5d60ab6
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838564"
---
# <a name="ltdequegt"></a>&lt;deque&gt;

定義容器類別範本 deque 和數個支援的範本。

## <a name="requirements"></a>規格需求

**標頭**： \<deque>

> [!NOTE]
> 連結 \<deque> 庫也會使用 `#include <initializer_list>` 語句。

## <a name="members"></a>成員

### <a name="operators"></a>運算子

|名稱|描述|
|-|-|
|[operator！ =](../standard-library/deque-operators.md#op_neq)|測試運算子左邊的 deque 物件是否不等於右邊的 deque 物件。|
|[運算子<](../standard-library/deque-operators.md#op_lt)|測試運算子左邊的 deque 物件是否小於右邊的 deque 物件。|
|[運算元\<=](../standard-library/deque-operators.md#op_gt_eq)|測試運算子左邊的 deque 物件是否小於或等於右邊的 deque 物件。|
|[operator = =](../standard-library/deque-operators.md#op_eq_eq)|測試運算子左邊的 deque 物件是否等於右邊的 deque 物件。|
|[運算子>](../standard-library/deque-operators.md#op_gt)|測試運算子左邊的 deque 物件是否大於右邊的 deque 物件。|
|[運算子>=](../standard-library/deque-operators.md#op_gt_eq)|測試運算子左邊的 deque 物件是否大於或等於右邊的 deque 物件。|

### <a name="functions"></a>Functions

|名稱|描述|
|-|-|
|[交換](../standard-library/deque-functions.md#swap)|交換兩個 deque 的項目。|

### <a name="classes"></a>類別

|名稱|描述|
|-|-|
|[deque 類別](../standard-library/deque-class.md)|順序容器的類別樣板，會以線性相片順序排列指定類型的專案，而且像向量一樣允許快速隨機存取任何專案，以及有效率地在容器背面插入和刪除。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)
