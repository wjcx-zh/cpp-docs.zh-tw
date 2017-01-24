---
title: "ML Nonfatal Error A2133 | Microsoft Docs"
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
  - "A2133"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "A2133"
ms.assetid: 5ba50911-22c8-43b7-90e2-946fc612e05f
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ML Nonfatal Error A2133
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**登錄值被叫用覆寫**  
  
 暫存器做為引數傳遞給程序中，但產生的程式碼[叫用](../../assembler/masm/invoke.md)以傳遞其他引數被終結的暫存器的內容。  
  
 組譯工具可能使用 AX、 AL、 AH、 EAX、 DX、 DL、 DH，並與暫存器來執行資料轉換。  
  
 使用不同的暫存器。  
  
## 請參閱  
 [ML Error Messages](../../assembler/masm/ml-error-messages.md)