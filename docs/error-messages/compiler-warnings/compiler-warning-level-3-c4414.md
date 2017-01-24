---
title: "編譯器警告 (層級 3) C4414 | Microsoft Docs"
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
  - "C4414"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4414"
ms.assetid: bc81d3ad-55dc-4a6b-a6f2-ec0ef38347df
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 3) C4414
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 至函式的 SHORT 跳躍指令被轉換為 NEAR  
  
 Short 跳躍指令會產生精簡指令，形成分支，移至距離該指令有限範圍內的位址。  指令包括代表跳躍點與目標位址 \(即函式定義\) 之間的短距離位移 \(Offset\)。  在進行連結時，函式可能會遭移除，或因連結時的最佳化而導致函式被移出短距離位移可達到的範圍。  編譯器必須產生特別的跳躍點記錄，跳躍點指令必須是 NEAR 或 FAR。  編譯器會進行轉換。  
  
 例如，下列程式碼會產生 C4414：  
  
```  
// C4414.cpp  
// compile with: /W3 /c  
// processor: x86  
int DoParityEven();  
int DoParityOdd();  
unsigned char global;  
int __declspec(naked) DoParityEither()  
{  
   __asm  
   {  
      test global,0  
      jpe SHORT DoParityEven  // C4414  
      jmp SHORT DoParityOdd   // C4414  
   }  
}  
```