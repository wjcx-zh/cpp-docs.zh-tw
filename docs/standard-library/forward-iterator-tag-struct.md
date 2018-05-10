---
title: forward_iterator_tag 結構 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xutility/std::forward_iterator_tag
dev_langs:
- C++
helpviewer_keywords:
- forward_iterator_tag struct
- forward_iterator_tag class
ms.assetid: 68b633ac-b135-4e9e-837d-14248a262ec5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c0a618524fae49d8a5bfdb9ad945285e877d7cc
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="forwarditeratortag-struct"></a>forward_iterator_tag 結構

此類別可提供 **iterator_category** 函式 (其表示正向迭代器) 的傳回類型。

## <a name="syntax"></a>語法

```cpp
struct forward_iterator_tag    : public input_iterator_tag {};
```

## <a name="remarks"></a>備註

分類標籤類別會用來當作演算法選擇的編譯標籤。 範本函式必須找出其迭代器引數最精確的分類，在編譯時間才能使用最有效率的演算法。 對於 `Iterator` 類型的每個迭代器，必須將 `iterator_traits`< `Iterator`> **::iterator_category** 定義為描述迭代器行為最精確的分類標籤。

當 **Iter** 描述的物件可當作正向迭代器時，此類型與 **iterator**\< **Iter**> **::iterator_category** 相同。

## <a name="example"></a>範例

如需如何使用 **iterator_tags** 的範例，請參閱 [iterator_traits](../standard-library/iterator-traits-struct.md) 或 [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md)。

## <a name="requirements"></a>需求

**標頭：**\<iterator>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[input_iterator_tag 結構](../standard-library/input-iterator-tag-struct.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>
