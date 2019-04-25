---
title: input_iterator_tag 結構
ms.date: 11/04/2016
f1_keywords:
- xutility/std::input_iterator_tag
helpviewer_keywords:
- input_iterator_tag class
- input_iterator_tag struct
ms.assetid: ad68a4c6-f315-4ce1-8b74-c1fc71bd1577
ms.openlocfilehash: 5478a8f9fa6013202a1ea8dd838eedb80b9c367e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159245"
---
# <a name="inputiteratortag-struct"></a>input_iterator_tag 結構

這個類別提供的傳回型別`iterator_category`代表輸入迭代器的函式。

## <a name="syntax"></a>語法

input_iterator_tag 結構{};

## <a name="remarks"></a>備註

分類標籤類別會用來當作可供選取演算法的編譯標籤。 範本函式必須尋找其迭代器引數的最明確分類，如此它才能在編譯階段使用最有效率的演算法。 對於 `Iterator` 類型的每個迭代器，必須將 `iterator_traits`< `Iterator`> **::iterator_category** 定義為描述迭代器行為最精確的分類標籤。

型別是相同**迭代器**\< **Iter**> **:: iterator_category**時`Iter`描述可以做為物件輸入迭代器。

## <a name="example"></a>範例

請參閱[iterator_traits](../standard-library/iterator-traits-struct.md)或是[random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md)如需如何使用的範例`iterator_tag`s。

## <a name="requirements"></a>需求

**標頭：**\<iterator>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>
