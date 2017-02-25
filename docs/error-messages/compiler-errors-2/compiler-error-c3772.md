---
title: "編譯器錯誤 C3772 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3772"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3772"
ms.assetid: 63e938d4-088d-41cc-a562-5881a05b5710
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# 編譯器錯誤 C3772
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

"name"：無效的 friend 樣板宣告  
  
 類別樣板特製化的 friend 宣告無效。 您無法宣告類別樣板的明確或部分特製化，又在相同的陳述式中宣告該特製化的 friend。*name* 預留位置識別無效的宣告。  
  
### 更正這個錯誤  
  
-   請勿宣告類別樣板特製化的 friend。  
  
-   如果應用程式適用的話，您可以宣告類別樣板的 friend，或宣告特定的部分或明確特製化的 friend。  
  
## 範例  
 下列程式碼範例失敗，因為它會宣告類別樣板之部分特製化的 friend。  
  
```  
// c3772.cpp // compile with: /c // A class template. template<class T> class A {}; // A partial specialization of the class template. template<class T> class A<T*> {}; // An explicit specialization. template<> class A<char>; class X { // Invalid declaration of a friend of a partial specialization. template<class T> friend class A<T*>; // C3772 // Instead, if it is appropriate for your application, declare a // friend of the class template. Consequently, all specializations // of the class template are friends: //    template<class T> friend class A; // Or declare a friend of a particular partial specialization: //    friend class A<int*>; // Or declare a friend of a particular explicit specialization: //    friend class A<char>; };  
```  
  
## 請參閱  
 [樣板規格](../Topic/Template%20Specifications.md)   
 [類別樣板的部分特製化](../../cpp/template-specialization-cpp.md)   
 [類別樣板的明確特製化](../Topic/Explicit%20Specialization%20of%20Class%20Templates.md)