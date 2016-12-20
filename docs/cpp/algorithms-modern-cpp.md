---
title: "演算法 (現代 C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 6f758d3c-a7c7-4a50-92bb-97b2f6d4ab27
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 演算法 (現代 C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

對於現代 C\+\+ 程式設計，建議您使用[標準樣板程式庫](../standard-library/cpp-standard-library-reference.md) \(STL\) 中的演算法。  以列是一些重要的範例：  
  
-   `for_each`，這是預設周遊演算法。\(也是非原地語意的 `transform`。\)  
  
-   `find_if`，這是預設搜尋演算法。  
  
-   `sort`、`lower_bound` 和其他預設排序及搜尋演算法。  
  
 若要寫入比較子，盡可能使用嚴格的 `<` 並使用*具名 Lambda*。  
  
```cpp  
  
auto comp = [](const widget& w1, const widget& w2)  
      { return w1.weight() < w2.weight(); }  
  
sort( v.begin(), v.end(), comp );  
  
auto i = lower_bound( v.begin(), v.end(), comp );  
  
```  
  
## 迴圈  
 如果可能，請使用範圍架構的 `for` 迴圈或演算法呼叫或兩者都使用，而不是手寫的迴圈。  `copy`、`transform`、`count_if`、`remove_if` 和其他類似項目比手寫迴圈更適合，因為其目的明顯，而且更容易撰寫無 Bug 的程式碼。  此外，許多 STL 演算法有實作最佳化，因此更有效率。  
  
 而不是如下的舊版 C\+\+：  
  
```cpp  
  
for( auto i = strings.begin(); i != strings.end(); ++i ) {  
  :::  
  :::  
}  
  
auto i = v.begin();  
  
for( ; i != v.end(); ++i ) {  
  if (*i > x && *i < y) break;  
}  
  
```  
  
 使用像這樣的現代 C\+\+：  
  
```cpp  
  
for_each( begin(strings), end(strings), [](string& s) {  
  :::  
  :::  
} );  
auto i = find_if( begin(v), end(v),  [=](int i) { return i > x && i < y; }  );  
  
```  
  
### 迴圈的範圍架構  
 範圍架構的 `for` 迴圈是 C\+\+ 11 語言功能，而非 STL 演算法。  但在討論迴圈時有必要提及。  範圍架構的 `for` 迴圈是 `for` 關鍵字的擴充，提供便利且有效率的方式撰寫逐一查看值範圍的迴圈。  STL 容器、字串和陣列是現成可供範圍架構的 `for` 迴圈使用。  若要為您的使用者定義類型啟用這個新的反覆項目語法，請加入下列支援：  
  
-   傳回迭代器至結構開頭的 `end` 方法和傳回迭代器至結構結尾的 `begin` 方法。  
  
-   在迭代器中支援這些方法：`operator*`、`operator!=` 和 `operator++` \(前置版本\)。  
  
 這些方法可以是成員或獨立函式。  
  
## 亂數  
 眾所周知的是，舊版 CRT `rand()` 函式有許多缺點，這已在 C\+\+ 社群中完整討論。  在現代 C\+\+ 中，您不一定要處理這些缺點，也不需要自行發明一致分配亂數產生器，因為 STL 有輕鬆快速建立這些產生器的工具可用，如 [\<random\>](../standard-library/random.md) 所示。  
  
## 請參閱  
 [歡迎回到 C\+\+](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C\+\+ 語言參考](../cpp/cpp-language-reference.md)   
 [C\+\+ Standard Library](../standard-library/cpp-standard-library-reference.md)