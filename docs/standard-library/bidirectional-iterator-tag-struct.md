---
title: bidirectional_iterator_tag 結構 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xutility/std::bidirectional_iterator_tag
dev_langs:
- C++
helpviewer_keywords:
- bidirectional_iterator_tag class
- bidirectional_iterator_tag struct
ms.assetid: 9ac06066-b8ae-44b6-bee4-b05855f6a31a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 108397f6c3c3c088839230f2b48b505300149345
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="bidirectionaliteratortag-struct"></a>bidirectional_iterator_tag 結構

類別，為表示雙向迭代器的 **iterator_category** 函式提供傳回型別。

## <a name="syntax"></a>語法

```cpp
struct bidirectional_iterator_tag    : public forward_iterator_tag {};
```

## <a name="remarks"></a>備註

分類標籤類別會用作演算法選擇的編譯標籤。 樣板函式必須尋找其迭代器引數最精確的分類，如此一來在編譯時間就可以使用最有效率的演算法。 對於 `Iterator` 類型的每個迭代器，必須將 `iterator_traits`< `Iterator`>:: **iterator_category** 定義為描述迭代器行為最精確的分類標籤。

當 **Iter** 描述的物件可當作雙向迭代器時，此類型與 **iterator**\< **Iter**>:: **iterator_category** 相同。

## <a name="example"></a>範例

如需如何使用 `bidirectional_iterator_tag` 的範例，請參閱 [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md)。

## <a name="requirements"></a>需求

**標頭：**\<iterator>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[forward_iterator_tag 結構](../standard-library/forward-iterator-tag-struct.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>
