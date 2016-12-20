---
title: "CMFCCaptionBar 類別 | Microsoft Docs"
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
  - "CMFCCaptionBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCCaptionBar 類別"
ms.assetid: acb54d5f-14ff-4c96-aeb3-7717cf566d9a
caps.latest.revision: 28
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCCaptionBar 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCCaptionBar` 物件是可顯示三個項目的控制列:按鈕、文字標籤和點陣圖。  它可以一次只會顯示每個型別的項目。  您可以對齊每個項目加入至控制項的左邊緣或右邊緣或到中央。  您也可以將一個平台或 3D 樣式套用至標題列上方與下方邊界。  
  
## 語法  
  
```  
class CMFCCaptionBar : public CPane  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCCaptionBar::Create](../Topic/CMFCCaptionBar::Create.md)|建立標題列控制項並將其附加至 `CMFCCaptionBar`物件。|  
|[CMFCCaptionBar::DoesAllowDynInsertBefore](../Topic/CMFCCaptionBar::DoesAllowDynInsertBefore.md)|表示另一個窗格是否可以動態地插入標題列及其父框架之間。  覆寫 \( [CBasePane::DoesAllowDynInsertBefore](../Topic/CBasePane::DoesAllowDynInsertBefore.md)\)。|  
|[CMFCCaptionBar::EnableButton](../Topic/CMFCCaptionBar::EnableButton.md)|啟用或停用在標題列中的按鈕。|  
|[CMFCCaptionBar::GetAlignment](../Topic/CMFCCaptionBar::GetAlignment.md)|傳回指定項目的對齊方式。|  
|[CMFCCaptionBar::GetBorderSize](../Topic/CMFCCaptionBar::GetBorderSize.md)|傳回現用視窗的框線大小。|  
|[CMFCCaptionBar::GetButtonRect](../Topic/CMFCCaptionBar::GetButtonRect.md)|擷取按鈕的週框 \(Bounding Rectangle\) 標題列。|  
|[CMFCCaptionBar::GetMargin](../Topic/CMFCCaptionBar::GetMargin.md)|傳回標題列項目的框線和標題列控制項的框線之間的距離。|  
|[CMFCCaptionBar::IsMessageBarMode](../Topic/CMFCCaptionBar::IsMessageBarMode.md)|指定標題列是否在訊息列模式。|  
|[CMFCCaptionBar::RemoveBitmap](../Topic/CMFCCaptionBar::RemoveBitmap.md)|從標題列移除點陣圖影像。|  
|[CMFCCaptionBar::RemoveButton](../Topic/CMFCCaptionBar::RemoveButton.md)|從標題列移除按鈕。|  
|[CMFCCaptionBar::RemoveIcon](../Topic/CMFCCaptionBar::RemoveIcon.md)|從標題列移除圖示。|  
|[CMFCCaptionBar::RemoveText](../Topic/CMFCCaptionBar::RemoveText.md)|從標題列中的文字標籤。|  
|[CMFCCaptionBar::SetBitmap](../Topic/CMFCCaptionBar::SetBitmap.md)|設定標題列的點陣圖影像。|  
|[CMFCCaptionBar::SetBorderSize](../Topic/CMFCCaptionBar::SetBorderSize.md)|設定標題列的框線大小。|  
|[CMFCCaptionBar::SetButton](../Topic/CMFCCaptionBar::SetButton.md)|設定標題列上的按鈕。|  
|[CMFCCaptionBar::SetButtonPressed](../Topic/CMFCCaptionBar::SetButtonPressed.md)|指定按鈕保持是否按下。|  
|[CMFCCaptionBar::SetButtonToolTip](../Topic/CMFCCaptionBar::SetButtonToolTip.md)|設定按鈕的工具提示。|  
|[CMFCCaptionBar::SetFlatBorder](../Topic/CMFCCaptionBar::SetFlatBorder.md)|設定標題列的框線樣式。|  
|[CMFCCaptionBar::SetIcon](../Topic/CMFCCaptionBar::SetIcon.md)|設定標題列圖示。|  
|[CMFCCaptionBar::SetImageToolTip](../Topic/CMFCCaptionBar::SetImageToolTip.md)|設定影像的工具提示標題列。|  
|[CMFCCaptionBar::SetMargin](../Topic/CMFCCaptionBar::SetMargin.md)|設定標題列項目的框線和標題列控制項的框線之間的距離。|  
|[CMFCCaptionBar::SetText](../Topic/CMFCCaptionBar::SetText.md)|設定標題列的文字標籤。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCCaptionBar::OnDrawBackground](../Topic/CMFCCaptionBar::OnDrawBackground.md)|由架構呼叫以填滿標題列的背景。|  
|[CMFCCaptionBar::OnDrawBorder](../Topic/CMFCCaptionBar::OnDrawBorder.md)|由架構呼叫以繪製標題列的框線。|  
|[CMFCCaptionBar::OnDrawButton](../Topic/CMFCCaptionBar::OnDrawButton.md)|由架構呼叫以繪製標題列按鈕。|  
|[CMFCCaptionBar::OnDrawImage](../Topic/CMFCCaptionBar::OnDrawImage.md)|由架構呼叫以繪製標題列影像。|  
|[CMFCCaptionBar::OnDrawText](../Topic/CMFCCaptionBar::OnDrawText.md)|由架構呼叫以繪製標題列文字。|  
  
### 資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CMFCCaptionBar::m\_clrBarBackground](../Topic/CMFCCaptionBar::m_clrBarBackground.md)|標題列的背景色彩。|  
|[CMFCCaptionBar::m\_clrBarBorder](../Topic/CMFCCaptionBar::m_clrBarBorder.md)|標題列的框線色彩。|  
|[CMFCCaptionBar::m\_clrBarText](../Topic/CMFCCaptionBar::m_clrBarText.md)|標題列文字的色彩。|  
  
## 備註  
 若要建立標題列，請依照下列步驟執行:  
  
1.  建構 `CMFCCaptionBar` 物件。  通常，您會將標題列加入框架視窗類別。  
  
2.  呼叫 [CMFCCaptionBar::Create](../Topic/CMFCCaptionBar::Create.md) 方法建立標題列控制項並將它附加至 `CMFCCaptionBar` 物件。  
  
3.  呼叫 [CMFCCaptionBar::SetButton](../Topic/CMFCCaptionBar::SetButton.md)、 [CMFCCaptionBar::SetText](../Topic/CMFCCaptionBar::SetText.md)、 [CMFCCaptionBar::SetIcon](../Topic/CMFCCaptionBar::SetIcon.md)和 [CMFCCaptionBar::SetBitmap](../Topic/CMFCCaptionBar::SetBitmap.md) 設定標題列項目。  
  
 當您將按鈕項目，您必須指定命令 ID 加入至按鈕。  當使用者按一下按鈕時，標題列傳送具有此 ID 加入至父框架視窗的 `WM_COMMAND` 訊息。  
  
 標題列在訊息列模式也可以運作，模擬訊息列出現在 Microsoft Office 2007 應用程式。  在訊息列模式，標題列中顯示點陣圖、訊息和通常會開啟對話方塊的按鈕\)。\(您可以將工具提示加入至點陣圖。  
  
 若要啟用訊息列方式，請呼叫 [CMFCCaptionBar::Create](../Topic/CMFCCaptionBar::Create.md) 並將第四個參數 \(bIsMessageBarMode\) 到 `TRUE`。  
  
## 範例  
 下列範例在 `CMFCCaptionBar` 類別示範如何使用各種方法。  這個範例顯示如何建立標題列控制項，將標題列之 3D 框線，請將距離，以像素為單位\)，在標題列項目的框線之間，以及標題列控制項，集合的邊緣標題列上的按鈕，請將按鈕的工具提示，設定標題列的文字標籤，則設定標題列的點陣圖影像，並設定影像的工具提示中的標題列。  這個程式碼片段是 [MS Office 2007 示範範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!CODE [NVC_MFC_MSOffice2007Demo#1](../CodeSnippet/VS_Snippets_Misc/NVC_MFC_MSOffice2007Demo#1)]  
[!CODE [NVC_MFC_MSOffice2007Demo#2](../CodeSnippet/VS_Snippets_Misc/NVC_MFC_MSOffice2007Demo#2)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCCaptionBar](../../mfc/reference/cmfccaptionbar-class.md)  
  
## 需求  
 **標題:** afxcaptionbar.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)