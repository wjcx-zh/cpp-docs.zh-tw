---
title: "偵錯迭代器支援 | Microsoft Docs"
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
  - "_HAS_ITERATOR_DEBUGGING symbol"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "偵錯迭代器支援"
  - "不相容的迭代器"
  - "迭代器, 偵錯迭代器支援"
  - "迭代器, 不相容"
  - "安全程式庫"
  - "安全程式庫, Standard C++ 程式庫"
  - "安全 Standard C++ 程式庫"
  - "Standard C++ 程式庫, 偵錯迭代器支援"
ms.assetid: f3f5bd15-4be8-4d64-a4d0-8bc0761c68b6
caps.latest.revision: 22
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 偵錯迭代器支援
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 執行階段程式庫偵測到無效的 Iterator 用法，並判斷提示並顯示對話方塊在執行階段。  若要啟用偵錯 Iterator 支援，您必須使用 . C 執行階段程式庫偵錯版本編譯您的程式。  如需詳細資訊，請參閱[CRT 程式庫功能](../c-runtime-library/crt-library-features.md)。  如需如何使用 Iterator 的詳細資訊，請參閱 [已檢查的迭代器](../standard-library/checked-iterators.md)。  
  
 C\+\+ 標準描述成員函式如何可能造成 Iterator 到容器就會變成無效。  兩個範例如下:  
  
-   清除容器的項目造成 Iterator 對這個項目會變成無效。  
  
-   加入 [向量](../standard-library/vector.md) 的大小 \(推入或插入\) 會將 Iterator 的 `vector` 變成無效。  
  
## 範例  
 如果您編譯在偵錯模式的程式，執行階段會判斷提示和結束。  
  
```cpp  
/* compile with /EHsc /MDd */  
#include <vector>  
#include <iostream>  
  
int main() {  
   std::vector<int> v ;  
  
   v.push_back(10);  
   v.push_back(15);  
   v.push_back(20);  
  
   std::vector<int>::iterator i = v.begin();  
   ++i;  
  
   std::vector<int>::iterator j = v.end();  
   --j;  
  
   std::cout<<*j<<'\n';  
  
   v.insert(i,25);   
  
   std::cout<<*j<<'\n'; // Using an old iterator after an insert  
}  
  
```  
  
## 範例  
 您可以使用符號 [\_HAS\_ITERATOR\_DEBUGGING](../standard-library/has-iterator-debugging.md) 關閉在偵錯組建的 Iterator 偵錯功能。  下列程式不提示，，但仍觸發未定義的行為。  
  
> [!IMPORTANT]
>  使用 `_ITERATOR_DEBUG_LEVEL` 控制項的 `_HAS_ITERATOR_DEBUGGING`。  如需詳細資訊，請參閱[\_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md)。  
  
```cpp  
// iterator_debugging.cpp  
// compile with: /EHsc /MDd  
#define _HAS_ITERATOR_DEBUGGING 0  
#include <vector>  
#include <iostream>  
  
int main() {  
   std::vector<int> v ;  
  
   v.push_back(10);  
   v.push_back(15);  
   v.push_back(20);  
  
   std::vector<int>::iterator i = v.begin();  
   ++i;  
  
   std::vector<int>::iterator j = v.end();  
   --j;  
  
   std::cout<<*j<<'\n';  
  
   v.insert(i,25);   
  
   std::cout<<*j<<'\n'; // Using an old iterator after an insert  
}  
```  
  
  **20**  
**\-572662307**   
## 範例  
 判斷提示可能會發生，如果您嘗試使用 Iterator，在初始化之前，如下所示:  
  
```cpp  
/* compile with /EHsc /MDd */  
#include <string>  
using namespace std;  
int main() {  
   string::iterator i1, i2;  
   if (i1 == i2)  
      ;  
}  
```  
  
## 範例  
 因為對 [for\_each](../Topic/for_each.md) 演算法的兩個 Iterator 不相容，下列程式碼範例會產生判斷提示。  演算法檢查以確定提供給它們的 Iterator 是否參考相同的容器。  
  
```cpp  
/* compile with /EHsc /MDd */  
#include <algorithm>  
#include <vector>  
using namespace std;  
  
int main()  
{  
    vector<int> v1;  
    vector<int> v2;  
  
    v1.push_back(10);  
    v1.push_back(20);  
  
    v2.push_back(10);  
    v2.push_back(20);  
  
    // The next line will assert because v1 and v2 are  
    // incompatible.  
    for_each(v1.begin(), v2.end(), [] (int& elem) { elem *= 2; } );  
}  
```  
  
 請注意這個範例會使用 Lambda 運算式 `[] (int& elem) { elem *= 2; }` 而不是子功能。  雖然這個選項與無關判斷提示失敗的功能類似的工具會產生相同的失敗 Lambda 是非常有用的方式完成精簡函式物件工作。  如需 Lambda 運算式的詳細資訊，請參閱 [Lambda 運算式](../cpp/lambda-expressions-in-cpp.md)。  
  
## 範例  
 偵錯也已檢查的 Iterator 會導致 `for` 重複宣告超出範圍的 Iterator 變數，當 `for` 迴圈範圍的結尾。  
  
```cpp  
// debug_iterator.cpp  
// compile with: /EHsc /MDd  
#include <vector>  
#include <iostream>  
int main() {  
   std::vector<int> v ;  
  
   v.push_back(10);  
   v.push_back(15);  
   v.push_back(20);  
  
   for (std::vector<int>::iterator i = v.begin() ; i != v.end(); ++i)  
   ;  
   --i;   // C2065  
}  
```  
  
## 範例  
 偵錯 Iterator 有重要解構函式。  如果解構函式不會執行，無論原因為何，存取違規和資料損毀可能發生。  請考量以下範例：  
  
```cpp  
/* compile with: /EHsc /MDd */  
#include <vector>  
struct base {  
   // FIX: uncomment the next line  
   // virtual ~base() {}  
};  
  
struct derived : base {  
   std::vector<int>::iterator m_iter;  
   derived( std::vector<int>::iterator iter ) : m_iter( iter ) {}  
   ~derived() {}  
};  
  
int main() {  
   std::vector<int> vect( 10 );  
   base * pb = new derived( vect.begin() );  
   delete pb;  // doesn't call ~derived()  
   // access violation  
}  
```  
  
## 請參閱  
 [STL 概觀](../standard-library/cpp-standard-library-overview.md)