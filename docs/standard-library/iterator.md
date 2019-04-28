---
title: '&lt;iterator&gt;'
ms.date: 11/04/2016
f1_keywords:
- <iterator>
- iterator/std::<iterator>
helpviewer_keywords:
- iterator header
ms.assetid: c61a3962-f3ed-411a-b5a3-e8b3c2b500bd
ms.openlocfilehash: 1b0d3282075246f3b217f0c8acac19ed8ece79cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62224086"
---
# <a name="ltiteratorgt"></a>&lt;iterator&gt;

定義迭代器基本、預先定義的迭代器和串流迭代器，以及一些支援的範本。 預先定義的迭代器包含插入和反向配接器。 插入迭代器配接器有三個類別：前面、背面、一般。 它們提供插入語意，而不是覆寫語意 (由容器成員函式迭代器提供的)。

## <a name="syntax"></a>語法

```cpp
#include <iterator>
```

## <a name="remarks"></a>備註

迭代器是指標的一般化，擷取自其需求，以允許 C++ 程式以一致方式使用不同資料結構。 迭代器為容器和泛型演算法之間的媒介。 演算法是定義為在範圍 (由迭代器類型指定的) 上作業，而不是在特定資料類型上作業。 演算法可在滿足迭代器需求的任何資料結構上操作。 迭代器有五種類型或分類，每個都有自己的一組需求和產生的功能：

- 輸出：向前移動，可以儲存但不會擷取值，由 ostream 和 inserter 提供。

- 輸入：向前移動，可以擷取但不會儲存值，由 istream 提供。

- 正向：向前移動，可以儲存和擷取值。

- 雙向：向前向後移動，可以儲存和擷取值，由 list、set、multiset、map 和 multimap 提供。

- 隨機存取：以任何順序存取項目，可以儲存和擷取值，由 vector、deque、string 和 array 提供。

具有更大的需求和更強大的項目存取權的迭代器，可取代較少需求的迭代器。 舉例來說，如果正向迭代器被呼叫，可改用隨機存取迭代器。

Visual Studio 已將擴充功能加入至 C++ Standard 程式庫迭代器，支援已檢查和未檢查迭代器的各種偵錯模式情況。 如需詳細資訊，請參閱[安全程式庫：C++標準程式庫](../standard-library/safe-libraries-cpp-standard-library.md)。

### <a name="functions"></a>函式

|功能|描述|
|-|-|
|[advance](../standard-library/iterator-functions.md#advance)|依指定的位置數目遞增迭代器。|
|[back_inserter](../standard-library/iterator-functions.md#back_inserter)|建立可以在指定的容器背面插入項目的迭代器。|
|[begin](../standard-library/iterator-functions.md#begin)|擷取在指定的容器中第一個項目的迭代器。|
|[cbegin](../standard-library/iterator-functions.md#cbegin)|擷取在指定的容器中第一個項目的常數迭代器。|
|[cend](../standard-library/iterator-functions.md#cend)|擷取常數迭代器，指向在指定的容器中最後一個項目後面的項目。|
|[distance](../standard-library/iterator-functions.md#distance)|判斷在兩個迭代器定址的位置之間的增量數。|
|[end](../standard-library/iterator-functions.md#end)|擷取迭代器，指向在指定的容器中最後一個項目後面的項目。|
|[front_inserter](../standard-library/iterator-functions.md#front_inserter)|建立可以在指定的容器前面插入項目的迭代器。|
|[inserter](../standard-library/iterator-functions.md#inserter)|迭代器配接器，將新的項目新增至容器中指定的插入點。|
|[make_checked_array_iterator](../standard-library/iterator-functions.md#make_checked_array_iterator)|建立其他演算法可使用的 [checked_array_iterator](../standard-library/checked-array-iterator-class.md)。 **注意：** 這個函式是「C++ 標準程式庫」的 Microsoft 擴充功能。 透過使用這個函式實作的程式碼不可移植到不支援此 Microsoft 擴充功能的 C++ Standard 建置環境。|
|[make_move_iterator](../standard-library/iterator-functions.md#make_move_iterator)|傳回移動迭代器，其中包含所提供的迭代器，做為其儲存的基底迭代器。|
|[make_unchecked_array_iterator](../standard-library/iterator-functions.md#make_unchecked_array_iterator)|建立其他演算法可使用的 [unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md)。 **注意：** 這個函式是「C++ 標準程式庫」的 Microsoft 擴充功能。 透過使用這個函式實作的程式碼不可移植到不支援此 Microsoft 擴充功能的 C++ Standard 建置環境。|
|[next](../standard-library/iterator-functions.md#next)|反覆運算指定的次數，並傳回新的迭代器位置。|
|[prev](../standard-library/iterator-functions.md#prev)|以反向方向反覆運算指定的次數，並傳回新的迭代器位置。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator!=](../standard-library/iterator-operators.md#op_neq)|測試運算子左邊的迭代器物件是否不等於右邊的迭代器物件。|
|[operator==](../standard-library/iterator-operators.md#op_eq_eq)|測試運算子左邊的迭代器物件是否等於右邊的迭代器物件。|
|[operator<](../standard-library/iterator-operators.md#op_lt)|測試運算子左邊的迭代器物件是否小於右邊的迭代器物件。|
|[operator\<=](../standard-library/iterator-operators.md#op_gt_eq)|測試運算子左邊的迭代器物件是否小於或等於右邊的迭代器物件。|
|[operator>](../standard-library/iterator-operators.md#op_gt)|測試運算子左邊的迭代器物件是否大於右邊的迭代器物件。|
|[operator>=](../standard-library/iterator-operators.md#op_gt_eq)|測試運算子左邊的迭代器物件是否大於或等於右邊的迭代器物件。|
|[operator+](../standard-library/iterator-operators.md#op_add)|將位移新增至迭代器，並傳回新的 `reverse_iterator`，定址在新的位移位置中插入的項目。|
|[operator-](../standard-library/iterator-operators.md#operator-)|將一個迭代器減去另一個，並傳回差異。|

### <a name="classes"></a>類別

|類別|描述|
|-|-|
|[back_insert_iterator](../standard-library/back-insert-iterator-class.md)|此樣板類別描述輸出迭代器物件。 項目插入容器的型別`Container`，它會透過受保護存取的`pointer`它所儲存的物件稱為容器。|
|[bidirectional_iterator_tag](../standard-library/bidirectional-iterator-tag-struct.md)|這個類別提供的傳回型別`iterator_category`表示雙向迭代器函式。|
|[checked_array_iterator](../standard-library/checked-array-iterator-class.md)|類別，使用隨機存取、已檢查的迭代器來存取陣列。 **注意：** 這個類別是 C++ 標準程式庫的 Microsoft 擴充功能。 透過使用這個函式實作的程式碼不可移植到不支援此 Microsoft 擴充功能的 C++ Standard 建置環境。|
|[forward_iterator_tag](../standard-library/forward-iterator-tag-struct.md)|這個類別提供的傳回型別`iterator_category`代表正向迭代器的函式。|
|[front_insert_iterator](../standard-library/front-insert-iterator-class.md)|此樣板類別描述輸出迭代器物件。 項目插入容器的型別`Container`，它會透過受保護存取的`pointer`它所儲存的物件稱為容器。|
|[input_iterator_tag](../standard-library/input-iterator-tag-struct.md)|這個類別提供的傳回型別`iterator_category`代表輸入迭代器的函式。|
|[insert_iterator](../standard-library/insert-iterator-class.md)|此樣板類別描述輸出迭代器物件。 項目插入容器的型別`Container`，它會透過受保護存取的`pointer`它所儲存的物件稱為容器。 它也會儲存受保護`iterator`類別的物件`Container::iterator`稱為`iter`。|
|[istream_iterator](../standard-library/istream-iterator-class.md)|此樣板類別描述輸入迭代器物件。 它會擷取類別的物件`Ty`它會透過它所儲存之類型指標的物件存取輸入資料流`basic_istream` \< **Elem**， **Tr**>。|
|[istreambuf_iterator](../standard-library/istreambuf-iterator-class.md)|此樣板類別描述輸入迭代器物件。 它會插入項目類別的`Elem`輸出資料流緩衝區中，存取物件透過其儲存的型別`pointer`要`basic_streambuf` \< **Elem**， **Tr**>。|
|[iterator](../standard-library/iterator-struct.md)|此樣板類別做為所有迭代器的基底類型。|
|[iterator_traits](../standard-library/iterator-traits-struct.md)|樣板協助程式類別，提供與不同迭代器類型相關聯的關鍵類型，因此可以相同方式參考這些不同迭代器類型。|
|[move_iterator](../standard-library/move-iterator-class.md)|`move_iterator` 物件儲存 `RandomIterator` 類型的隨機存取迭代器。 它的行為就像隨機存取迭代器 (除非取值時)。 `operator*` 的結果會隱含轉型為 `value_type&&:` 以建立 `rvalue reference`。|
|[ostream_iterator](../standard-library/ostream-iterator-class.md)|此樣板類別描述輸出迭代器物件。 它會插入類別的物件`Type`輸出資料流中，存取物件透過其儲存的型別`pointer`要`basic_ostream` \< **Elem**， **Tr**>。|
|[ostreambuf_iterator 類別](../standard-library/ostreambuf-iterator-class.md)|此樣板類別描述輸出迭代器物件。 它會插入類別的元素`Elem`輸出資料流緩衝區，它會透過它所儲存之類型指標的物件存取這`basic_streambuf` \< **Elem**， **Tr**>。|
|[output_iterator_tag](../standard-library/output-iterator-tag-struct.md)|這個類別提供的傳回型別`iterator_category`表示輸出迭代器函式。|
|[random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md)|這個類別提供的傳回型別`iterator_category`表示隨機存取迭代器函式。|
|[reverse_iterator](../standard-library/reverse-iterator-class.md)|此樣板類別描述行為類似隨機存取迭代器，只不過是反向方向的物件。|
|[unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md)|類別，使用隨機存取、未檢查的迭代器來存取陣列。 **注意：** 這個類別是 C++ 標準程式庫的 Microsoft 擴充功能。 透過使用這個函式實作的程式碼不可移植到不支援此 Microsoft 擴充功能的 C++ Standard 建置環境。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>
