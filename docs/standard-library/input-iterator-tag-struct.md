---
title: input_iterator_tag 結構
ms.date: 11/04/2016
f1_keywords:
- xutility/std::input_iterator_tag
helpviewer_keywords:
- input_iterator_tag class
- input_iterator_tag struct
ms.assetid: ad68a4c6-f315-4ce1-8b74-c1fc71bd1577
ms.openlocfilehash: 47e0d08f79cfa41c414ac4fcd570ce8fdfbd0b35
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455322"
---
# <a name="input_iterator_tag-struct"></a>input_iterator_tag 結構

類別，為表示輸入反覆運算器的`iterator_category`函式提供傳回型別。

## <a name="syntax"></a>語法

結構 input_iterator_tag {};

## <a name="remarks"></a>備註

分類標籤類別會用來當作可供選取演算法的編譯標籤。 範本函式必須尋找其迭代器引數的最明確分類，如此它才能在編譯階段使用最有效率的演算法。 對於 `Iterator` 類型的每個迭代器，必須將 `iterator_traits`< `Iterator`>  **::iterator_category** 定義為描述迭代器行為最精確的分類標籤。

當描述可做為輸入反覆運算器的物件`Iter`時，此類型與**iterator** \< **Iter** >  **：： iterator_category**相同。

## <a name="example"></a>範例

如需如何使用`iterator_tag`的範例，請參閱[iterator_traits](../standard-library/iterator-traits-struct.md)或 [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md)。

## <a name="requirements"></a>需求

**標頭：** \<iterator>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)
