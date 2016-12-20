---
title: "CMFCLinkCtrl Class | Microsoft Docs"
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
  - "CMFCLinkCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCLinkCtrl class"
ms.assetid: 80f3874d-7cc8-410e-9ff1-62a225f5034b
caps.latest.revision: 27
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCLinkCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

當按一下按鈕時， `CMFCLinkCtrl` 類別來顯示一個按鈕為超連結 \(Hyperlink\) 和叫用連結的目標。  
  
## 語法  
  
```  
class CMFCLinkCtrl : public CMFCButton  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCLinkCtrl::SetURL](../Topic/CMFCLinkCtrl::SetURL.md)|顯示指定的 URL 做為按鈕文字。|  
|[CMFCLinkCtrl::SetURLPrefix](../Topic/CMFCLinkCtrl::SetURLPrefix.md)|設定為隱含通訊協定 \(例如， 「http: "\) 的 URL。|  
|[CMFCLinkCtrl::SizeToContent](../Topic/CMFCLinkCtrl::SizeToContent.md)|調整按鈕大小包含按鈕文字或點陣圖。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCLinkCtrl::OnDrawFocusRect](../Topic/CMFCLinkCtrl::OnDrawFocusRect.md)|呼叫由架構在按鈕的焦點矩形的動畫。|  
  
## 備註  
 當您按一下  `CMFCLinkCtrl` 從類別衍生的按鈕時，架構會將按鈕的 URL 當做參數傳遞至 `ShellExecute` 方法。  然後 `ShellExecute` 方法開啟 URL 的目標。  
  
## 範例  
 下列範例會示範如何設定 `CMFCLinkCtrl` 物件大小和如何設定 URL 和一個工具提示。 `CMFCLinkCtrl` 物件。  這個範例是 [新的控制項範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!CODE [NVC_MFC_NewControls#9](../CodeSnippet/VS_Snippets_Misc/NVC_MFC_NewControls#9)]  
[!CODE [NVC_MFC_NewControls#10](../CodeSnippet/VS_Snippets_Misc/NVC_MFC_NewControls#10)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
 [CMFCLinkCtrl](../../mfc/reference/cmfclinkctrl-class.md)  
  
## 需求  
 **標題:** afxlinkctrl.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CLinkCtrl Class](../../mfc/reference/clinkctrl-class.md)   
 [CMFCButton Class](../../mfc/reference/cmfcbutton-class.md)