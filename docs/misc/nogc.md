---
title: "__nogc | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__nogc_cpp"
  - "__nogc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__nogc 類型宣告"
  - "類別 [c + +] unmanaged 類型"
  - "unmanaged 的類別的宣告"
  - "unmanaged 類別"
ms.assetid: 3e7f1b09-0fc3-4a8f-9458-a22f7a38ce45
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __nogc
> [!NOTE]
>  本主題只適用於 Managed Extensions for C\+\+ 第 1 版。 這個語法只可用於維護第 1 版的程式碼。 在新語法中，您不需要將類型明確標記為 Unmanaged。  
  
 明確宣告 Unmanaged 類型。  
  
## 語法  
  
```  
  
__nogc   
class-specifier  
__nogc   
struct-specifier  
__nogc  
interface-specifier  
__nogc  
array-specifier  
__nogc  
pointer-specifier  
__nogc  
new  
  
```  
  
## 備註  
 `__nogc` 關鍵字可用來明確指定將物件配置在標準 C\+\+ 堆積上。 這個關鍵字為選擇項。 如果您未在類別宣告前面指定 `__gc` 或 `__nogc`，則它會預設為 `__nogc`。  
  
 這種類型的物件類似標準 C\+\+ 物件，這類物件會從標準 C\+\+ 堆積進行配置，而且不受 Managed 物件的限制影響。  
  
 `__nogc` 關鍵字也可在 \_\_value 類型的物件明確配置在標準 C\+\+ 堆積上時使用。  
  
```  
// keyword__nogc.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
__value struct V {   
   int i;  
};  
int main() {  
   V * v = __nogc new V;  
   v->i = 10;  
   delete v;  
}  
```  
  
> [!NOTE]
>  `__nogc` 關鍵字也可以套用至陣列和指標類型。  
  
 gc 指標不可以是 `__nogc` 類別的成員。 如需在 `__nogc` 類別中嵌入實值類型的方針，請參閱 [\_\_value](../misc/value.md)。  
  
## 範例  
 下列範例會宣告 Unmanaged 類別 \(`X`\) 並且具現化及修改物件：  
  
```  
// keyword__nogc_2.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__nogc class X {  
public:  
   int i;  
};  
  
int main() {  
   X* x;   // declares an unmanaged pointer of type X  
   x = new X();   // creates unmanaged object of type X on the C++ heap  
   Console::WriteLine(x->i);  
  
   x->i = 4;   // modifies unmanaged object  
   Console::WriteLine(x->i);  
  
   delete x;   // call C++ delete operator to clean up resource  
}  
```  
  
 **48378256 4**