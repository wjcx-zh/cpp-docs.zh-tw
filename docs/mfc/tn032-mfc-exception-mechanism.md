---
title: "TN032：MFC 例外狀況機制 | Microsoft Docs"
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
  - "vc.mfc.exceptions"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CException 類別, 使用"
  - "MFC, 例外狀況"
  - "TN032"
ms.assetid: 0271f0aa-82cb-47a2-b7ea-e88126fc7e43
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN032：MFC 例外狀況機制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

舊版的 Visual C\+\+ 不支援 Standard C\+\+ 例外狀況機制，因此， MFC 提供了使用的巨集 **TRY\/CATCH\/THROW** 。  這個版本的 Visual C\+\+ 完全支援 C\+\+ 例外狀況。  這個標記會自動包含某些先前巨集的進階實作詳細資料包括如何清除堆疊式物件。  因為 C\+\+ 例外狀況預設回溯支援的堆疊，這個技術提示不再是必要的。  
  
 如需 MFC 巨集和新的 C\+\+ 關鍵字之間差異的詳細資訊，請參考 [例外狀況：使用 MFC 巨集和 C\+\+ 例外狀況](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) 。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)