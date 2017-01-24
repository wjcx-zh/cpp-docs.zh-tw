---
title: "編譯器警告 (層級 1) C4311 | Microsoft Docs"
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
  - "C4311"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4311"
ms.assetid: ddc579d0-d051-47bc-915d-71ffb32323c9
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4311
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'variable' : 指標從 'type' 到 'type' 截斷  
  
 此警告會偵測 64 位元指標截斷問題。  例如，如果程式碼是針對 64 位元架構而編譯的，若指派給 `int` \(32 位元\)，指標 \(64 位元\) 的值將會被截斷。  如需詳細資訊，請參閱[使用指標的規則](http://msdn.microsoft.com/library/windows/desktop/aa384242)。  
  
 如需其他與警告 C4311 的常見原因有關的資訊，請參閱[常見編譯器錯誤](http://msdn.microsoft.com/library/windows/desktop/aa384160)。  
  
 下列程式碼範例會在針對 64 位元目標而編譯時產生 C4311，並接著示範如何修正此問題：  
  
```  
// C4311.cpp  
// compile by using: cl /W1 C4311.cpp  
int main() {  
   void* p = &p;  
   unsigned int i = (unsigned int) p;   // C4311 for 64-bit targets  
   unsigned long long j = (unsigned long long) p;   // OK  
}  
  
```