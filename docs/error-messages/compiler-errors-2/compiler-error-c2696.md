---
title: "編譯器錯誤 C2696 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2696"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2696"
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 編譯器錯誤 C2696
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法建立 Managed 型別 'type' 的暫存物件  
  
 Unmanaged 程式中的 `const` 的參考使得編譯器呼叫建構函式，並在堆疊上建立一個暫存物件。  但是 Managed 類別絕對不能建立在堆疊上。  
  
 C2696 只能透過 **\/clr:oldSyntax** 取得。  
  
 下列範例會產生 C2696：  
  
```  
// C2696b.cpp  
// compile with: /clr:oldSyntax  
  
__gc class G {  
public:  
   G( int i ) {}  
};  
  
void func( const G& g );  
  
int main() {  
   func( 1 );   // C2696  
   G *myG = new G( 1 );   // OK  
   func( *myG );  
}  
```