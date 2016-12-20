---
title: "__gc | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__gc"
  - "__gc_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__gc 類型"
  - "管理類別 [c + +]"
  - "Managed 類別"
ms.assetid: 63b1e7ab-d1c8-4582-aa89-21bfddf694a9
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __gc
> [!NOTE]
>  本主題只適用於 Managed Extensions for C\+\+ 第 1 版。 這個語法只可用於維護第 1 版的程式碼。 請參閱 [Classes and Structs](../windows/classes-and-structs-cpp-component-extensions.md) 如需新語法中使用的相同功能。  
  
 宣告 \_\_gc 類型。  
  
## 語法  
  
```  
  
__gc  
array-specifier  
__gc   
class-specifier  
__gc   
struct-specifier  
__gc  
interface-specifier  
__gc  
pointer-specifier  
__gc new  
  
```  
  
## 備註  
 \_\_gc 類型是一個 C \+\+ 語言的擴充功能，它藉由提供如互通性和記憶體回收這類功能，簡化了 .NET Framework 程式設計。  
  
> [!NOTE]
>  除非成員函式是純虛擬函式，否則必須定義抽象 \_\_gc 類別的每個成員函式。  
  
 在 Managed Extensions for C\+\+ 中，C\# 類別和 C\# 結構的對等用法如下：  
  
|Managed Extensions for C\+\+|C\#|如需詳細資訊|  
|----------------------------------|---------|------------|  
|\_\_gc struct 或 \_\_gc class|Class \- 類別|[class](../Topic/class%20\(C%23%20Reference\).md) 關鍵字|  
|\_\_value struct 或 \_\_value class|struct|[struct](../Topic/struct%20\(C%23%20Reference\).md) 關鍵字|  
  
## 範例  
 在下列範例中，Managed 類別 \(`X`\) 是使用公用資料成員宣告，透過 Managed 指標操作：  
  
```  
// keyword__gc.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__gc class X {  
public:  
   int i;  
   int ReturnInt() { return 5; }  
};  
  
int main() {  
   // X is a __gc class, so px is a __gc pointer  
   X* px;  
   px = new X;   // creates a managed object of type X  
   Console::WriteLine(px->i);  
  
   px->i = 4;   // modifies X::i through px  
   Console::WriteLine(px->i);  
  
   int n = px->ReturnInt();   // calls X::ReturnInt through px  
   Console::WriteLine(n);  
}  
```  
  
## 輸出  
  
```  
0  
4  
5  
```