---
title: "密封虛擬函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__sealed 關鍵字"
  - "衍生類別, 虛擬函式"
  - "sealed 關鍵字 [C++]"
  - "虛擬函式, 密封"
ms.assetid: 0e9fae03-6425-4512-9a24-8ccb6dc8a0d4
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 密封虛擬函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從 Managed Extensions for C\+\+ 升級為 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 之後，密封虛擬函式 \(Virtual Function\) 的語法已變更。  
  
 在 Managed Extensions 中，`__sealed` 關鍵字是用來修改參考型別 \(Reference Type\)，使其後續無法衍生 \(請參閱 [Managed 類別類型的宣告](../dotnet/declaration-of-a-managed-class-type.md)\)，或是用來修改虛擬函式，使其後續無法在衍生類別中覆寫方法。  例如：  
  
```  
__gc class base { public: virtual void f(); };  
__gc class derived : public base {  
public:  
   __sealed void f();  
};  
```  
  
 在此範例中，`derived::f()` 會根據是否與函式原型 \(Function Prototype\) 完全相符來覆寫 `base::f()` 執行個體。  `__sealed` 關鍵字表示從衍生類別繼承而來的後續類別無法提供 `derived::f()` 的覆寫。  
  
 在新的語法中，`sealed` 必須放在簽章 \(Signature\) 的後面，而不是像先前所允許的可以出現在實際函式原型之前的任何位置。  此外，使用 `sealed` 時也必須明確使用 `virtual` 關鍵字。  換句話說，上述 `derived` 的正確轉譯結果應該如下：  
  
```  
ref class derived: public base {  
public:  
   virtual void f() override sealed;  
};  
```  
  
 如果這個執行個體中沒有出現 `virtual` 關鍵字，將會發生錯誤。  在新的語法中，可以用內容關鍵字 `abstract` 取代 `=0`，以表示純虛擬函式 \(Pure Virtual Function\)。  在 Managed Extensions 中不支援這種方式。  例如：  
  
```  
__gc class base { public: virtual void f()=0; };  
```  
  
 可以重新改寫為：  
  
```  
ref class base { public: virtual void f() abstract; };  
```  
  
## 請參閱  
 [在類別或介面中的成員宣告 \(C\+\+\/CLI\)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [sealed](../windows/sealed-cpp-component-extensions.md)