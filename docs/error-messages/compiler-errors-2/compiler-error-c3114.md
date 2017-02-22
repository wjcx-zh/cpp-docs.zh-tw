---
title: "編譯器錯誤 C3114 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3114"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3114"
ms.assetid: b5d2df4f-87d0-4292-9981-25c6a6013c05
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器錯誤 C3114
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'argument': 不是有效的具名屬性引數  
  
 若要讓屬性 \(attribute\) 類別資料成員做為有效的具名引數，它絕對不能標記為 `static`、`const` 或 `literal`。  如果是屬性 \(property\)，此屬性不可以為 `static`，而且必須有 get 和 set 存取子。  
  
 如需詳細資訊，請參閱[property](../../windows/property-cpp-component-extensions.md)與[User\-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md)。  
  
## 範例  
 下列範例會產生 C3114。  
  
```  
// C3114.cpp  
// compile with: /clr /c  
public ref class A : System::Attribute {  
public:  
   static property int StaticProp {  
      int get();  
   }  
  
   property int Prop2 {  
      int get();  
      void set(int i);  
   }  
};  
  
[A(StaticProp=123)]   // C3114  
public ref class R {};  
  
[A(Prop2=123)]   // OK  
public ref class S {};  
```