---
title: ".FPO | Microsoft Docs"
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
  - ".FPO"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".FPO directive"
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .FPO
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

。FPO 指示詞控制偵錯記錄到.debug$ F 區段或區段的發出。  
  
## 語法  
  
```  
  
FPO (  
cdwLocals  
,   
cdwParams  
,   
cbProlog  
,   
cbRegs  
,   
fUseBP  
,   
cbFrame  
)  
  
```  
  
#### 參數  
 `cdwLocals`  
 本機變數，不帶正負號的 32 位元值的數目。  
  
 `cdwParams`  
 在 \[DWORD，不帶正負號的 16 位元值參數的大小。  
  
 *cbProlog*  
 在函式初構程式碼，不帶正負號的 8 位元值的位元組數目。  
  
 `cbRegs`  
 數字儲存的暫存器。  
  
 `fUseBP`  
 指出是否已配置的 EBP 暫存器。  0 或 1。  
  
 *cbFrame*  
 指示框架類型。  如需詳細資訊，請參閱 [FPO\_DATA](http://msdn.microsoft.com/library/windows/desktop/ms679352)。  
  
## 請參閱  
 [Directives Reference](../../assembler/masm/directives-reference.md)