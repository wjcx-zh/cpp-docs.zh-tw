---
title: "CMFCMenuButton 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCMenuButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCMenuButton 類別"
ms.assetid: 53d3d459-1e5a-47c5-8b7f-2e61f6af5187
caps.latest.revision: 32
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 34
---
# CMFCMenuButton 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

顯示快顯功能表和報告使用者功能表選取的按鈕。  
  
## 語法  
  
```  
class CMFCMenuButton : public CMFCButton  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCMenuButton::CMFCMenuButton](../Topic/CMFCMenuButton::CMFCMenuButton.md)|建構 `CMFCMenuButton` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCMenuButton::PreTranslateMessage](../Topic/CMFCMenuButton::PreTranslateMessage.md)|由架構呼叫以將 Windows 訊息，在分派前。  覆寫 \( `CMFCButton::PreTranslateMessage`\)。|  
|[CMFCMenuButton::SizeToContent](../Topic/CMFCMenuButton::SizeToContent.md)|根據其文字和影像大小變更按鈕的大小。|  
  
### 資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CMFCMenuButton::m\_bOSMenu](../Topic/CMFCMenuButton::m_bOSMenu.md)|指定是否顯示預設系統快顯功能表或使用 [CContextMenuManager::TrackPopupMenu](../Topic/CContextMenuManager::TrackPopupMenu.md)。|  
|[CMFCMenuButton::m\_bRightArrow](../Topic/CMFCMenuButton::m_bRightArrow.md)|指定快顯功能表是否在下會發生在按鈕的右邊。|  
|[CMFCMenuButton::m\_bStayPressed](../Topic/CMFCMenuButton::m_bStayPressed.md)|指定功能表按鈕是否在使用者版本之後變更其狀態按鈕。|  
|[CMFCMenuButton::m\_hMenu](../Topic/CMFCMenuButton::m_hMenu.md)|要附加的 Windows 功能表的控制代碼。|  
|[CMFCMenuButton::m\_nMenuResult](../Topic/CMFCMenuButton::m_nMenuResult.md)|這個識別項項目使用者從快顯功能表中選取的指示。|  
  
## 備註  
 從 [CButton Class](../../mfc/reference/cbutton-class.md)，然後，衍生的 `CMFCMenuButton` 類別衍生自 [CMFCButton Class](../../mfc/reference/cmfcbutton-class.md) 。  因此，您可以使用 `CMFCMenuButton` 在程式碼中會使用 `CButton`的方式。  
  
 在建立 `CMFCMenuButton`時，可以在控制代碼必須傳遞給相關聯的快顯功能表。  接著，呼叫 `CMFCMenuButton::SizeToContent`函式。  `CMFCMenuButton::SizeToContent` 會檢查按鈕大小足以包含即指向位置快顯視窗會顯示\)，或在下面按鈕右邊的箭頭。  
  
## 範例  
 下列範例示範如何將功能表的控制代碼附加到按鈕，根據其文字和影像大小調整按鈕的大小，並將由架構所顯示的快顯功能表。  這個程式碼片段是 [新的控制項範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!CODE [NVC_MFC_NewControls#38](../CodeSnippet/VS_Snippets_Misc/NVC_MFC_NewControls#38)]  
[!CODE [NVC_MFC_NewControls#39](../CodeSnippet/VS_Snippets_Misc/NVC_MFC_NewControls#39)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
 [CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)  
  
## 需求  
 **標題:** afxmenubutton.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCButton Class](../../mfc/reference/cmfcbutton-class.md)