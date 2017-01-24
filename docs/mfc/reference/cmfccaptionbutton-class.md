---
title: "CMFCCaptionButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCCaptionButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCCaptionButton class"
ms.assetid: c5774b38-c0dd-414a-9ede-3b2f78f233ec
caps.latest.revision: 28
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCCaptionButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCCaptionButton` 類別實作會在停駐窗格或小型框架視窗的標題列中顯示的按鈕。  通常，這個架構便會自動建立標題按鈕。  
  
## 語法  
  
```  
class CMFCCaptionButton : public CObject  
```  
  
## Members  
  
### 建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCCaptionButton::CMFCCaptionButton](../Topic/CMFCCaptionButton::CMFCCaptionButton.md)|CMFCCaptionButton 建構物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCCaptionButton::GetHit](../Topic/CMFCCaptionButton::GetHit.md)|傳回表示按鈕的命令。|  
|[CMFCCaptionButton::GetIconID](../Topic/CMFCCaptionButton::GetIconID.md)|傳回影像 ID 與按鈕。|  
|[CMFCCaptionButton::GetRect](../Topic/CMFCCaptionButton::GetRect.md)|傳回按鈕佔用的矩形。|  
|[CMFCCaptionButton::GetSize](../Topic/CMFCCaptionButton::GetSize.md)|會傳回按鈕的寬度和高度。|  
|[CMFCCaptionButton::IsMiniFrameButton](../Topic/CMFCCaptionButton::IsMiniFrameButton.md)|指示標題列高度是否設定為微大小。|  
|[CMFCCaptionButton::Move](../Topic/CMFCCaptionButton::Move.md)|設定按鈕的位置和  視窗會顯示狀態。|  
|[CMFCCaptionButton::OnDraw](../Topic/CMFCCaptionButton::OnDraw.md)|繪製標題按鈕。|  
|[CMFCCaptionButton::SetMiniFrameButton](../Topic/CMFCCaptionButton::SetMiniFrameButton.md)|設定標題列的迷你大小。|  
  
## 備註  
 您可以從 [CPaneFrameWnd Class](../../mfc/reference/cpaneframewnd-class.md) 衍生類別並使用受保護的方法， `AddButton`，加入標題按鈕加入至微型框架視窗。  
  
 CPaneFrameWnd.h 定義標題按鈕的兩種類型的命令 ID:  
  
-   `AFX_CAPTION_BTN_PIN`，顯示固定按鈕，當停駐窗格支援自動隱藏模式。  
  
-   `AFX_CAPTION_BTN_CLOSE`，顯示 \[**關閉**\] 按鈕，當窗格可以關閉或隱藏。  
  
## 範例  
 下列範例示範如何建構 `CMFCCaptionButton` 物件和設定標題列的迷你大小。  
  
 [!code-cpp[NVC_MFC_RibbonApp#43](../../mfc/reference/codesnippet/CPP/cmfccaptionbutton-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCCaptionButton](../../mfc/reference/cmfccaptionbutton-class.md)  
  
## 需求  
 **標題:** afxcaptionbutton.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CPaneFrameWnd Class](../../mfc/reference/cpaneframewnd-class.md)   
 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md)