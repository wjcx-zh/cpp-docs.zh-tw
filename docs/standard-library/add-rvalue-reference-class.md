---
title: "add_rvalue_reference 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "type_traits/std::add_rvalue_reference"
  - "std::add_rvalue_reference"
  - "add_rvalue_reference"
  - "std.add_rvalue_reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "add_rvalue_reference 類別"
ms.assetid: 76b0cb7c-1031-45d0-b409-f03ab0297580
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# add_rvalue_reference 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果它是物件或函式的類型，請建立右值參考類型的樣板參數。 否則，請參考摺疊的語意 （semantics），因為此類型為樣板參數相同。  
  
## 語法  
  
```cpp  
template<class T>  
    struct add_rvalue_reference;  
  
template<class T>  
    using add_rvalue_reference_t = typename add_rvalue_reference<T>::type;  
```  
  
#### 參數  
 T  
 要修改的類型。  
  
## 備註  
 `add_rvalue_reference` 類別具有名為 `type`, ，它是類型的樣板參數的右值參考的別名 `T`。 參考摺疊的語意表示，對於非物件和非函式類型 `T`, ，`T&&` 是 `T`。 例如，當 `T` 是左值參考類型，  `add_rvalue_reference<T>::type` 是左值參考類型，而不是右值參考。  
  
 為了方便起見，\< type\_traits \> 定義協助程式範本時， `add_rvalue_reference_t`, ，該別名 `type` 成員 `add_rvalue_reference`。  
  
## 範例  
 這個程式碼範例顯示如何藉由建立右值參考型別使用 static\_assert `add_rvalue_reference` 和 `add_rvalue_reference_t`, ，以及如何將 `add_rvalue_reference` 左值參考類型不是右值參考，但摺疊為左值參考型別。  
  
```cpp  
// ex_add_rvalue_reference.cpp  
// Build by using: cl /EHsc /W4 ex_add_rvalue_reference.cpp  
#include <type_traits>   
#include <iostream>   
#include <string>  
  
using namespace std;  
int main()  
{  
    static_assert(is_same<add_rvalue_reference<string>::type, string&&>::value,   
        "Expected add_rvalue_reference_t<string> to be string&&");  
    static_assert(is_same<add_rvalue_reference_t<string*>, string*&&>::value,   
        "Expected add_rvalue_reference_t<string*> to be string*&&");  
    static_assert(is_same<add_rvalue_reference<string&>::type, string&>::value,   
        "Expected add_rvalue_reference_t<string&> to be string&");  
    static_assert(is_same<add_rvalue_reference_t<string&&>, string&&>::value,   
        "Expected add_rvalue_reference_t<string&&> to be string&&");  
    cout << "All static_assert tests of add_rvalue_reference passed." << endl;  
    return 0;  
}  
  
/*Output:  
All static_assert tests of add_rvalue_reference passed.  
*/  
```  
  
## 需求  
 標頭：\<type\_traits\> 命名空間：std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [add\_lvalue\_reference Class](../standard-library/add-lvalue-reference-class.md)   
 [is\_rvalue\_reference 類別](../standard-library/is-rvalue-reference-class.md)