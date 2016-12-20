---
title: "交換資料 | Microsoft Docs"
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
  - "DDX (對話資料交換), 屬性工作表"
  - "與屬性工作表交換資料"
  - "屬性工作表, 資料交換"
ms.assetid: 689f02d0-51a9-455b-8ffb-5b44f0aefa28
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 交換資料
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如同大多數對話方塊，在屬性工作表和應用程式之間的交換資料是其中一個屬性工作表的最重要的函式。  本文說明如何完成這項工作。  
  
 藉由屬性工作表交換資料實際上是交換具有屬性工作表之個別屬性頁的資料的問題。  因為 [CPropertyPage](../mfc/reference/cpropertypage-class.md) 物件是特殊的 [CDialog](../mfc/reference/cdialog-class.md) 物件，使用屬性頁交換資料的方法相同於對話方塊的交換。  程序使用架構的對話資料交換 \(Dialog Data Exchange，DDX\) 機制的糾點，在對話方塊中的控制項和對話方塊物件的成員變數之間交換資料。  
  
 使用屬性工作表交換資料與使用一般對話方塊之間的重要差異為屬性工作表有多頁，因此，您必須使用所有在屬性工作表中的屬性頁交換資料。  如需有關 DDX 的詳細資訊，請參閱[對話資料交換和驗證](../mfc/dialog-data-exchange-and-validation.md)。  
  
 下列範例說明在檢視和屬性工作表的兩夜之間交換資料：  
  
 [!code-cpp[NVC_MFCDocView#4](../mfc/codesnippet/CPP/exchanging-data_1.cpp)]  
  
## 請參閱  
 [屬性工作表](../mfc/property-sheets-mfc.md)