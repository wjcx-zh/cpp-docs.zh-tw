---
title: "可覆寫的 CWinApp 成員函式 | Microsoft Docs"
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
  - "CWinApp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "應用程式類別"
  - "CWinApp 類別, 可覆寫函式"
  - "覆寫, CWinApp 中的可覆寫函式"
ms.assetid: 07183d5e-734b-45d9-a8b6-9dde4adac0b4
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 可覆寫的 CWinApp 成員函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CWinApp](../mfc/reference/cwinapp-class.md) 提供數個金鑰可覆寫成員函式 \(`CWinApp` 覆寫從類別 [CWinThread](../mfc/reference/cwinthread-class.md)的這些成員，衍生自 `CWinApp` \)：  
  
-   [InitInstance](../mfc/initinstance-member-function.md)  
  
-   [執行](../mfc/run-member-function.md)  
  
-   [ExitInstance](../mfc/exitinstance-member-function.md)  
  
-   [OnIdle](../mfc/onidle-member-function.md)  
  
 唯一您必須覆寫的 `CWinApp` 成員函式是 `InitInstance`。  
  
## 請參閱  
 [CWinApp：應用程式類別](../mfc/cwinapp-the-application-class.md)