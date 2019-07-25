---
title: forward_iterator_tag 結構
ms.date: 11/04/2016
f1_keywords:
- xutility/std::forward_iterator_tag
helpviewer_keywords:
- forward_iterator_tag struct
- forward_iterator_tag class
ms.assetid: 68b633ac-b135-4e9e-837d-14248a262ec5
ms.openlocfilehash: 687e39ce752bc0d4d289421887570dea6870f8f3
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457128"
---
# <a name="forwarditeratortag-struct"></a>forward_iterator_tag 結構

此類別可提供 **iterator_category** 函式 (其表示正向迭代器) 的傳回類型。

## <a name="syntax"></a>語法

```cpp
struct forward_iterator_tag    : public input_iterator_tag {};
```

## <a name="remarks"></a>備註

分類標籤類別會用來當作演算法選擇的編譯標籤。 範本函式必須找出其迭代器引數最精確的分類，在編譯時間才能使用最有效率的演算法。 對於 `Iterator` 類型的每個迭代器，必須將 `iterator_traits`< `Iterator`>  **::iterator_category** 定義為描述迭代器行為最精確的分類標籤。

當 **Iter** 描述的物件可當作正向迭代器時，此類型與 **iterator**\< **Iter**>  **::iterator_category** 相同。

## <a name="example"></a>範例

如需如何使用 **iterator_tags** 的範例，請參閱 [iterator_traits](../standard-library/iterator-traits-struct.md) 或 [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md)。

## <a name="requirements"></a>需求

**標頭：** \<iterator>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[input_iterator_tag 結構](../standard-library/input-iterator-tag-struct.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)
