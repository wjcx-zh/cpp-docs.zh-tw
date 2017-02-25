---
title: "編譯器錯誤 C2061 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2061"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2061"
ms.assetid: b0e61c0c-a205-4820-b9aa-301d6c6fe6eb
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 編譯器錯誤 C2061
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

語法錯誤 : 識別項 'identifier'  
  
 編譯器發現識別項出現在不應出現的地方。  請確定已宣告 `identifier`，再加以使用。  
  
 初始設定式可能是由括弧括住。  若要避免這種問題，可將宣告子 \(Declarator\) 括在括弧中，或讓它成為 `typedef`。  
  
 當編譯器在偵測時將運算式視為類別樣板引數時，也可能會發生這個錯誤；請使用 [typename](../../cpp/typename.md) 告知編譯器它是個型別。  
  
 下列範例會產生 C2061：  
  
```  
// C2061.cpp  
// compile with: /c  
template < A a >   // C2061  
// try the following line instead  
// template < typename b >  
class c{};  
```  
  
 如果您傳遞執行個體名稱給 [typeid](../../windows/typeid-cpp-component-extensions.md)，可能會發生 C2061：  
  
```  
// C2061b.cpp  
// compile with: /clr  
ref struct G {  
   int i;  
};  
  
int main() {  
   G ^ pG = gcnew G;  
   System::Type ^ pType = typeid<pG>;   // C2061  
   System::Type ^ pType2 = typeid<G>;   // OK  
}  
```