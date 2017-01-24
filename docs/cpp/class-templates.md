---
title: "類別樣板 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "類別樣板"
  - "類別 [C++], 在類型上操作"
  - "範本, 類別樣板"
ms.assetid: 633a53c8-24ee-4c23-8c88-e7c3cb0b7ac3
caps.latest.revision: 13
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 類別樣板
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以使用類別樣板建立一系列以某個類型運作的類別。  類別樣板是參數化類型。  它們隱含可以針對各種傳入參數 \(稱為樣板引數\) 值建立的不同類別。  
  
 樣板引數可以是類型或所指定類型的常數值。  例如：  
  
```  
// class_templates.cpp  
template <class T, int i> class TempClass   
{  
public:  
    TempClass( void );  
    ~TempClass( void );  
    int MemberSet( T a, int b );  
private:  
    T Tarray[i];  
    int arraysize;  
};  
  
int main()  
{  
}  
```  
  
 在此範例中，樣板類別使用了兩個參數，一個為 `T` 類型，另一個為 int `i`。  `T` 參數可以傳遞任何類型的參數，包括結構和類別。  `i` 參數必須傳遞整數常數。  因為 `i` 是在編譯時期定義的常數，您可以使用標準陣列宣告來定義 `i` 大小的成員陣列。  
  
 如需詳細資訊，請參閱：  
  
-   [類別樣板的成員](../Topic/Members%20of%20Class%20Templates.md)  
  
-   [類別成員的樣板](../Topic/Templates%20for%20Class%20Members.md)  
  
-   [樣板類別的成員函式](../Topic/Member%20Functions%20of%20Template%20Classes.md)  
  
-   [巢狀類別樣板](../Topic/Nested%20Class%20Templates.md)  
  
-   [類別樣板具現化](../Topic/Class%20Template%20Instantiation.md)  
  
-   [類別樣板的明確特製化](../Topic/Explicit%20Specialization%20of%20Class%20Templates.md)  
  
-   [類別樣板的部分特製化](../cpp/template-specialization-cpp.md)  
  
-   [類別樣板的預設引數](../Topic/Default%20Arguments%20for%20Class%20Templates.md)  
  
-   [樣板 Friend](../cpp/template-friends.md)  
  
## 請參閱  
 [樣板](../cpp/templates-cpp.md)