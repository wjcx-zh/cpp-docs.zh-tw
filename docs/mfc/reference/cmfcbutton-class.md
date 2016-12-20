---
title: "CMFCButton Class | Microsoft Docs"
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
  - "CMFCButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCButton class"
  - "CMFCButton constructor"
  - "CMFCButton::CreateObject method"
  - "CMFCButton::DrawItem method"
  - "CMFCButton::OnDrawParentBackground method"
  - "CMFCButton::PreTranslateMessage method"
ms.assetid: 4b32f57c-7a53-4734-afb9-d47e3359f62e
caps.latest.revision: 35
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCButton` 類別將功能加入至 [CButton](../../mfc/reference/cbutton-class.md) 類別 \(例如對齊按鈕文字，結合了按鈕文字和影像，選取游標和指定工具提示。  
  
## 語法  
  
```  
class CMFCButton : public CButton  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|`CMFCButton::CMFCButton`|預設建構函式。|  
|`CMFCButton::~CMFCButton`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCButton::CleanUp](../Topic/CMFCButton::CleanUp.md)|重設的內部變數並釋放配置的資源 \(例如影像、點陣圖和圖示。|  
|`CMFCButton::CreateObject`|由架構建立這個類別型別的動態執行個體。|  
|`CMFCButton::DrawItem`|呼叫框架，只有一個主控描繪 \(Owner\-Drawn\) 按鈕的視覺外觀變更時。  \(覆寫 [CButton::DrawItem](../Topic/CButton::DrawItem.md)\)。|  
|[CMFCButton::EnableFullTextTooltip](../Topic/CMFCButton::EnableFullTextTooltip.md)|指定是否顯示為工具提示的文字會以工具提示視窗的或文字的截斷的版本在小型工具提示視窗的。|  
|[CMFCButton::EnableMenuFont](../Topic/CMFCButton::EnableMenuFont.md)|指定按鈕文字的字型是否與應用程式功能表字型。|  
|[CMFCButton::EnableWindowsTheming](../Topic/CMFCButton::EnableWindowsTheming.md)|指定按鈕的框線樣式是否符合目前 Windows 佈景主題。|  
|`CMFCButton::GetThisClass`|由框架以取得指向與這個類別型別的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件。|  
|[CMFCButton::GetToolTipCtrl](../Topic/CMFCButton::GetToolTipCtrl.md)|傳回基礎工具提示控制項的參考。|  
|[CMFCButton::IsAutoCheck](../Topic/CMFCButton::IsAutoCheck.md)|表示核取方塊或選項按鈕是否為自動按鈕。|  
|[CMFCButton::IsAutorepeatCommandMode](../Topic/CMFCButton::IsAutorepeatCommandMode.md)|指出是否設定為自動迴圈。|  
|[CMFCButton::IsCheckBox](../Topic/CMFCButton::IsCheckBox.md)|指出是否為核取方塊按鈕。|  
|[CMFCButton::IsChecked](../Topic/CMFCButton::IsChecked.md)|指示目前的按鈕是否已核取。|  
|[CMFCButton::IsHighlighted](../Topic/CMFCButton::IsHighlighted.md)|指出是否已反白顯示。|  
|[CMFCButton::IsPressed](../Topic/CMFCButton::IsPressed.md)|指出是否已按下並反白顯示。|  
|[CMFCButton::IsPushed](../Topic/CMFCButton::IsPushed.md)|會指示是否已按下按鈕。|  
|[CMFCButton::IsRadioButton](../Topic/CMFCButton::IsRadioButton.md)|指出是否為選項按鈕。|  
|[CMFCButton::IsWindowsThemingEnabled](../Topic/CMFCButton::IsWindowsThemingEnabled.md)|表示按鈕的框線樣式是否符合目前 Windows 佈景主題。|  
|`CMFCButton::OnDrawParentBackground`|繪製按鈕的父代背景指定區域的。  \(覆寫 [AFX\_GLOBAL\_DATA::DrawParentBackground](../Topic/AFX_GLOBAL_DATA::DrawParentBackground.md)\)。|  
|`CMFCButton::PreTranslateMessage`|包含會分派給 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式之前，將 Windows 訊息。  \(覆寫 [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md)\)。|  
|[CMFCButton::SetAutorepeatMode](../Topic/CMFCButton::SetAutorepeatMode.md)|將按鈕自動迴圈。|  
|[CMFCButton::SetCheckedImage](../Topic/CMFCButton::SetCheckedImage.md)|設定已選取之按鈕的影像。|  
|[CMFCButton::SetFaceColor](../Topic/CMFCButton::SetFaceColor.md)|設定按鈕文字的背景色彩。|  
|[CMFCButton::SetImage](../Topic/CMFCButton::SetImage.md)|將按鈕的影像。|  
|[CMFCButton::SetMouseCursor](../Topic/CMFCButton::SetMouseCursor.md)|設定游標影像。|  
|[CMFCButton::SetMouseCursorHand](../Topic/CMFCButton::SetMouseCursorHand.md)|設定游標相符的影像。|  
|[CMFCButton::SetStdImage](../Topic/CMFCButton::SetStdImage.md)|使用 `CMenuImages` 物件設定按鈕影像。|  
|[CMFCButton::SetTextColor](../Topic/CMFCButton::SetTextColor.md)|設定按鈕文字的色彩不會選取之按鈕的。|  
|[CMFCButton::SetTextHotColor](../Topic/CMFCButton::SetTextHotColor.md)|設定按鈕文字的色彩都已選取之按鈕的。|  
|[CMFCButton::SetTooltip](../Topic/CMFCButton::SetTooltip.md)|與相關聯的工具提示  按鈕。|  
|[CMFCButton::SizeToContent](../Topic/CMFCButton::SizeToContent.md)|調整按鈕大小包含它的按鈕文字和影像。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCButton::OnDraw](../Topic/CMFCButton::OnDraw.md)|呼叫由架構來繪製按鈕。|  
|[CMFCButton::OnDrawBorder](../Topic/CMFCButton::OnDrawBorder.md)|呼叫由架構分割按鈕的框線。|  
|[CMFCButton::OnDrawFocusRect](../Topic/CMFCButton::OnDrawFocusRect.md)|呼叫框架繪製按鈕的焦點矩形。|  
|[CMFCButton::OnDrawText](../Topic/CMFCButton::OnDrawText.md)|呼叫框架繪製按鈕文字。|  
|[CMFCButton::OnFillBackground](../Topic/CMFCButton::OnFillBackground.md)|呼叫框架繪製按鈕文字的背景。|  
|[CMFCButton::SelectFont](../Topic/CMFCButton::SelectFont.md)|擷取與指定之裝置內容的字型。|  
  
### 資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CMFCButton::m\_bDrawFocus](../Topic/CMFCButton::m_bDrawFocus.md)|表示是否要在按鈕四周繪製焦點矩形。|  
|[CMFCButton::m\_bHighlightChecked](../Topic/CMFCButton::m_bHighlightChecked.md)|當游標停留在它，是否要反白顯示 BS\_CHECKBOX\-style 按鈕。|  
|[CMFCButton::m\_bRightImage](../Topic/CMFCButton::m_bRightImage.md)|表示是否要在按鈕右邊顯示影像。|  
|[CMFCButton::m\_bTransparent](../Topic/CMFCButton::m_bTransparent.md)|指出是否啟用透明。|  
|[CMFCButton::m\_nAlignStyle](../Topic/CMFCButton::m_nAlignStyle.md)|指定按鈕文字的對齊方式。|  
|[CMFCButton::m\_nFlatStyle](../Topic/CMFCButton::m_nFlatStyle.md)|指定按鈕的樣式，例如無框線，平滑，或半水平 3D。|  
  
## 備註  
 按鈕的其他型別 `CMFCButton` 從類別衍生，例如 [CMFCURLLinkButton](../../mfc/reference/cmfclinkctrl-class.md) 類別，支援超連結和 `CMFCColorButton` 類別，支援色彩選擇器對話方塊。  
  
 `CMFCButton` 物件的模式可以是 *3D*， *平滑*， *一般* 或完全沒有框線。  按鈕文字可以靠左，頂端或按鈕的中央。  在執行階段，您可以控制按鈕是否顯示文字、影像、文字和影像。  您也可以指定特定游標會顯示影像，當游標停留在按鈕時。  
  
 建立按鈕控制項直接在您的程式碼，或是使用 \[**MFC 類別精靈**\] 工具和對話方塊範本。  如果您直接建立按鈕控制項，請將 `CMFCButton` 變數加入您的應用程式，然後呼叫建構函式，並 `CMFCButton` 的 `Create` 方法。  如果您使用 \[**MFC 類別精靈**\]，請將 `CButton` 變數加入您的應用程式，然後從 `CButton` 變更引數的型別轉換為 `CMFCButton`。  
  
 若要處理在對話方塊中應用程式的通知訊息，請加入訊息對應項目和事件處理常式會在每個告知的。  `CMFCButton` 物件傳送的告知數目相同。 `CButton` 物件傳送的項目。  
  
## 範例  
 您可以使用類別，在 `CMFCButton` 的各種方法。下列範例將示範如何設定按鈕的屬性。  這個範例是 [新的控制項範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!CODE [NVC_MFC_NewControls#28](../CodeSnippet/VS_Snippets_Misc/NVC_MFC_NewControls#28)]  
[!CODE [NVC_MFC_NewControls#31](../CodeSnippet/VS_Snippets_Misc/NVC_MFC_NewControls#31)]  
[!CODE [NVC_MFC_NewControls#32](../CodeSnippet/VS_Snippets_Misc/NVC_MFC_NewControls#32)]  
[!CODE [NVC_MFC_NewControls#33](../CodeSnippet/VS_Snippets_Misc/NVC_MFC_NewControls#33)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
## 需求  
 **標題:** afxbutton.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCLinkCtrl Class](../../mfc/reference/cmfclinkctrl-class.md)   
 [CMFCColorButton Class](../../mfc/reference/cmfccolorbutton-class.md)   
 [CMFCMenuButton 類別](../../mfc/reference/cmfcmenubutton-class.md)