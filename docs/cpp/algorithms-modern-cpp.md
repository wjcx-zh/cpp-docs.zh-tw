---
title: "演算法 （現代 c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 6f758d3c-a7c7-4a50-92bb-97b2f6d4ab27
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5d89f6b5116459018cb50eb58b976f6f853ed088
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="algorithms-modern-c"></a>演算法 (現代 C++)
對於現代的 c + + 程式設計中，我們建議您使用中的演算法[c + + 標準程式庫](../standard-library/cpp-standard-library-reference.md)。 以下是一些重要的範例：  
  
-   `for_each`這是預設周遊演算法。 (也`transform`就地 not 語意。)  
  
-   `find_if`這是預設的搜尋演算法。  
  
-   `sort``lower_bound`，和其他預設排序和搜尋演算法。  
  
 若要撰寫比較子，使用 strict`<`並用*名為 lambda*時您可以。  
  
```cpp  
auto comp = [](const widget& w1, const widget& w2)  
      { return w1.weight() < w2.weight(); }  
  
sort( v.begin(), v.end(), comp );  
  
auto i = lower_bound( v.begin(), v.end(), comp );  
```  
  
## <a name="loops"></a>迴圈  
 可能的話，請使用範圍架構`for`迴圈或演算法的呼叫，或兩者，而不是手寫的迴圈。`copy`， `transform`， `count_if`， `remove_if`，和其他類似它們會遠高於手寫迴圈因為及其意圖很明顯讓您更輕鬆地撰寫無錯誤的程式碼。 此外，許多 c + + 標準程式庫演算法有實作最佳化，使它們更有效率。  
  
 而不是 c + + 舊像這樣：  
  
```cpp  
for ( auto i = strings.begin(); i != strings.end(); ++i ) {  
   /* ... */  
}  
  
auto i = v.begin();  
  
for ( ; i != v.end(); ++i ) {  
  if (*i > x && *i < y) break;  
}  
```  
  
 使用在現代 c + +，就像這樣：  
  
```cpp  
for_each( begin(strings), end(strings), [](string& s) {  
   // ...  
} );  
  
auto i = find_if( begin(v), end(v),  [=](int i) { return i > x && i < y; } );  
```  
  
### <a name="range-based-for-loops"></a>範圍架構的 for 迴圈  
 範圍架構`for`迴圈是 C + + 11 語言功能，不是 c + + 標準程式庫演算法。 但它點值得討論在本討論內容需迴圈。 範圍架構`for`迴圈是一種擴充的`for`關鍵字並提供方便且有效率的方式，來撰寫迴圈，逐一查看某個範圍的值。 C + + 標準程式庫容器、 字串和陣列是現成的範圍為基礎`for`迴圈。 若要啟用這種新的反覆項目語法適用於您的使用者定義類型，新增下列支援：  
  
-   A`begin`傳回結構開頭的迭代器的方法和`end`傳回結構結尾的迭代器的方法。  
  
-   中的迭代器，這些方法的支援： `operator*`， `operator!=`，和`operator++`（前置詞版）。  
  
 成員或獨立函式，可以使用這些方法。  
  
## <a name="random-numbers"></a>隨機數字  
 它是任何密碼，舊的 CRT`rand()`函式有許多的缺點，旨在討論 c + + 社群。 在現代 c + + 中，您不必處理這些缺點，也不需要來自創自己統一分佈亂數產生器，因為中所示，快速且輕鬆地建立這些工具都可以提供c++標準程式庫，[\<隨機 >](../standard-library/random.md)。  
  
## <a name="see-also"></a>請參閱  
 [歡迎回到 c + +](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C + + 語言參考](../cpp/cpp-language-reference.md)   
 [C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)