---
title: "編譯器警告 (層級 4) C4366 | Microsoft Docs"
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
  - "C4366"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4366"
ms.assetid: 65d2942f-3741-42f4-adf2-4920d5a055ca
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4366
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

一元 'operator' 運算子的結果可能未對齊  
  
 如果結構成員有可能會因為封裝而無法對齊，編譯器就會在該成員的位址指定給對齊指標時發出警告。  此項預設為對齊所有指標。  
  
 若要解決 C4366，請變更結構的對齊，或使用 [\_\_unaligned](../../cpp/unaligned.md) 關鍵字宣告指標。  
  
 如需詳細資訊，請參閱 \_\_unaligned 和 [pack](../../preprocessor/pack.md)。  
  
## 範例  
 下列範例會產生 C4366。  
  
```  
// C4366.cpp  
// compile with: /W4 /c  
// processor: IPF x64  
#pragma pack(1)  
struct X {  
   short s1;  
   int s2;  
};  
  
int main() {  
   X x;  
   short * ps1 = &x.s1;   // OK  
   int * ps2 = &x.s2;   // C4366  
}  
```