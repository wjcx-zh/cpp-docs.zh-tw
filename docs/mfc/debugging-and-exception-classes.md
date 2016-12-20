---
title: "偵錯和例外狀況類別 | Microsoft Docs"
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
  - "vc.classes.debug"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "偵錯 [MFC], 偵錯類別"
  - "偵錯 [MFC], 例外狀況類別"
ms.assetid: 0d158efd-2e62-452e-9d2a-d3c30dfee7f9
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 偵錯和例外狀況類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這些類別支援偵錯動態記憶體配置，並支援從擲回例外狀況的函式所攔截的函式所傳遞的例外狀況資訊。  
  
 使用 [CDumpContext](../mfc/reference/cdumpcontext-class.md) 類別和 [CMemoryState](../mfc/reference/cmemorystate-structure.md) 類別在開發期間協助偵錯，如 [偵錯 MFC 應用程式](../Topic/MFC%20Debugging%20Techniques.md)中所述。  使用 [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) 在執行階段來判斷所有物件類別，如本文 [存取的執行階段類別資訊](../mfc/accessing-run-time-class-information.md)所述。  架構會使用 `CRuntimeClass` 動態建立特定類別的物件。  
  
## 請參閱  
 [類別概觀](../mfc/class-library-overview.md)