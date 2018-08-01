---
title: __if_exists 陳述式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __if_exists_cpp
dev_langs:
- C++
helpviewer_keywords:
- identifiers, testing for existence
- symbols, testing for existence
- __if_exists keyword [C++]
ms.assetid: d3eb34b6-f3a9-4063-a286-b62a28c0c7fa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1ac866487c25ee4ce75abbebe9b9f9c2a5e97828
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405940"
---
# <a name="ifexists-statement"></a>__if_exists 陳述式
**__If_exists**陳述式會測試是否存在指定的識別項。 如果識別項存在，就會執行指定的陳述式區塊。  
  
## <a name="syntax"></a>語法  
  
```  
__if_exists ( identifier ) {   
statements  
};  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|*identifier*|要測試其是否存在的識別項。|  
|*陳述式*|若要執行的一或多個陳述式*識別碼*存在。|  
  
## <a name="remarks"></a>備註  
  
> [!CAUTION]
>  若要達到最可靠的結果，使用 **__if_exists**低於下列條件約束陳述式。  
  
-   適用於 **__if_exists**只是簡單類型，而不是範本的陳述式。  
  
-   適用於 **__if_exists**類別內外的識別項的陳述式。 不適用 **__if_exists**至區域變數的陳述式。  
  
-   使用 **__if_exists**只能在函式主體中的陳述式。 函式的主體的外面 **__if_exists**完整定義的類型只能測試陳述式。  
  
-   當您對多載函式進行測試時，無法對特定形式的多載進行測試。  
  
 若要補充 **__if_exists**陳述式是[__if_not_exists](../cpp/if-not-exists-statement.md)陳述式。  
  
## <a name="example"></a>範例  
 請注意，這個範例會使用範本，但不建議這樣做。  
  
```cpp 
// the__if_exists_statement.cpp  
// compile with: /EHsc  
#include <iostream>  
  
template<typename T>  
class X : public T {  
public:  
   void Dump() {  
      std::cout << "In X<T>::Dump()" << std::endl;  
  
      __if_exists(T::Dump) {  
         T::Dump();  
      }  
  
      __if_not_exists(T::Dump) {  
         std::cout << "T::Dump does not exist" << std::endl;  
      }  
   }     
};  
  
class A {  
public:  
   void Dump() {  
      std::cout << "In A::Dump()" << std::endl;  
   }  
};  
  
class B {};  
  
bool g_bFlag = true;  
  
class C {  
public:  
   void f(int);  
   void f(double);  
};  
  
int main() {   
   X<A> x1;  
   X<B> x2;  
  
   x1.Dump();  
   x2.Dump();  
  
   __if_exists(::g_bFlag) {  
      std::cout << "g_bFlag = " << g_bFlag << std::endl;  
   }  
  
   __if_exists(C::f) {  
      std::cout << "C::f exists" << std::endl;  
   }  
  
   return 0;  
}  
```  
  
## <a name="output"></a>輸出  
  
```Output  
In X<T>::Dump()  
In A::Dump()  
In X<T>::Dump()  
T::Dump does not exist  
g_bFlag = 1  
C::f exists  
```  
  
## <a name="see-also"></a>另請參閱  
 [選取範圍陳述式](../cpp/selection-statements-cpp.md)   
 [關鍵字](../cpp/keywords-cpp.md)   
 [__if_not_exists 陳述式](../cpp/if-not-exists-statement.md)