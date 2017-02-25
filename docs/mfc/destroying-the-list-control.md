---
title: "終結清單控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CListCtrl 類別, 終結控制項"
  - "清單控制項, 終結"
ms.assetid: 513ec820-3a02-49d2-b073-a6a7a3fc91b3
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 終結清單控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果您將您的 [CListCtrl](../mfc/reference/clistctrl-class.md) 物件，在終結檢視或對話方塊類別，它的資料成員，在終結它的擁有人。  如果您使用 [CListView](../mfc/reference/clistview-class.md)，架構會終結控制項，以在終結檢視時。  
  
 如果您在應用程式中儲存某些清單資料而不是清單控制項，您必須將其解除配置。  在 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]\(如需詳細資訊，請參閱 [回呼項目和回呼遮罩](http://msdn.microsoft.com/library/windows/desktop/bb774736) 。  
  
 此外，您必須負責解除配置您建立並與清單控制項的影像清單。  
  
## 請參閱  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控制項](../mfc/controls-mfc.md)