---
title: '&lt;vector&gt;'
ms.date: 11/04/2016
f1_keywords:
- <vector>
helpviewer_keywords:
- vector header
ms.assetid: c1431ad8-c0b6-4dbb-89c4-5f651e432d7f
ms.openlocfilehash: 348b5c53ecd3fb7900d03fed7c1209a2c94eeb4c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410849"
---
# <a name="ltvectorgt"></a>&lt;vector&gt;

定義容器範本類別 vector 以及數個支援的範本。

`vector` 是以線性順序組織指定類型項目的容器。 它可讓您快速隨機存取任何項目，並動態地加入序列及從序列中移除。 當隨機存取效能很重要時，`vector` 是慣用的序列容器。

如需類別 `vector` 的詳細資訊，請參閱 [vector 類別](../standard-library/vector-class.md)。 如需特製化 `vector<bool>` 的相關資訊，請參閱 [vector\<bool> 類別](../standard-library/vector-bool-class.md)。

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

*Type*<br/>
儲存在向量中之資料類型的樣板參數。

*Allocator*<br/>
儲存之配置器物件的樣板參數，負責記憶體配置和解除配置。

*left*<br/>
比較作業中的第一個 (左) 向量

*right*<br/>
比較作業中的第二個 (右) 向量。

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator! =](../standard-library/vector-operators.md#op_neq)|測試運算子左邊的向量物件是否不等於右邊的向量物件。|
|[operator<](../standard-library/vector-operators.md#op_lt)|測試運算子左邊的向量物件是否小於右邊的向量物件。|
|[operator\<=](../standard-library/vector-operators.md#op_gt_eq)|測試運算子左邊的向量物件是否小於或等於右邊的向量物件。|
|[operator==](../standard-library/vector-operators.md#op_eq_eq)|測試運算子左邊的向量物件是否等於右邊的向量物件。|
|[operator>](../standard-library/vector-operators.md#op_gt)|測試運算子左邊的向量物件是否大於右邊的向量物件。|
|[operator>=](../standard-library/vector-operators.md#op_gt_eq)|測試運算子左邊的向量物件是否大於或等於右邊的向量物件。|

### <a name="classes"></a>類別

|類別|描述|
|-|-|
|[vector 類別](../standard-library/vector-class.md)|序列容器的類別範本，其以線性排列方式排列指定類型的項目，並允許快速隨機存取任何項目。|

### <a name="specializations"></a>特製化

|||
|-|-|
|[vector\<bool> 類別](../standard-library/vector-bool-class.md)|`bool` 類型項目之樣板類別向量的完整特製化，並提供特製化所使用之基礎類型的配置器。|

## <a name="requirements"></a>需求

**標頭：** \<vector>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>
