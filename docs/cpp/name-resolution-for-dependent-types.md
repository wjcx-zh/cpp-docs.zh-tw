---
title: "相依類型的名稱解析 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
ms.assetid: 34066bb4-0c79-4fd8-bda7-539a60a277ab
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5d8978e38745f088884bbf28ffb0ab98cfb87895
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="name-resolution-for-dependent-types"></a>相依類型的名稱解析
使用**typename**在給定的限定的名稱識別的類型會告訴編譯器樣板定義中的限定名稱。 如需詳細資訊，請參閱[typename](../cpp/typename.md)。  
  
```cpp  
// template_name_resolution1.cpp  
#include <stdio.h>  
template <class T> class X  
{  
public:  
   void f(typename T::myType* mt) {}  
};  
  
class Yarg  
{  
public:  
   struct myType { };  
};  
  
int main()  
{  
   X<Yarg> x;  
   x.f(new Yarg::myType());  
   printf("Name resolved by using typename keyword.");  
}  
```  
  
```Output  
Name resolved by using typename keyword.  
```  
  
 相依名稱的名稱查閱會檢查從樣板定義內容的名稱，這個內容會在下列範例中，尋找`myFunction(char)`— 和樣板具現化的內容。在下列範例中，樣板具現化在 main 中因此，`MyNamespace::myFunction`是可見的具現化的點，並且可挑選為較佳的相符項目。 如果 `MyNamespace::myFunction` 已重新命名，則會改為呼叫 `myFunction(char)`。  
  
 所有名稱都會做為相依名稱解析。 儘管如此，如果可能發生任何衝突，仍建議您使用完整限定名稱。  
  
```cpp  
// template_name_resolution2.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
void myFunction(char)  
{  
   cout << "Char myFunction" << endl;  
}  
  
template <class T> class Class1  
{  
public:  
   Class1(T i)  
   {  
      // If replaced with myFunction(1), myFunction(char)  
      // will be called  
      myFunction(i);  
}  
};  
  
namespace MyNamespace  
{  
   void myFunction(int)  
   {  
      cout << "Int MyNamespace::myFunction" << endl;  
   }  
};  
  
using namespace MyNamespace;  
  
int main()  
{  
   Class1<int>* c1 = new Class1<int>(100);  
}  
```  
  
### <a name="output"></a>輸出  
  
```  
Int MyNamespace::myFunction  
```  
  
### <a name="template-disambiguation"></a>樣板去除混淆  
 [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] 會強制執行 C++98/03/11 標準規則，以便釐清 "template" 關鍵字。 在下列範例中，Visual c + + 2010年會接受的不一致的程式行及合格的行。  [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)]接受只有合格的線條。  
  
```cpp  
#include <iostream>  
#include <ostream>  
#include <typeinfo>  
using namespace std;  
  
template <typename T> struct Allocator {  
    template <typename U> struct Rebind {  
        typedef Allocator<U> Other;  
    };  
};  
  
template <typename X, typename AY> struct Container {  
    #if defined(NONCONFORMANT)  
        typedef typename AY::Rebind<X>::Other AX; // nonconformant  
    #elif defined(CONFORMANT)  
        typedef typename AY::template Rebind<X>::Other AX; // conformant  
    #else  
        #error Define NONCONFORMANT or CONFORMANT.  
    #endif  
};  
  
int main() {  
    cout << typeid(Container<int, Allocator<float>>::AX).name() << endl;  
}  
```  
  
 遵循去除混淆規則是必要條件，因為根據預設，C++ 會假設 `AY::Rebind` 不是樣板，因此編譯器會將下列 "`<`" 解譯為小於。 編譯器必須知道 `Rebind` 是樣板，才能將 "`<`" 正確剖析為角括號。  
  
## <a name="see-also"></a>請參閱  
 [名稱解析](../cpp/templates-and-name-resolution.md)