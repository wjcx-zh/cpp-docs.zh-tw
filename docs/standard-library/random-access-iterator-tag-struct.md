---
title: "random_access_iterator_tag 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "xutility/std::random_access_iterator_tag"
  - "random_access_iterator_tag"
  - "std.random_access_iterator_tag"
  - "std::random_access_iterator_tag"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "random_access_iterator_tag 類別"
  - "random_access_iterator_tag 結構"
ms.assetid: 59f5b741-c5b4-459c-ad0a-3b67cddeea23
caps.latest.revision: 23
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# random_access_iterator_tag 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

提供傳回類別的類型**迭代器類別** 表示隨機存取的函式。  
  
## 語法  
  
```  
  
   struct random_access_iterator_tag  
: public bidirectional_iterator_tag {};  
```  
  
## 備註  
 類別將類別標記為演算法選取使用編譯標記。  樣板函式需要尋找其 Iterator 引數最特定的類別，以便使用最有效的演算法在編譯時期。  對於型別 `Iterator`Iterator，必須定義 `iterator_traits`\<`Iterator`\>**::iterator\_category** 是描述 Iterator 的行為的最特定的分類標記。  
  
 這個型別與 **iterator**\<**Iter**\>**::iterator\_category** ，當 **Iter** 描述可做為隨機存取 Iterator 的物件時。  
  
## 範例  
  
```  
// iterator_rait.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
#include <list>  
  
using namespace std;  
  
int main( )  
{  
   vector<int> vi;  
   vector<char> vc;  
   list<char> lc;  
   iterator_traits<vector<int>:: iterator>::iterator_category cati;  
   iterator_traits<vector<char>:: iterator>::iterator_category catc;  
   iterator_traits<list<char>:: iterator>::iterator_category catlc;  
  
   // These are both random-access iterators  
   cout << "The type of iterator for vector<int> is "  
       << "identified by the tag:\n "   
       << typeid ( cati ).name( ) << endl;  
   cout << "The type of iterator for vector<char> is "  
       << "identified by the tag:\n "   
       << typeid ( catc ).name( ) << endl;  
   if ( typeid ( cati ) == typeid( catc ) )  
      cout << "The iterators are the same." << endl << endl;  
   else  
      cout << "The iterators are not the same." << endl << endl;  
  
   // But the list iterator is bidirectinal, not random access  
   cout << "The type of iterator for list<char> is "  
       << "identified by the tag:\n "   
       << typeid (catlc).name( ) << endl;  
  
   // cout << ( typeid ( vi.begin( ) ) == typeid( vc.begin( ) ) ) << endl;  
   if ( typeid ( vi.begin( ) ) == typeid( vc.begin( ) ) )  
      cout << "The iterators are the same." << endl;  
   else  
      cout << "The iterators are not the same." << endl;  
   // A random-access iterator is a bidirectional iterator.  
   cout << ( void* ) dynamic_cast< iterator_traits<list<char>:: iterator>  
          ::iterator_category* > ( &catc ) << endl;  
}  
```  
  
## 範例輸出  
 以下輸出\(x86\)。  
  
```  
The type of iterator for vector<int> is identified by the tag:  
 struct std::random_access_iterator_tag  
The type of iterator for vector<char> is identified by the tag:  
 struct std::random_access_iterator_tag  
The iterators are the same.  
  
The type of iterator for list<char> is identified by the tag:  
 struct std::bidirectional_iterator_tag  
The iterators are not the same.  
0012FF3B  
```  
  
## 需求  
 **標頭：**\<迭代器\>  
  
 **命名空間:** std  
  
## 請參閱  
 [bidirectional\_iterator\_tag 結構](../standard-library/bidirectional-iterator-tag-struct.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)