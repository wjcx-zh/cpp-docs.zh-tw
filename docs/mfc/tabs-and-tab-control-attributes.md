---
title: "索引標籤和索引標籤控制項屬性 | Microsoft Docs"
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
  - "屬性 [C++], 參考主題"
  - "CTabCtrl 類別, 索引標籤控制項屬性"
  - "索引標籤控制項, 屬性"
  - "索引標籤"
  - "索引標籤, 屬性"
ms.assetid: ecf190cb-f323-4751-bfdb-766dbe6bb553
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 索引標籤和索引標籤控制項屬性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您對外觀的相當整理選項控制選項的控制項和行為 \([CTabCtrl](../mfc/reference/ctabctrl-class.md)\)。  每個選項可能有標籤、圖示、項目狀態和應用程式定義的 32 位元值與它。  對於每個索引標籤，可以顯示圖示，標籤或兩者。  
  
 此外，每個索引標籤項目可以有三個可能的狀態:按，解壓縮或反白顯示。  這個狀態可以修改現有的索引標籤項目只設定。  若要修改現有的索引標籤項目，請擷取它與呼叫 [GetItem](../Topic/CTabCtrl::GetItem.md)，修改 `TCITEM` 結構 \(特別是 **dwState** 和 **dwStateMask** 資料成員\)，然後傳回與呼叫中修改的 `TCITEM` 結構轉換為 [SetItem](../Topic/CTabCtrl::SetItem.md)。  如果您需要清除項目狀態 `CTabCtrl` 中所有索引標籤項目物件，呼叫 [DeselectAll](../Topic/CTabCtrl::DeselectAll.md)。  這個函式會將所有索引標籤項目或所有項目的狀態，但目前選取的項目。  
  
 下列程式碼會清除這個狀態所有索引標籤項目並修改第三個項目的狀態:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#32](../mfc/codesnippet/CPP/tabs-and-tab-control-attributes_1.cpp)]  
  
 如需選項屬性的詳細資訊，請參閱 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]的 [選項以及屬性](http://msdn.microsoft.com/library/windows/desktop/bb760550) 。  如需加入選項的詳細資訊加入至索引標籤控制項，請參閱本主題稍後的 [將選項加入至索引標籤控制項](../mfc/adding-tabs-to-a-tab-control.md) 。  
  
## 請參閱  
 [使用 CTabCtrl](../mfc/using-ctabctrl.md)   
 [控制項](../mfc/controls-mfc.md)