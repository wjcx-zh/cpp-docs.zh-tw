---
title: "How to: Declare Value Types with the interior_ptr Keyword (C++/CLI) | Microsoft Docs"
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
  - "_ptr keyword"
  - "value types, declaring"
ms.assetid: 49eea66e-eeba-49bd-95b0-ba297be436e3
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Declare Value Types with the interior_ptr Keyword (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`interior_ptr` 可與實值型別一起使用。  
  
> [!IMPORTANT]
>  這個語言功能支援於 **\/clr** 編譯器選項，但不支援於 **\/ZW** 編譯器選項。  
  
## 範例  
  
### 說明  
 下列 [!INCLUDE[cppcli](../build/reference/includes/cppcli_md.md)] 範例會示範如何使用具有實值型別的 `interior_ptr` 。  
  
### 程式碼  
  
```  
// interior_ptr_value_types.cpp  
// compile with: /clr  
value struct V {  
   V(int i) : data(i){}  
   int data;  
};  
  
int main() {  
   V v(1);  
   System::Console::WriteLine(v.data);  
  
   // pointing to a value type  
   interior_ptr<V> pv = &v;  
   pv->data = 2;  
  
   System::Console::WriteLine(v.data);  
   System::Console::WriteLine(pv->data);  
  
   // pointing into a value type  
   interior_ptr<int> pi = &v.data;  
   *pi = 3;  
   System::Console::WriteLine(*pi);  
   System::Console::WriteLine(v.data);  
   System::Console::WriteLine(pv->data);  
}  
```  
  
### Output  
  
```  
1  
2  
2  
3  
3  
3  
```  
  
## 範例  
  
### 說明  
 在實值型別，對 interior\_ptr 的 `this` 指標評估。  
  
 在實值型別 `V`的非靜態成員函式的主體中， `this` 是其值為物件位址函式呼叫 `interior_ptr<V>` 型別的運算式。  
  
### 程式碼  
  
```  
// interior_ptr_value_types_this.cpp  
// compile with: /clr /LD  
value struct V {  
   int data;  
   void f() {  
      interior_ptr<V> pv1 = this;  
      // V* pv2 = this;   error  
   }  
};  
```  
  
## 範例  
  
### 說明  
 下列範例顯示如何使用有靜態成員的傳址運算子。  
  
 靜態 Visual C\+\+ 型別成員的位址產生原生指標。因為實值型別成員在執行階段堆積上，而且可以由記憶體回收行程移動，靜態實值型別成員的位址是 Managed 指標。  
  
### 程式碼  
  
```  
// interior_ptr_value_static.cpp  
// compile with: /clr  
using namespace System;  
value struct V { int i; };  
  
ref struct G {  
   static V v = {22};   
   static int i = 23;   
   static String^ pS = "hello";   
};  
  
int main() {  
   interior_ptr<int> p1 = &G::v.i;  
   Console::WriteLine(*p1);  
  
   interior_ptr<int> p2 = &G::i;  
   Console::WriteLine(*p2);  
  
   interior_ptr<String^> p3 = &G::pS;  
   Console::WriteLine(*p3);  
}  
```  
  
### Output  
  
```  
22  
23  
hello  
```  
  
## 請參閱  
 [interior\_ptr \(C\+\+\/CLI\)](../windows/interior-ptr-cpp-cli.md)