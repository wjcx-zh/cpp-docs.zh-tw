---
title: "編譯器錯誤 C2893 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2893"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2893"
ms.assetid: ec0cbe43-005d-45da-8742-aaeb9b81d28e
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2893
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

特製化函式樣板 'template name' 失敗  
  
 編譯器未能特製化函式樣板。  造成此項錯誤的原因有許多。  
  
 一般來說，解決 C2893 錯誤的方法是檢閱函式的簽章，並確定您可以具現化每一個型別。  
  
## 範例  
 造成 C2893 的原因可能是：`f` 的樣板參數 `T` 是推算為 `std::map<int,int>`，但 `std::map<int,int>` 沒有任何成員 `data_type` \(`T::data_type` 不能以 `T = std::map<int,int>` 具現化\)。  下列範例會產生 C2893：  
  
```  
// C2893.cpp  
// compile with: /c /EHsc  
#include<map>  
using namespace std;  
class MyClass {};  
  
template<class T>   
inline typename T::data_type  
// try the following line instead  
// inline typename  T::mapped_type  
f(T const& p1, MyClass const& p2);  
  
template<class T>  
void bar(T const& p1) {  
    MyClass r;  
    f(p1,r);   // C2893  
}  
  
int main() {  
   map<int,int> m;  
   bar(m);  
}  
```