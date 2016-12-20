---
title: "CMFCRibbonEdit Class | Microsoft Docs"
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
  - "CMFCRibbonEdit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonEdit class"
ms.assetid: 9b85f1f2-446b-454e-9af9-104fdad8a897
caps.latest.revision: 25
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonEdit Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作在功能區列上的編輯控制項。  
  
## 語法  
  
```  
class CMFCRibbonEdit : public CMFCRibbonButton  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonEdit::CMFCRibbonEdit](../Topic/CMFCRibbonEdit::CMFCRibbonEdit.md)|建構 `CMFCRibbonEdit` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonEdit::CanBeStretched](../Topic/CMFCRibbonEdit::CanBeStretched.md)|表示 `CMFCRibbonEdit` 控制項的高度是否可垂直加入至功能區列的高度。|  
|[CMFCRibbonEdit::CMFCRibbonEdit](../Topic/CMFCRibbonEdit::CMFCRibbonEdit.md)|建構 `CMFCRibbonEdit` 物件。|  
|[CMFCRibbonEdit::CopyFrom](../Topic/CMFCRibbonEdit::CopyFrom.md)|複製指定的 `CMFCRibbonEdit` 物件的狀態為目前 `CMFCRibbonEdit` 物件的。|  
|[CMFCRibbonEdit::CreateEdit](../Topic/CMFCRibbonEdit::CreateEdit.md)|`CMFCRibbonEdit` 建立物件的新的文字方塊。|  
|[CMFCRibbonEdit::DestroyCtrl](../Topic/CMFCRibbonEdit::DestroyCtrl.md)|終結 `CMFCRibbonEdit` 物件。|  
|[CMFCRibbonEdit::DropDownList](../Topic/CMFCRibbonEdit::DropDownList.md)|下拉式清單方塊。|  
|[CMFCRibbonEdit::EnableSpinButtons](../Topic/CMFCRibbonEdit::EnableSpinButtons.md)|啟用和設定微調按鈕的範圍文字方塊中。|  
|[CMFCRibbonEdit::GetCompactSize](../Topic/CMFCRibbonEdit::GetCompactSize.md)|擷取物件的 `CFMCRibbonEdit` 袖珍型。|  
|[CMFCRibbonEdit::GetEditText](../Topic/CMFCRibbonEdit::GetEditText.md)|擷取文字方塊中的文字。|  
|[CMFCRibbonEdit::GetIntermediateSize](../Topic/CMFCRibbonEdit::GetIntermediateSize.md)|擷取 `CMFCRibbonEdit` 期間的物件大小。|  
|[CMFCRibbonEdit::GetTextAlign](../Topic/CMFCRibbonEdit::GetTextAlign.md)|擷取文字的對齊方式在文字方塊中。|  
|[CMFCRibbonEdit::GetWidth](../Topic/CMFCRibbonEdit::GetWidth.md)|擷取的寬度，以像素為單位， `CMFCRibbonEdit` 控制項。|  
|[CMFCRibbonEdit::HasCompactMode](../Topic/CMFCRibbonEdit::HasCompactMode.md)|表示 `CMFCRibbonEdit` 顯示控制項的大小是否可以是壓縮的。|  
|[CMFCRibbonEdit::HasFocus](../Topic/CMFCRibbonEdit::HasFocus.md)|`CMFCRIbbonEdit` 指出控制項是否擁有焦點。|  
|[CMFCRibbonEdit::HasLargeMode](../Topic/CMFCRibbonEdit::HasLargeMode.md)|表示 `CMFCRibbonEdit` 顯示控制項的大小是否會很大。|  
|[CMFCRibbonEdit::HasSpinButtons](../Topic/CMFCRibbonEdit::HasSpinButtons.md)|表示文字方塊是否有微調按鈕。|  
|[CMFCRibbonEdit::IsHighlighted](../Topic/CMFCRibbonEdit::IsHighlighted.md)|`CMFCRibbonEdit` 指出控制項是否會反白顯示。|  
|[CMFCRibbonEdit::OnAfterChangeRect](../Topic/CMFCRibbonEdit::OnAfterChangeRect.md)|呼叫框架，同時顯示矩形的維度 `CMFCRibbonEdit` 變更的。|  
|[CMFCRibbonEdit::OnDraw](../Topic/CMFCRibbonEdit::OnDraw.md)|呼叫框架 `CMFCRibbonEdit` 繪製控制項。|  
|[CMFCRibbonEdit::OnDrawLabelAndImage](../Topic/CMFCRibbonEdit::OnDrawLabelAndImage.md)|呼叫框架繪製標籤和影像 `CMFCRibbonEdit` 控制項。|  
|[CMFCRibbonEdit::OnDrawOnList](../Topic/CMFCRibbonEdit::OnDrawOnList.md)|呼叫框架會在命令清單方塊的 `CMFCRibbonEdit` 控制項。|  
|[CMFCRibbonEdit::OnEnable](../Topic/CMFCRibbonEdit::OnEnable.md)|呼叫框架 `CMFCRibbonEdit` 啟用或停用控制項。|  
|[CMFCRibbonEdit::OnHighlight](../Topic/CMFCRibbonEdit::OnHighlight.md)|呼叫框架，當游標進入或離開 `CMFCRibbonEdit` 控制項的範圍。|  
|[CMFCRibbonEdit::OnKey](../Topic/CMFCRibbonEdit::OnKey.md)|呼叫，便會由架構使用者按下時 keytip 和 `CMFCRibbonEdit` 控制項擁有焦點。|  
|[CMFCRibbonEdit::OnLButtonDown](../Topic/CMFCRibbonEdit::OnLButtonDown.md)|呼叫框架更新 `CMFCRibbonEdit` 控制項，當使用者在控制項上按下滑鼠左鍵的。|  
|[CMFCRibbonEdit::OnLButtonUp](../Topic/CMFCRibbonEdit::OnLButtonUp.md)|呼叫框架，使用者放開滑鼠左鍵。|  
|[CMFCRibbonEdit::OnRTLChanged](../Topic/CMFCRibbonEdit::OnRTLChanged.md)|呼叫框架更新 `CMFCRibbonEdit` 控制項，在設定重新導向。|  
|[CMFCRibbonEdit::OnShow](../Topic/CMFCRibbonEdit::OnShow.md)|呼叫由架構來顯示或隱藏 `CMFCRibbonEdit` 控制項。|  
|[CMFCRibbonEdit::Redraw](../Topic/CMFCRibbonEdit::Redraw.md)|`CMFCRibbonEdit` 更新控制項的顯示。|  
|[CMFCRibbonEdit::SetACCData](../Topic/CMFCRibbonEdit::SetACCData.md)|設定協助工具的資料。 `CMFCRibbonEdit` 物件。|  
|[CMFCRibbonEdit::SetEditText](../Topic/CMFCRibbonEdit::SetEditText.md)|將文字方塊中的文字。|  
|[CMFCRibbonEdit::SetTextAlign](../Topic/CMFCRibbonEdit::SetTextAlign.md)|設定文字方塊的文字對齊方式。|  
|[CMFCRibbonEdit::SetWidth](../Topic/CMFCRibbonEdit::SetWidth.md)|設定文字方塊的寬度 `CMFCRibbonEdit` 控制項。|  
  
## 備註  
  
## 範例  
 下列範例示範如何建構 `CMFCRibbonEdit` 物件，示範在編輯控制項旁的微調按鈕，並將編輯控制項的文字。  這個程式碼片段是 [MS Office 2007 示範範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!CODE [NVC_MFC_MSOffice2007Demo#7](../CodeSnippet/VS_Snippets_Misc/NVC_MFC_MSOffice2007Demo#7)]  
  
## 需求  
 **標題:** afxRibbonEdit.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton Class](../../mfc/reference/cmfcribbonbutton-class.md)   
 [CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md)