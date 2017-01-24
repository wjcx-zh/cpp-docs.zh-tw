---
title: "架構中的對話方塊元件 | Microsoft Docs"
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
  - "對話方塊類別, 對話方塊元件"
  - "對話方塊範本, MFC 架構"
  - "MFC 對話方塊, 關於 MFC 對話方塊"
  - "MFC 對話方塊, 建立"
  - "MFC 對話方塊, 對話方塊資源"
ms.assetid: 592db160-0a8a-49be-ac72-ead278aca53f
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 架構中的對話方塊元件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 MFC 架構，對話方塊有兩個元件：  
  
-   指定對話方塊的控制項和其位置的對話方塊範本資源。  
  
     對話方塊資源從 Windows 建立對話方塊視窗的地方儲存對話方塊範本，並顯示。  樣板指定對話方塊的特性，包括它的大小、位置、樣式和對話方塊的控制項型別和位置。  您通常會使用儲存的對話方塊範本作為資源，不過您也可以在記憶體中建立自己的範本。  
  
-   對話方塊類別，衍生自 [CDialog](../mfc/reference/cdialog-class.md)，提供管理對話方塊的程式設計介面。  
  
     當可見時，對話方塊是視窗，並且會附加到 Windows 的視窗。  當對話方塊視窗建立時，會建立對話方塊樣板資源做為範本建立子視窗控制項對話方塊。  
  
## 請參閱  
 [對話方塊](../mfc/dialog-boxes.md)   
 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)