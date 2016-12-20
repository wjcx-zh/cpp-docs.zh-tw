---
title: "編譯器錯誤 C2847 | Microsoft Docs"
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
  - "C2847"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2847"
ms.assetid: 9ad9a0e0-8b16-49d9-a5be-f8eda2372aa9
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2847
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法將 sizeof 套用於 Managed 或 WinRT 型別 'class'  
  
 [sizeof](../../cpp/sizeof-operator.md) 運算子會在編譯時期取得物件的值。  Managed 或 WinRT 型別、介面或實值型別的大小是動態的，因此無法在編譯時間得知。  
  
 例如，下列範例會產生 C2847：  
  
```  
// C2847.cpp  
// compile with: /clr  
ref class A {};  
  
int main() {  
   A ^ xA = gcnew A;  
   sizeof(*xA);   // C2847 cannot use sizeof on managed object  
}  
```  
  
 下列範例會產生 C2847：  
  
```  
// C2847_b.cpp  
// compile with: /clr:oldSyntax  
__gc class A {};  
  
int main() {  
   A *xA = new A;  
   sizeof(*xA);   // C2847 cannot use sizeof on managed object  
}  
```