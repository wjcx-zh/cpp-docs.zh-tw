---
title: "setjmp/longjump | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: b0e21902-095d-4198-8f9a-b6326525721a
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# setjmp/longjump
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您包含 setjmpex.h 或 setjmp.h 時，所有的 [setjmp](../c-runtime-library/reference/setjmp.md) 或 [longjmp](../c-runtime-library/reference/longjmp.md) 呼叫會產生叫用解構函式 \(Destructor\) 和 finally 呼叫的回溯。  這和 x86 不同，在 x86 中包含 setjmp.h 會導致不叫用 finally 子句和解構函式。  
  
 `setjmp` 呼叫會保留目前的堆疊指標、靜態暫存器和 MxCsr 暫存器。  `longjmp` 呼叫會傳回最近的 `setjmp` 呼叫位置，並將堆疊指標、靜態暫存器和 MxCsr 暫存器重設回最近的 `setjmp` 呼叫所保留的狀態。  
  
## 請參閱  
 [呼叫慣例](../build/calling-convention.md)