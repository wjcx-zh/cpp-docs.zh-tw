---
title: "編譯器錯誤 C2811 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2811"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2811"
ms.assetid: 6a44b18e-44c1-49d8-9b99-e0545b9a6e7d
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C2811
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type1' : 無法從 'type2' 繼承，ref class 只能從 ref class 或 interface class 繼承  
  
 您試圖使用 Unmanaged 類別當做 Managed 類別的基底類別。  
  
 下列範例會產生 C2811：  
  
```  
// C2811.cpp  
// compile with: /clr /c  
struct S{};  
ref struct T {};  
ref class C : public S {};   // C2811  
ref class D : public T {};   // OK  
```