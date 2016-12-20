---
title: "ML Nonfatal Error A2085 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "A2085"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "A2085"
ms.assetid: c2fef415-a32b-4249-896c-6d981fc6e327
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ML Nonfatal Error A2085
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**指示或不接受目前的 CPU 模式中的暫存器**  
  
 您嘗試使用的指令、 暫存器或目前的處理器模式無效的關鍵字。  
  
 例如，32 位元暫存器需要 [.386](../../assembler/masm/dot-386.md) 或更新。  例如 CR0 需要特殊權限的模式，控制登錄 [.386P](../../assembler/masm/dot-386p.md) 或更新。  這項錯誤也會產生的 **NEAR32**，  **FAR32**，以及 **平面** 需要的關鍵字。 **386** 或更新。  
  
## 請參閱  
 [ML Error Messages](../../assembler/masm/ml-error-messages.md)