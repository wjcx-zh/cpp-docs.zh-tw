---
title: "ML Fatal Error A1007 | Microsoft Docs"
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
  - "A1007"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "A1007"
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ML Fatal Error A1007
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**巢狀層級太深**  
  
 組譯工具已達到其巢狀的限制。  限制為除了註明否則 20 層。  
  
 巢狀下列其中一項被結構太深：  
  
-   高層級的指示詞，例如 [。IF](../../assembler/masm/dot-if.md), [.重複](../../assembler/masm/dot-repeat.md)，或  [。雖然](../../assembler/masm/dot-while.md)。  
  
-   結構定義。  
  
-   組件的條件式指示詞中。  
  
-   程序定義。  
  
-   A  [PUSHCONTEXT](../../assembler/masm/pushcontext.md) 指示詞 \(上限為 10\)。  
  
-   區段定義。  
  
-   包含檔案。  
  
-   巨集。  
  
## 請參閱  
 [ML Error Messages](../../assembler/masm/ml-error-messages.md)