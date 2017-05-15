---
title: '&lt;iterator&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::<iterator>
- std.<iterator>
- <iterator>
- iterator/std::<iterator>
dev_langs:
- C++
helpviewer_keywords:
- iterator header
ms.assetid: c61a3962-f3ed-411a-b5a3-e8b3c2b500bd
caps.latest.revision: 27
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 67ba9e9a670ac187d15fe53729d8cdac475472ce
ms.contentlocale: zh-tw
ms.lasthandoff: 04/29/2017

---
# <a name="ltiteratorgt"></a>&lt;iterator&gt;
定義迭代器基本、預先定義的迭代器和串流迭代器，以及一些支援的範本。 預先定義的迭代器包含插入和反向配接器。 插入迭代器配接器有三個類別：前面、背面、一般。 它們提供插入語意，而不是覆寫語意 (由容器成員函式迭代器提供的)。  
  
## <a name="syntax"></a>語法  
  
```  
#include <iterator>  
  
```  
  
## <a name="remarks"></a>備註  
 迭代器是指標的一般化，擷取自其需求，以允許 C++ 程式以一致方式使用不同資料結構。 迭代器為容器和泛型演算法之間的媒介。 演算法是定義為在範圍 (由迭代器類型指定的) 上作業，而不是在特定資料類型上作業。 演算法可在滿足迭代器需求的任何資料結構上操作。 迭代器有五種類型或分類，每個都有自己的一組需求和產生的功能：  
  
-   輸出：向前移動，可以儲存但不會擷取值，由 ostream 和 inserter 提供。  
  
-   輸入：向前移動，可以擷取但不會儲存值，由 istream 提供。  
  
-   正向：向前移動，可以儲存和擷取值。  
  
-   雙向：向前向後移動，可以儲存和擷取值，由 list、set、multiset、map 和 multimap 提供。  
  
-   隨機存取：以任何順序存取項目，可以儲存和擷取值，由 vector、deque、string 和 array 提供。  
  
 具有更大的需求和更強大的項目存取權的迭代器，可取代較少需求的迭代器。 舉例來說，如果正向迭代器被呼叫，可改用隨機存取迭代器。  
  
 Visual Studio 已將擴充功能加入至 C++ Standard 程式庫迭代器，支援已檢查和未檢查迭代器的各種偵錯模式情況。 如需詳細資訊，請參閱[安全程式庫：C++ 標準程式庫](../standard-library/safe-libraries-cpp-standard-library.md)。  
  
### <a name="functions"></a>函式  
  
|||  
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
|[make_checked_array_iterator](../standard-library/iterator-functions.md#make_checked_array_iterator)|建立其他演算法可使用的 [checked_array_iterator](../standard-library/checked-array-iterator-class.md)。 **注意：**這個函式是「C++ 標準程式庫」的 Microsoft 擴充功能。 透過使用這個函式實作的程式碼不可移植到不支援此 Microsoft 擴充功能的 C++ Standard 建置環境。|  
|[make_move_iterator](../standard-library/iterator-functions.md#make_move_iterator)|傳回移動迭代器，其中包含所提供的迭代器，做為其儲存的基底迭代器。|  
|[make_unchecked_array_iterator](../standard-library/iterator-functions.md#make_unchecked_array_iterator)|建立其他演算法可使用的 [unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md)。 **注意：**這個函式是「C++ 標準程式庫」的 Microsoft 擴充功能。 透過使用這個函式實作的程式碼不可移植到不支援此 Microsoft 擴充功能的 C++ Standard 建置環境。|  
|[next](../standard-library/iterator-functions.md#next)|反覆運算指定的次數，並傳回新的迭代器位置。|  
|[prev](../standard-library/iterator-functions.md#prev)|以反向方向反覆運算指定的次數，並傳回新的迭代器位置。|  
  
### <a name="operators"></a>運算子  
  
|||  
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
  
|||  
|-|-|  
|[back_insert_iterator](../standard-library/back-insert-iterator-class.md)|此樣板類別描述輸出迭代器物件。 它會將元素插入到 **Container** 類型的容器中，其中會透過它所儲存的受保護 **pointer** 物件 (稱為容器) 來存取該容器。|  
|[bidirectional_iterator_tag](../standard-library/bidirectional-iterator-tag-struct.md)|一種類別，可為代表雙向迭代器的 **iterator_category** 函式提供傳回類型。|  
|[checked_array_iterator](../standard-library/checked-array-iterator-class.md)|類別，使用隨機存取、已檢查的迭代器來存取陣列。 **注意：**這個類別是「C++ 標準程式庫」的 Microsoft 擴充功能。 透過使用這個函式實作的程式碼不可移植到不支援此 Microsoft 擴充功能的 C++ Standard 建置環境。|  
|[forward_iterator_tag](../standard-library/forward-iterator-tag-struct.md)|一種類別，可為代表正向迭代器的 **iterator_category** 函式提供傳回類型。|  
|[front_insert_iterator](../standard-library/front-insert-iterator-class.md)|此樣板類別描述輸出迭代器物件。 它會將元素插入到 **Container** 類型的容器中，其中會透過它所儲存的受保護 **pointer** 物件 (稱為容器) 來存取該容器。|  
|[input_iterator_tag](../standard-library/input-iterator-tag-struct.md)|一種類別，可為代表輸入迭代器的 **iterator_category** 函式提供傳回類型。|  
|[insert_iterator](../standard-library/insert-iterator-class.md)|此樣板類別描述輸出迭代器物件。 它會將元素插入到 **Container** 類型的容器中，其中會透過它所儲存的受保護 **pointer** 物件 (稱為容器) 來存取該容器。 它也會儲存 **Container::iterator** 類別的受保護 **iterator** 物件 (稱為 **iter**)。|  
|[istream_iterator](../standard-library/istream-iterator-class.md)|此樣板類別描述輸入迭代器物件。 它會從輸入資料流擷取 **Ty** 類別的物件，其中會透過它所儲存的物件 (屬於 `basic_istream`\<**Elem**, **Tr**> 的 pointer 類型) 來存取該資料流。|  
|[istreambuf_iterator](../standard-library/istreambuf-iterator-class.md)|此樣板類別描述輸入迭代器物件。 它會將 **Elem** 類別的元素插入到輸出資料流緩衝區中，其中會透過它所儲存的物件 (屬於 `basic_streambuf`\<**Elem**, **Tr**> 的 **pointer** 類型) 來存取該緩衝區。|  
|[iterator](../standard-library/iterator-struct.md)|此樣板類別做為所有迭代器的基底類型。|  
|[iterator_traits](../standard-library/iterator-traits-struct.md)|樣板協助程式類別，提供與不同迭代器類型相關聯的關鍵類型，因此可以相同方式參考這些不同迭代器類型。|  
|[move_iterator](../standard-library/move-iterator-class.md)|`move_iterator` 物件儲存 `RandomIterator` 類型的隨機存取迭代器。 它的行為就像隨機存取迭代器 (除非取值時)。 `operator*` 的結果會隱含轉型為 `value_type&&:` 以建立 `rvalue reference`。|  
|[ostream_iterator](../standard-library/ostream-iterator-class.md)|此樣板類別描述輸出迭代器物件。 它會將 **Type** 類別的物件插入到輸出資料流中，其中會透過它所儲存的物件 (屬於 `basic_ostream`\<**Elem**, **Tr**> 的 **pointer** 類型) 來存取該資料流。|  
|[ostreambuf_iterator 類別](../standard-library/ostreambuf-iterator-class.md)|此樣板類別描述輸出迭代器物件。 它會將 **Elem** 類別的元素插入到輸出資料流緩衝區中，其中會透過它所儲存的物件 (屬於 `basic_streambuf`\<**Elem**, **Tr**> 的 pointer 類型) 來存取該緩衝區。|  
|[output_iterator_tag](../standard-library/output-iterator-tag-struct.md)|一種類別，可為代表輸出迭代器的 **iterator_category** 函式提供傳回類型。|  
|[random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md)|一種類別，可為代表隨機存取迭代器的 **iterator_category** 函式提供傳回類型。|  
|[reverse_iterator](../standard-library/reverse-iterator-class.md)|此樣板類別描述行為類似隨機存取迭代器，只不過是反向方向的物件。|  
|[unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md)|類別，使用隨機存取、未檢查的迭代器來存取陣列。 **注意：**這個類別是「C++ 標準程式庫」的 Microsoft 擴充功能。 透過使用這個函式實作的程式碼不可移植到不支援此 Microsoft 擴充功能的 C++ Standard 建置環境。|  
  
## <a name="see-also"></a>另請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)




