---
title: "__if_exists 陳述式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __if_exists_cpp
- __if_exists
dev_langs:
- C++
helpviewer_keywords:
- identifiers, testing for existence
- symbols, testing for existence
- __if_exists keyword [C++]
ms.assetid: d3eb34b6-f3a9-4063-a286-b62a28c0c7fa
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 3d0eaa00abb1f833ef491fc27bfee01790776edb
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="ifexists-statement"></a>__if_exists 陳述式
`__if_exists` 陳述式會測試指定識別項是否存在。 如果識別項存在，就會執行指定的陳述式區塊。  
  
## <a name="syntax"></a>語法  
  
```  
__if_exists ( identifier ) {   
statements  
};  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|說明|  
|---------------|-----------------|  
|`identifier`|要測試其是否存在的識別項。|  
|`statements`|如果執行的一或多個陳述式`identifier`存在。|  
  
## <a name="remarks"></a>備註  
  
> [!CAUTION]
>  為取得最可靠的結果，使用 `__if_exists` 陳述式時請遵循下列條件約束。  
  
-   只能將 `__if_exists` 陳述式套用至簡單類型，而不能套用於範本。  
  
-   將 `__if_exists` 陳述式套用至類別內外的識別項。 勿將 `__if_exists` 陳述式套用至區域變數。  
  
-   只在函式本體中使用 `__if_exists` 陳述式。 在函式的主體之外，`__if_exists` 陳述式只能測試完整定義的類型。  
  
-   當您對多載函式進行測試時，無法對特定形式的多載進行測試。  
  
 補數`__if_exists`陳述式是[__if_not_exists](../cpp/if-not-exists-statement.md)陳述式。  
  
## <a name="example"></a>範例  
 請注意，這個範例會使用範本，但不建議這樣做。  
  
```  
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
  
```  
In X<T>::Dump()  
In A::Dump()  
In X<T>::Dump()  
T::Dump does not exist  
g_bFlag = 1  
C::f exists  
```  
  
## <a name="see-also"></a>另請參閱  
 [選擇陳述式](../cpp/selection-statements-cpp.md)   
 [關鍵字](../cpp/keywords-cpp.md)   
 [__if_not_exists 陳述式](../cpp/if-not-exists-statement.md)
