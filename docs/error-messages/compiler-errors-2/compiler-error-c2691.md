---
title: "編譯器錯誤 C2691 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2691"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2691"
ms.assetid: 6925f8f3-ea60-4909-91e6-b781492c645d
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2691
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'資料類型'：受管理或 WinRT 陣列不能有這種項目類型  
  
 受管理或 WinRT 陣列項目的類型可以是值類型或參考類型。  
  
 下列範例會產生 C2691：  
  
```  
// C2691a.cpp  
// compile with: /clr  
class A {};  
  
int main() {  
   array<A>^ a1 = gcnew array<A>(20);   // C2691  
   array<int>^ a2 = gcnew array<int>(20);   // value type OK  
}  
```  
  
 下列範例會產生 C2691：  
  
```  
// C2691b.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
int main() {  
   int * a1 __gc[];   // C2691  
   int * a1 = new int [20];   // OK  
}  
```  
  
 如果您嘗試使用 Managed Extensions for C\+\+ 定義不規則的陣列，C2691 也可能發生。  目前的語法支援不規則的陣列，如需詳細資訊，請參閱 [Arrays](../../windows/arrays-cpp-component-extensions.md)。  
  
 下列範例會產生 C2691：  
  
```  
// C2691c.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
int main() {  
   Int32 myJaggedArray[][] = new Int32 [50][];   // C2691  
}  
```