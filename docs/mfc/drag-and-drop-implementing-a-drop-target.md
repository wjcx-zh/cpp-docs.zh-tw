---
title: "拖放：實作置放目標 | Microsoft Docs"
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
  - "拖放, 置放目標"
  - "OLE 拖放, 置放目標"
  - "OLE 拖放, 實作置放目標"
ms.assetid: 0689f1ec-5326-4008-b226-4b373c881358
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 拖放：實作置放目標
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文概述如何讓應用程式置放目標。  實作置放目標版本實作置放來源採用稍微更多工作，不過，它仍然是相當簡單。  這些技術也套用至非 OLE 應用程式。  
  
#### 實作置放目標。  
  
1.  將 10% 成員變數加入至您要做為置放目標的應用程式中的每個檢視。  這個成員變數必須從它衍生的型別是 `COleDropTarget` 或類別。  
  
2.  從處理 `WM_CREATE` 訊息的檢視類別函式 \(一般為 `OnCreate`\)，請呼叫新成員變數的 `Register` 成員函式。  排程器，`Revoke` 將會自動呼叫您的意圖。  
  
3.  覆寫下列函式。  如果您想要在應用程式中的相同的行為，請覆寫您的檢視類別的這些函式。  如果您要修改行為在不同案例中或要啟用置放在非`CView` 視窗，請覆寫您的 `COleDropTarget`的這些函式的衍生類別。  
  
    |覆寫|允許|  
    |--------|--------|  
    |`OnDragEnter`|在視窗發生置放作業。  當游標第一次進入視窗時呼叫。|  
    |`OnDragLeave`|在拖曳作業將指定的視窗時的特殊行為。|  
    |`OnDragOver`|在視窗發生置放作業。  在游標跨視窗拖曳時呼叫。|  
    |`OnDrop`|置放入指定之視窗的資料處理。|  
    |`OnScrollBy`|特殊行為，當移動所需的目標視窗。|  
  
 請參閱 MFC OLE 範例[OCLIENT](../top/visual-cpp-samples.md) 中部分範例的 MAINVIEW.CPP 檔案示範這些函式如何一起運作。  
  
 如需詳細資訊，請參閱：  
  
-   [實作置放來源](../mfc/drag-and-drop-implementing-a-drop-source.md)  
  
-   [建立和終結的 OLE 資料物件和資料來源](../mfc/data-objects-and-data-sources-creation-and-destruction.md)  
  
-   [管理OLE資料物件和資料來源](../mfc/data-objects-and-data-sources-manipulation.md)  
  
## 請參閱  
 [拖放 \(OLE\)](../mfc/drag-and-drop-ole.md)   
 [COleDropTarget Class](../mfc/reference/coledroptarget-class.md)