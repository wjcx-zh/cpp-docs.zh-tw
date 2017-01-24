---
title: "ML Nonfatal Error A2050 | Microsoft Docs"
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
  - "A2050"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "A2050"
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ML Nonfatal Error A2050
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**真實或不允許的 BCD 數字**  
  
 浮點數 \(實際\) 的數字或二進位檔 coded 小數 \(BCD\) 常數而非用作為資料的初始設定式。  
  
 發生下列其中一項：  
  
-   在運算式中使用實數或 BCD。  
  
-   實數用來初始化一個指示詞，而非 [DWORD](../../assembler/masm/dword.md)，  [QWORD](../../assembler/masm/qword.md)，或  [TBYTE](../../assembler/masm/tbyte.md)。  
  
-   初始化一個指示詞，而非使用 BCD `TBYTE`。  
  
## 請參閱  
 [ML Error Messages](../../assembler/masm/ml-error-messages.md)