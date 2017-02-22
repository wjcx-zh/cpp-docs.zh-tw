---
title: "編譯器錯誤 C3830 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3830"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3830"
ms.assetid: c9798f88-5001-4067-9fb1-09957ddc6fa8
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C3830
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type1': 不可繼承自 'type2'，實值型別只能繼承自介面類別  
  
 實值型別不能繼承基底類別。如需詳細資訊，請參閱[Classes and Structs](../../windows/classes-and-structs-cpp-component-extensions.md)。  
  
 下列範例會產生 C3830：  
  
```  
// C3830a.cpp  
// compile with: /clr /c  
public value struct MyStruct4 {  
   int i;  
};  
  
public value class MyClass : public MyStruct4 {};   // C3830  
  
// OK  
public interface struct MyInterface4 {  
   void i();  
};  
  
public value class MyClass2 : public MyInterface4 {  
public:  
   virtual void i(){}  
};  
```  
  
 **Managed Extensions for C\+\+**  
  
 `__value` 型別不能繼承基底類別。  
  
 下列範例會產生 C3830：  
  
```  
// C3830b.cpp  
// compile with: /clr:oldSyntax /c  
#using <mscorlib.dll>  
__value struct v : public System::Object {};   // C3830  
__value struct w {};   // OK  
```