---
title: '&lt;vector&gt;'
ms.date: 11/04/2016
f1_keywords:
- <vector>
helpviewer_keywords:
- vector header
ms.assetid: c1431ad8-c0b6-4dbb-89c4-5f651e432d7f
ms.openlocfilehash: 7cecff1e5e0014c4f1a4294a5c6ba25c5d38da67
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840007"
---
# <a name="ltvectorgt"></a>&lt;vector&gt;

定義容器類別範本向量和數個支援的範本。

`vector` 是以線性順序組織指定類型項目的容器。 它可讓您快速隨機存取任何項目，並動態地加入序列及從序列中移除。 當隨機存取效能很重要時，`vector` 是慣用的序列容器。

> [!NOTE]
> 連結 \<vector> 庫也會使用 `#include <initializer_list>` 語句。

如需類別 `vector` 的詳細資訊，請參閱 [vector 類別](../standard-library/vector-class.md)。 如需特製化的詳細資訊 `vector<bool>` ，請參閱 [vector \<bool> 類別](../standard-library/vector-bool-class.md)。

## <a name="syntax"></a>語法

```cpp
namespace std {
template <class Type, class Allocator>
class vector;
template <class Allocator>
class vector<bool>;

template <class Allocator>
struct hash<vector<bool, Allocator>>;

// TEMPLATE FUNCTIONS
template <class Type, class Allocator>
bool operator== (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator!= (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator<(
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator> (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator<= (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator>= (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
void swap (
    vector<Type, Allocator>& left,
    vector<Type, Allocator>& right);

}  // namespace std
```

### <a name="parameters"></a>參數

*類型*\
儲存在向量中之資料類型的樣板參數。

*分配器*\
儲存之配置器物件的樣板參數，負責記憶體配置和解除配置。

*離開*\
比較作業中的第一個 (左) 向量

*對*\
比較作業中的第二個 (右) 向量。

## <a name="members"></a>成員

### <a name="operators"></a>運算子

|名稱|描述|
|-|-|
|[運算元！=](../standard-library/vector-operators.md#op_neq)|測試運算子左邊的向量物件是否不等於右邊的向量物件。|
|[運算子<](../standard-library/vector-operators.md#op_lt)|測試運算子左邊的向量物件是否小於右邊的向量物件。|
|[運算元\<=](../standard-library/vector-operators.md#op_gt_eq)|測試運算子左邊的向量物件是否小於或等於右邊的向量物件。|
|[operator = =](../standard-library/vector-operators.md#op_eq_eq)|測試運算子左邊的向量物件是否等於右邊的向量物件。|
|[運算子>](../standard-library/vector-operators.md#op_gt)|測試運算子左邊的向量物件是否大於右邊的向量物件。|
|[運算子>=](../standard-library/vector-operators.md#op_gt_eq)|測試運算子左邊的向量物件是否大於或等於右邊的向量物件。|

### <a name="classes"></a>類別

|名稱|描述|
|-|-|
|[vector 類別](../standard-library/vector-class.md)|序列容器的類別樣板，以線性排列方式排列指定類型的項目，並允許快速隨機存取任何項目。|

### <a name="specializations"></a>特製化

|名稱|描述|
|-|-|
|雜湊|傳回向量的雜湊。|
|[vector \<bool> 類別](../standard-library/vector-bool-class.md)|類型專案之類別樣板向量的完整特製化， **`bool`** 具有特製化所使用之基礎類型的配置器。|

## <a name="requirements"></a>規格需求

**標頭：**\<vector>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)
