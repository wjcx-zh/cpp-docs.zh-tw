---
title: "__abstract | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__abstract_cpp"
  - "__abstract"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "抽象類別 [c + +]"
  - "__abstract 關鍵字"
ms.assetid: fc6eee5e-9f07-4438-97f7-f2e124263575
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __abstract
> [!NOTE]
>  本主題只適用於 Managed Extensions for C\+\+ 第 1 版。 這個語法只可用於維護第 1 版的程式碼。 請參閱 [abstract](../windows/abstract-cpp-component-extensions.md) 如需新語法中使用的相同功能。  
  
 宣告無法直接執行個體化的 Managed 類別。  
  
## 語法  
  
```  
  
__abstract   
class-specifier  
__abstract   
struct-specifier  
  
```  
  
## 備註  
 `__abstract` 關鍵字會宣告目標類別只能做為另一個類別的基底類別使用。 將 `__abstract` 套用至類別或結構不表示結果為 \_\_gc 類別或 \_\_gc 結構。  
  
 不同於 [abstract](../cpp/abstract-classes-cpp.md) 基底類別在 C\+\+ 中的概念，具有 `__abstract` 關鍵字的類別可以定義其成員函式。  
  
> [!NOTE]
>  搭配 `__abstract` 或 `__value` 關鍵字時不能使用 `__sealed` 關鍵字，搭配 `__interface` 關鍵字時則為多餘的關鍵字。  
  
## 範例  
 在下列範例中，`Derived` 類別衍生自抽象基底類別 \(`Base`\)。 然後會嘗試對二者執行具現化，但只有 `Derived` 成功。  
  
```  
// keyword__abstract.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
__abstract __gc class Base {  
   int BaseFunction() {  
      return 0;  
   }  
};  
  
__gc class Derived: public Base {};  
  
int main() {  
   Base* MyBase = new Base();   // C3622 can't BAse is abstract  
   Derived* MyDerived = new Derived();  
}  
```