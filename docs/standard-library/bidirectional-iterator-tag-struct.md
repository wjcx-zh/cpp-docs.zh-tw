---
title: bidirectional_iterator_tag 結構
ms.date: 11/04/2016
f1_keywords:
- xutility/std::bidirectional_iterator_tag
helpviewer_keywords:
- bidirectional_iterator_tag class
- bidirectional_iterator_tag struct
ms.assetid: 9ac06066-b8ae-44b6-bee4-b05855f6a31a
ms.openlocfilehash: c8296ddf30c0e2a3d34e69cbf079c0477e0e8b7a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62414072"
---
# <a name="bidirectionaliteratortag-struct"></a>bidirectional_iterator_tag 結構

這個類別提供的傳回型別`iterator_category`表示雙向迭代器函式。

## <a name="syntax"></a>語法

```cpp
struct bidirectional_iterator_tag    : public forward_iterator_tag {};
```

## <a name="remarks"></a>備註

分類標籤類別會用作演算法選擇的編譯標籤。 樣板函式必須尋找其迭代器引數最精確的分類，如此一來在編譯時間就可以使用最有效率的演算法。 對於 `Iterator` 類型的每個迭代器，必須將 `iterator_traits`< `Iterator`>:: **iterator_category** 定義為描述迭代器行為最精確的分類標籤。

型別是相同**迭代器**\< **Iter**>:: **iterator_category**時`Iter`描述可以做為雙向的物件迭代器。

## <a name="example"></a>範例

如需如何使用 `bidirectional_iterator_tag` 的範例，請參閱 [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md)。

## <a name="requirements"></a>需求

**標頭：**\<iterator>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[forward_iterator_tag 結構](../standard-library/forward-iterator-tag-struct.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>
