---
title: "介面成員的明確覆寫 | Microsoft Docs"
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
  - "虛擬函式的明確覆寫"
  - "函式 [C++], 覆寫"
  - "介面成員, 明確覆寫"
  - "覆寫函式"
  - "虛擬函式, 明確覆寫"
ms.assetid: 46f1f536-bf43-4311-9a17-ff2282e528a9
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 介面成員的明確覆寫
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

宣告類別內介面成員之明確覆寫的語法，已經由 Managed Extensions for C\+\+ 變更為 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)]。  
  
 您通常想要在實作介面的類別中提供介面成員的兩個執行個體，其中一個執行個體是透過介面控點管理類別物件時使用，而另一個執行個體則是透過類別介面使用類別物件時使用。  例如：  
  
```  
public __gc class R : public ICloneable {  
   // to be used through ICloneable  
   Object* ICloneable::Clone();  
  
   // to be used through an R  
   R* Clone();  
};  
```  
  
 在 Managed Extensions 中，使用以介面名稱來限定的方法名稱提供介面方法的明確宣告，藉以達成此目的。  類別的特定執行個體則是資格不符的。  在本範例中透過 `R` 的執行個體明確呼叫時，就不再需要向下轉換 \(Down Cast\) `Clone` 的傳回值。  
  
 在新語法中，已引入的一般覆寫機制會取代 Managed Extensions 語法。  重新撰寫的範例如下所示：  
  
```  
public ref class R : public ICloneable {  
public:  
   // to be used through ICloneable  
   virtual Object^ InterfaceClone() = ICloneable::Clone;  
  
   // to be used through an R  
   virtual R^ Clone();  
};  
```  
  
 本修訂會要求明確覆寫的介面成員在類別中具備唯一名稱。  我在這裡為 `InterfaceClone` 提供了複雜的名稱。  行為是相同的，經由 `ICloneable` 介面進行的引動過程會叫用重新命名的 `InterfaceClone,`，而透過型別 `R` 的物件所進行的呼叫則會叫用第二個 `Clone` 介面。  
  
## 請參閱  
 [在類別或介面中的成員宣告 \(C\+\+\/CLI\)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [Explicit Overrides](../windows/explicit-overrides-cpp-component-extensions.md)