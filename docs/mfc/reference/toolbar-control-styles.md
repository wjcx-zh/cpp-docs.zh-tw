---
title: "ToolBar 控制項樣式 | Microsoft Docs"
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
  - "ToolBar 控制項樣式"
ms.assetid: 0f717eb9-fa32-4263-b852-809238863feb
caps.latest.revision: 16
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ToolBar 控制項樣式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[CMFCToolBarButton Class](../../mfc/reference/cmfctoolbarbutton-class.md) 有一組決定按鈕的外觀和行為的樣式旗標。  您可以藉由呼叫 [CMFCToolBarButton::SetStyle](../Topic/CMFCToolBarButton::SetStyle.md)設定這些旗標的組合。  本主題列出樣式旗標值及其意義。  
  
## 屬性值  
 下列值決定控制項代表按鈕類型:  
  
 TBBS\_BUTTON  
 標準按鈕 \(預設值\)。  
  
 TBBS\_CHECKBOX  
 Check box  
  
 TBBS\_CHECKGROUP  
 核取方塊的開頭。  
  
 TBBS\_GROUP  
 按鈕群組的開頭。  
  
 TBBS\_SEPARATOR  
 Separator。  
  
 下列值表示控制項的目前狀態:  
  
 TBBS\_CHECKED  
 核取方塊已核取。  
  
 TBBS\_DISABLED  
 控制項已停用。  
  
 TBBS\_INDETERMINATE  
 核取方塊處於不定狀態。  
  
 TBBS\_PRESSED  
 按鈕已按下。  
  
 下列值變更按鈕的配置在工具列:  
  
 TBBS\_BREAK  
 將項目放在新的一行或一欄，而沒有建置該段餾資料。  
  
## 備註  
 目前的樣式、在 [CMFCToolBarButton::m\_nStyle](../Topic/CMFCToolBarButton::m_nStyle.md)中。  請勿直接在 `m_nStyle` 的新值，因為某些衍生類別執行額外的處理時呼叫 `SetStyles`。  
  
 視覺化管理員判斷每個狀態的按鈕外觀。  如需詳細資訊，請參閱[視覺化管理員](../../mfc/visualization-manager.md)。  
  
## 需求  
 **標題:** afxtoolbarbutton.h  
  
## 請參閱  
 [巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)   
 [CMFCToolBarButton Class](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [視覺化管理員](../../mfc/visualization-manager.md)