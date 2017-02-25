---
title: "&lt;iterator&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::<iterator>"
  - "std.<iterator>"
  - "<iterator>"
  - "iterator/std::<iterator>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "iterator 標頭"
ms.assetid: c61a3962-f3ed-411a-b5a3-e8b3c2b500bd
caps.latest.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 27
---
# &lt;iterator&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義迭代器基本、預先定義的迭代器和串流迭代器，以及一些支援的範本。  預先定義的迭代器包含插入和反向配接器。  插入迭代器配接器有三個類別：前面、背面、一般。  它們提供插入語意，而不是覆寫語意 \(由容器成員函式迭代器提供的\)。  
  
## 語法  
  
```  
  
#include <iterator>  
  
```  
  
## 備註  
 迭代器是指標的一般化，擷取自其需求，以允許 C\+\+ 程式以一致方式使用不同資料結構。  迭代器為容器和泛型演算法之間的媒介。  演算法是定義為在範圍 \(由迭代器類型指定的\) 上作業，而不是在特定資料類型上作業。  演算法可在滿足迭代器需求的任何資料結構上操作。  迭代器有五種類型或分類，每個都有自己的一組需求和產生的功能：  
  
-   輸出：向前移動，可以儲存但不會擷取值，由 ostream 和 inserter 提供。  
  
-   輸入：向前移動，可以擷取但不會儲存值，由 istream 提供。  
  
-   正向：向前移動，可以儲存和擷取值。  
  
-   雙向：向前向後移動，可以儲存和擷取值，由 list、set、multiset、map 和 multimap 提供。  
  
-   隨機存取：以任何順序存取項目，可以儲存和擷取值，由 vector、deque、string 和 array 提供。  
  
 具有更大的需求和更強大的項目存取權的迭代器，可取代較少需求的迭代器。  舉例來說，如果正向迭代器被呼叫，可改用隨機存取迭代器。  
  
 Visual Studio 已將擴充功能加入至 C\+\+ Standard 程式庫迭代器，支援已檢查和未檢查迭代器的各種偵錯模式情況。  如需詳細資訊，請參閱[安全程式庫：C\+\+ 標準程式庫](../standard-library/safe-libraries-cpp-standard-library.md)。  
  
### 函式  
  
|||  
|-|-|  
|[advance](../Topic/advance.md)|依指定的位置數目遞增迭代器。|  
|[back\_inserter](../Topic/back_inserter.md)|建立可以在指定的容器背面插入項目的迭代器。|  
|[begin](../Topic/begin.md)|擷取在指定的容器中第一個項目的迭代器。|  
|[cbegin](../Topic/cbegin.md)|擷取在指定的容器中第一個項目的常數迭代器。|  
|[cend](../Topic/cend.md)|擷取常數迭代器，指向在指定的容器中最後一個項目後面的項目。|  
|[distance](../Topic/distance.md)|判斷在兩個迭代器定址的位置之間的增量數。|  
|[end](../Topic/end.md)|擷取迭代器，指向在指定的容器中最後一個項目後面的項目。|  
|[front\_inserter](../Topic/front_inserter.md)|建立可以在指定的容器前面插入項目的迭代器。|  
|[inserter](../Topic/inserter.md)|迭代器配接器，將新的項目新增至容器中指定的插入點。|  
|[make\_checked\_array\_iterator](../Topic/make_checked_array_iterator.md)|建立其他演算法可使用的 [checked\_array\_iterator](../standard-library/checked-array-iterator-class.md)。 **Note:**  這個函式是 Standard C\+\+ 程式庫的 Microsoft 擴充功能。  透過使用這個函式實作的程式碼不可移植到不支援此 Microsoft 擴充功能的 C\+\+ Standard 建置環境。|  
|[make\_move\_iterator](../Topic/make_move_iterator.md)|傳回移動迭代器，其中包含所提供的迭代器，做為其儲存的基底迭代器。|  
|[make\_unchecked\_array\_iterator](../Topic/make_unchecked_array_iterator.md)|建立其他演算法可使用的 [unchecked\_array\_iterator](../standard-library/unchecked-array-iterator-class.md)。 **Note:**  這個函式是 Standard C\+\+ 程式庫的 Microsoft 擴充功能。  透過使用這個函式實作的程式碼不可移植到不支援此 Microsoft 擴充功能的 C\+\+ Standard 建置環境。|  
|[next](../Topic/next.md)|反覆運算指定的次數，並傳回新的迭代器位置。|  
|[prev](../Topic/prev.md)|以反向方向反覆運算指定的次數，並傳回新的迭代器位置。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\!\=](../Topic/operator!=%20\(%3Citerator%3E\).md)|測試運算子左邊的迭代器物件是否不等於右邊的迭代器物件。|  
|[operator\=\=](../Topic/operator==%20\(%3Citerator%3E\).md)|測試運算子左邊的迭代器物件是否等於右邊的迭代器物件。|  
|[運算子\<](../Topic/operator%3C%20\(%3Citerator%3E\).md)|測試運算子左邊的迭代器物件是否小於右邊的迭代器物件。|  
|[operator\<\=](../Topic/operator%3C=%20\(%3Citerator%3E\).md)|測試運算子左邊的迭代器物件是否小於或等於右邊的迭代器物件。|  
|[運算子\>](../Topic/operator%3E%20\(%3Citerator%3E\).md)|測試運算子左邊的迭代器物件是否大於右邊的迭代器物件。|  
|[operator\>\=](../Topic/operator%3E=%20\(%3Citerator%3E\).md)|測試運算子左邊的迭代器物件是否大於或等於右邊的迭代器物件。|  
|[operator\+](../Topic/operator+%20\(%3Citerator%3E\).md)|將位移新增至迭代器，並傳回新的 `reverse_iterator`，定址在新的位移位置中插入的項目。|  
|[operator\-](../Topic/operator-%20\(%3Citerator%3E\).md)|將一個迭代器減去另一個，並傳回差異。|  
  
### 類別  
  
|||  
|-|-|  
|[back\_insert\_iterator](../standard-library/back-insert-iterator-class.md)|此樣板類別描述輸出迭代器物件。  它將項目插入 **Container** 類型容器中，並透過它所儲存受保護的 **pointer** 物件 \(稱為容器\) 存取項目。|  
|[bidirectional\_iterator\_tag](../standard-library/bidirectional-iterator-tag-struct.md)|類別，為表示雙向迭代器的 **iterator\_category** 函式提供傳回類型。|  
|[checked\_array\_iterator](../standard-library/checked-array-iterator-class.md)|類別，使用隨機存取、已檢查的迭代器來存取陣列。 **Note:**  這個類別是 Standard C\+\+ 程式庫的 Microsoft 擴充功能。  透過使用這個函式實作的程式碼不可移植到不支援此 Microsoft 擴充功能的 C\+\+ Standard 建置環境。|  
|[forward\_iterator\_tag](../standard-library/forward-iterator-tag-struct.md)|類別，為表示正向迭代器的 **iterator\_category** 函式提供傳回類型。|  
|[front\_insert\_iterator](../standard-library/front-insert-iterator-class.md)|此樣板類別描述輸出迭代器物件。  它將項目插入 **Container** 類型容器中，並透過它所儲存受保護的 **pointer** 物件 \(稱為容器\) 存取項目。|  
|[input\_iterator\_tag](../standard-library/input-iterator-tag-struct.md)|類別，為表示輸入迭代器的 **iterator\_category** 函式提供傳回類型。|  
|[insert\_iterator](../standard-library/insert-iterator-class.md)|此樣板類別描述輸出迭代器物件。  它將項目插入 **Container** 類型容器中，並透過它所儲存受保護的 **pointer** 物件 \(稱為容器\) 存取項目。  它也會儲存受保護的 **iterator** 物件，物件屬於類別 **Container::iterator**，稱為 **iter**。|  
|[istream\_iterator](../standard-library/istream-iterator-class.md)|此樣板類別描述輸入迭代器物件。  它從輸入資料流擷取 **Ty** 類別的物件，並透過它所儲存的物件 \(屬於 `basic_istream`\<**Elem**, **Tr**\> 的 pointer 類型\) 存取。|  
|[istreambuf\_iterator](../standard-library/istreambuf-iterator-class.md)|此樣板類別描述輸入迭代器物件。  它將類別 **Elem** 的項目插入輸出資料流緩衝區中，並透過它所儲存的物件 \(屬於 `basic_streambuf`\<**Elem**, **Tr**\> 的 **pointer** 類型\) 存取項目。|  
|[iterator](../standard-library/iterator-struct.md)|此樣板類別做為所有迭代器的基底類型。|  
|[iterator\_traits](../standard-library/iterator-traits-struct.md)|樣板協助程式類別，提供與不同迭代器類型相關聯的關鍵類型，因此可以相同方式參考這些不同迭代器類型。|  
|[move\_iterator](../standard-library/move-iterator-class.md)|`move_iterator` 物件儲存 `RandomIterator` 類型的隨機存取迭代器。  它的行為就像隨機存取迭代器 \(除非取值時\)。  `operator*` 的結果會隱含轉型為 `value_type&&:` 以建立 `rvalue reference`。|  
|[ostream\_iterator](../standard-library/ostream-iterator-class.md)|此樣板類別描述輸出迭代器物件。  它將 **Type** 類別的物件插入輸出資料流中，並透過它所儲存的物件 \(屬於 `basic_ostream`\<**Elem**, **Tr**\> 的 **pointer** 類型\) 存取。|  
|[ostreambuf\_iterator 類別](../standard-library/ostreambuf-iterator-class.md)|此樣板類別描述輸出迭代器物件。  它將類別 **Elem** 的項目插入輸出資料流緩衝區中，並透過它所儲存的物件 \(屬於 `basic_streambuf`\<**Elem**, **Tr**\> 的 pointer 類型\) 存取項目。|  
|[output\_iterator\_tag](../standard-library/output-iterator-tag-struct.md)|類別，為表示輸出迭代器的 **iterator\_category** 函式提供傳回類型。|  
|[random\_access\_iterator\_tag](../standard-library/random-access-iterator-tag-struct.md)|類別，為表示隨機存取的 **iterator\_category** 函式提供傳回類型。|  
|[reverse\_iterator](../standard-library/reverse-iterator-class.md)|此樣板類別描述行為類似隨機存取迭代器，只不過是反向方向的物件。|  
|[unchecked\_array\_iterator](../standard-library/unchecked-array-iterator-class.md)|類別，使用隨機存取、未檢查的迭代器來存取陣列。 **Note:**  這個類別是 Standard C\+\+ 程式庫的 Microsoft 擴充功能。  透過使用這個函式實作的程式碼不可移植到不支援此 Microsoft 擴充功能的 C\+\+ Standard 建置環境。|  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)