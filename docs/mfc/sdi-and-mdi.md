---
title: "SDI 和 MDI | Microsoft Docs"
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
helpviewer_keywords: 
  - "框架視窗, MDI 應用程式"
  - "框架視窗, SDI 應用程式"
  - "MDI, 和 SDI 的比較"
  - "MFC, 視窗"
  - "單一文件介面 (SDI), 應用程式"
ms.assetid: bb7239d9-4759-4f63-bfff-44a04b48c067
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SDI 和 MDI
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 可與單一文件介面 \(SDI\) \(SDI\) 和多重文件一起使用連接 \(MDI\) 應用程式。  
  
 SDI 應用程式一次只允許一個開啟的文件框架視窗。  MDI 應用程式允許多重文件框架視窗中開啟應用程式的相同執行個體。  MDI 應用程式中有多個 MDI 子視窗，是框架視窗，可以開啟的視窗中，含有不同資料的每個。  在某些應用程式中，子視窗可以是不同的型別，例如圖表視窗和報告視窗。  在這種情況下，，如同的 MDI 子視窗不同類型啟動，功能表列會變更。  
  
> [!NOTE]
>  在 Windows 95 中，因為作業系統採用了「文件置中的檢視，以及之後，應用程式通常是 SDI。  
  
 如需詳細資訊，請參閱 [文件、檢視和架構](../mfc/documents-views-and-the-framework.md)。  
  
## 請參閱  
 [使用類別來編寫 Windows 應用程式](../mfc/using-the-classes-to-write-applications-for-windows.md)