---
title: Iterators | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- iterator conventions
- C++ Standard Library, iterator conventions
ms.assetid: 2f746be7-b37d-4bfc-bf05-be4336ca982f
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f03b62e045fe0130f981d55767c756df89bca9c6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="iterators"></a>迭代器
迭代器是一種物件，可逐一查看「C++ 標準程式庫」容器中的元素，並提供個別元素的存取途徑。 「C++ 標準程式庫」容器都有提供迭代器，因此演算法能以標準方式存取其元素，而不需要考慮元素儲存所在容器的類型。  
  
 您可以透過使用成員與全域函式 (例如 begin() 與 end()) 以及運算子 (例如 ++ 與 --) 來前後移動，以明確地使用迭代器。 您也可以搭配 range-for 迴圈或 (對於某些迭代器型別) 註標運算子 []，以隱含的方式使用迭代器。  
  
 在「C++ 標準程式庫」中，序列或範圍的開頭是第一個元素。 序列或範圍的結尾一律定義為最後一個元素之後的元素。 全域函式 begin 與 end 會將迭代器傳回到指定的容器。 一般明確迭代器會以迴圈方式處理容器中的所有元素，如下所示：  
  
```  
 
vector<int> vec{ 0,1,2,3,4 };  
for (auto it = begin(vec);

it != end(vec);

it++)  
{  // Access element using dereference operator
    cout <<*it <<" ";  
}  
```  
  
 使用 range-for 迴圈：  
  
```  
for (auto num : vec)  
 {  // no deference operator
    cout <<num <<" ";  
 }  
```  
  
 迭代器有五種分類。 為了增加能力，在這裡將分類為：  
  
- **輸出**。 輸出迭代器 `X` 可以透過使用 ++ 運算子逐一執行序列中的元素，而且可以使用 * 運算子只寫入一次元素。  
  
- **輸入**。 輸入迭代器 `X` 可以透過使用 ++ 運算子逐一執行序列中的元素，而且可以透過使用 * 運算子不限次數地讀取元素。 您可以透過使用 ++ 與 != 運算子來比較輸入迭代器。 遞增輸入迭代器的任何複本之後，就沒有其他複本可以安全地進行比較、取值 (Dereference) 或在以後遞增。  
  
- **正向**。 正向迭代器 `X` 可以使用 ++ 運算子來逐一執行序列，而且可以透過使用 * 運算子不限次數地讀取任何元素或寫入非常數元素。 您可以透過使用 -> 運算子來存取元素成員，以及透過使用 == 與 != 運算子來比較正向迭代器。 您可以建立正向迭代器的多個複本，每個都可以取值 (Dereference)，而且獨立遞增。 已初始化但未參考任何容器的正向迭代器稱為 Null 正向迭代器。 Null 正向迭代器一律會以相等方式比較。  
  
-   雙向。 雙向迭代器 `X` 可以取代正向迭代器。 不過，您也可以遞減雙向迭代器，如同 --`X`、`X`-- 或 (`V` = *`X`--)。 您可以使用與正向迭代器相同的方式來存取元素成員，以及比較雙向迭代器。  
  
- **隨機存取**。 隨機存取迭代器 `X` 可以取代雙向迭代器。 透過隨機存取迭代器，您可以使用註標運算子 [] 來存取元素。 您可以使用 +、-、+= 與 -= 運算子來向前或向後移動指定的元素數目，以及計算迭代器之間的距離。 您可以透過使用 ==、!=、\<、>、\<= 及 >= 來比較雙向迭代器。  
  
 所有迭代器可以指派或複製。 它們被假設為輕量級物件，通常依據值傳遞和傳回，而不是依據參考。 另請注意，當在有效的迭代器上執行時，上述的作業均無法擲回例外狀況。  
  
 可以藉由顯示三個序列來摘要迭代器分類的階層。 對於序列的唯寫存取，您可以使用任一項：  
  
```  
output iterator  
 -> forward iterator  
 -> bidirectional iterator  
 -> random-access iterator  
```  
  
 向右箭號表示「可以取代」。 舉例來說，任何需要輸出迭代器的演算法應該都可與正向迭代器妥善地搭配運作，但是反之則「不」然。  
  
 對於序列的唯讀存取，您可以使用任一項：  
  
```  
input iterator  
 -> forward iterator  
 -> bidirectional iterator  
 -> random-access iterator  
```  
  
 在此案例中，輸入迭代器是所有分類中最薄弱的。  
  
 最後，對於序列的讀取/寫入存取，您可以使用任一項：  
  
```  
forward iterator  
 -> bidirectional iterator  
 -> random-access iterator  
```  
  
 物件指標一律可以當做隨機存取迭代器，所以如果它對於指定的序列支援讀取/寫入存取，則可以做為任何分類的迭代器。  
  
 物件指標以外的迭代器 `Iterator` 也必須定義特製化 `iterator_traits<Iterator>` 所需的成員類型。 請注意，只要藉由從公用基底類別 [iterator](../standard-library/iterator-struct.md) 衍生 `Iterator`，即可符合這些需求。  
  
 請務必了解每個迭代器分類的承諾和限制，以了解「C++ 標準程式庫」中的容器和演算法如何使用迭代器。  
  
> [!NOTE]
>  您可以透過使用 range-for 迴圈來避免使用迭代器。 如需詳細資訊，請參閱[迴圈 (現代化 C++)](http://msdn.microsoft.com/en-us/b1b2779c-750e-4576-a514-a84178eae9da)。  
  
 Visual c + + 現在提供已檢查的迭代器和偵錯迭代器，以確保您不要覆寫容器的界限。 如需詳細資訊，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)和[偵錯迭代器支援](../standard-library/debug-iterator-support.md)。  
  
## <a name="see-also"></a>請參閱  
 [C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

