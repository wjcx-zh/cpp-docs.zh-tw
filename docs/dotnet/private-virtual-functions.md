---
title: "私用虛擬函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "存取修飾詞 [C++], 類別成員的"
  - "衍生類別, 虛擬函式"
  - "成員存取 [C++], 虛擬成員"
  - "虛擬函式, private"
ms.assetid: 04448086-bf72-44be-9c1f-dfda1744949e
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 私用虛擬函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從 Managed Extensions for C\+\+ 升級為 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 之後，在衍生類別中處理私用虛擬函式的方式已變更。  
  
 在 Managed Extensions 中，虛擬函式的存取層級並不能限制它在衍生類別中被覆寫。  在新的語法中，虛擬函式不能覆寫它無法存取的基底類別 \(Base Class\) 虛擬函式。  例如：  
  
```  
__gc class MyBaseClass {  
   // inaccessible to a derived class   
   virtual void g();  
};  
  
__gc class MyDerivedClass : public MyBaseClass {  
public:  
   // okay in Managed Extensions; g() overrides MyBaseClass::g()  
   // error in new syntax; cannot override: MyBaseClass::g() is inaccessible …  
   void g();  
};  
```  
  
 這種設計在新的語法中並沒有實際的對應方式。  只需要將基底類別成員變成可以存取，也就是非私用的 \(Private\)，就可以了。  繼承的方法不一定要採取相同的存取方式。  在此範例中，最不具破壞性的變更就是將 MyBaseClass 成員變成 `protected`。  如此一來，一般程式仍然無法透過 MyBaseClass 存取方法。  
  
```  
ref class MyBaseClass {  
protected:  
   virtual void g();  
};  
  
ref class MyDerivedClass : MyBaseClass {  
public:  
   virtual void g() override;  
};  
```  
  
 請注意，如果基底類別中沒有明確的 `virtual` 關鍵字，則根據新的語法將會產生警告訊息。  
  
## 請參閱  
 [在類別或介面中的成員宣告 \(C\+\+\/CLI\)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [成員可視性](../misc/member-visibility.md)