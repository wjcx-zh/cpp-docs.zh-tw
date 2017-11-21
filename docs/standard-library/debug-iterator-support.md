---
title: "偵錯迭代器支援 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Safe Libraries
- Safe Libraries, C++ Standard Library
- Safe C++ Standard Library
- C++ Standard Library, debug iterator support
- iterators, debug iterator support
- iterators, incompatible
- incompatible iterators
- debug iterator support
ms.assetid: f3f5bd15-4be8-4d64-a4d0-8bc0761c68b6
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c0c2f0153d216292169b72e3e75d5d40fb5f35cf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="debug-iterator-support"></a>Debug Iterator Support
Visual C++ 執行階段程式庫可在執行階段偵測不正確的迭代器用法、進行判斷提示並顯示對話方塊。 若要啟用偵錯迭代器支援，您必須使用 C++ 標準程式庫和 C 執行階段程式庫的偵錯版本來編譯您的程式。 如需詳細資訊，請參閱 [CRT 程式庫功能](../c-runtime-library/crt-library-features.md)。 如需如何使用已檢查的迭代器的資訊，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。  
  
 C++ 標準說明為何成員函式可能會導致容器的迭代器變成無效。 以下為兩個範例：  
  
-   從容器清除元素時，會導致迭代器的元素變成無效。  
  
-   使用 push 或 insert 增加[向量](../standard-library/vector.md)的大小時，會導致 `vector` 內的迭代器變成無效。  
  
## <a name="example"></a>範例  
如果您在偵錯模式中編譯此範例程式，程式就會在執行階段進行判斷提示並終止。  
  
```cpp  
// iterator_debugging_0.cpp  
// compile by using /EHsc /MDd  
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
  
   std::cout << *j << '\n';  
  
   v.insert(i,25);   
  
   std::cout << *j << '\n'; // Using an old iterator after an insert  
}  
```  
  
## <a name="example"></a>範例  
您可以使用前置處理器巨集 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)，來關閉偵錯組建中的迭代器偵錯功能。 這個程式不會進行判斷提示，但仍會觸發未定義的行為。  
  
```cpp  
// iterator_debugging_1.cpp  
// compile by using: /EHsc /MDd  
#define _ITERATOR_DEBUG_LEVEL 0  
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
  
   std::cout << *j << '\n';  
  
   v.insert(i,25);   
  
   std::cout << *j << '\n'; // Using an old iterator after an insert  
}  
```  
  
```Output  
20  
-572662307  
```  
  
## <a name="example"></a>範例  
如果您嘗試在迭代器初始化之前就加以使用，也會發生如下的判斷提示：  
  
```cpp  
// iterator_debugging_2.cpp  
// compile by using: /EHsc /MDd  
#include <string>  
using namespace std;  
  
int main() {  
   string::iterator i1, i2;  
   if (i1 == i2)  
      ;  
}  
```  
  
## <a name="example"></a>範例  
下列程式碼範例會引起判斷提示，因為針對 [for_each](../standard-library/algorithm-functions.md#for_each) 演算法提供的兩個迭代器不相容。 演算法會檢查並判斷會提供給它們的迭代器是否參考相同的容器。  
  
```cpp  
// iterator_debugging_3.cpp  
// compile by using /EHsc /MDd  
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
  
    // The next line asserts because v1 and v2 are  
    // incompatible.  
    for_each(v1.begin(), v2.end(), [] (int& elem) { elem *= 2; } );  
}  
```  
  
請注意，此範例中使用 Lambda 運算式`[] (int& elem) { elem *= 2; }` 而不是仿函式。 雖然這種選擇與判斷提示失敗無關 (類似的仿函式會導致相同的失敗)，但 Lambda 非常適合用來完成精簡函式物件的工作。 如需 Lambda 運算式的詳細資訊，請參閱 [Lambda 運算式](../cpp/lambda-expressions-in-cpp.md)。  
  
## <a name="example"></a>範例  
當 `for` 迴圈範圍結束時，偵錯迭代器的檢查也會導致 `for` 迴圈中宣告的迭代器變數超出範圍。  
  
```cpp  
// iterator_debugging_4.cpp  
// compile by using: /EHsc /MDd  
#include <vector>  
#include <iostream>  
int main() {  
   std::vector<int> v ;  
  
   v.push_back(10);  
   v.push_back(15);  
   v.push_back(20);  
  
   for (std::vector<int>::iterator i = v.begin(); i != v.end(); ++i)  
      ;   // do nothing  
   --i;   // C2065  
}  
```  
  
## <a name="example"></a>範例  
偵錯迭代器具有非一般的解構函式。 如果解構函式因任何原因並未執行，即可能發生存取違規與資料損毀情況。 請考量以下範例：  
  
```cpp  
// iterator_debugging_5.cpp  
// compile by using: /EHsc /MDd  
#include <vector>  
struct base {  
   // TO FIX: uncomment the next line  
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
  
## <a name="see-also"></a>另請參閱  
[C++ 標準程式庫概觀](../standard-library/cpp-standard-library-overview.md)




