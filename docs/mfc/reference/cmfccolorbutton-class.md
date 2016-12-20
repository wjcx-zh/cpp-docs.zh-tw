---
title: "CMFCColorButton Class | Microsoft Docs"
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
  - "CMFCColorButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCColorButton class"
  - "CMFCColorButton::m_bAltColorDlg data member"
  - "CMFCColorButton::m_bAutoSetFocus data member"
  - "CMFCColorButton::m_Color data member"
  - "CMFCColorButton::m_ColorAutomatic data member"
  - "CMFCColorButton::m_lstDocColors data member"
  - "CMFCColorButton::m_nColumns data member"
  - "CMFCColorButton::m_pPalette data member"
  - "CMFCColorButton::m_pPopup data member"
  - "CMFCColorButton::m_strAutoColorText data member"
  - "CMFCColorButton::m_strDocColorsText data member"
  - "CMFCColorButton::m_strOtherText data member"
ms.assetid: 9fdf34ae-4cc5-4c5e-9d89-1c50e8a73699
caps.latest.revision: 34
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCColorButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCColorButton` 和 [CMFCColorBar Class](../../mfc/reference/cmfccolorbar-class.md) 類別一起用來實作色彩選擇器控制項。  
  
## 語法  
  
```  
class CMFCColorButton : public CMFCButton  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCColorButton::CMFCColorButton](../Topic/CMFCColorButton::CMFCColorButton.md)|建構新的 `CMFCColorButton` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCColorButton::EnableAutomaticButton](../Topic/CMFCColorButton::EnableAutomaticButton.md)|啟用和停用規則色彩按鈕上的「Auto」按鈕。  \(標準系統自動按鈕標記 \[**自動**\]\)。|  
|[CMFCColorButton::EnableOtherButton](../Topic/CMFCColorButton::EnableOtherButton.md)|啟用和停用規則色彩\] 按鈕下方定位「其他」按鈕。  \(標準系統「其他」按鈕標記 \[**更多色彩…**\]\)。|  
|[CMFCColorButton::GetAutomaticColor](../Topic/CMFCColorButton::GetAutomaticColor.md)|擷取目前的自動色彩。|  
|[CMFCColorButton::GetColor](../Topic/CMFCColorButton::GetColor.md)|擷取按鈕的色彩。|  
|[CMFCColorButton::SetColor](../Topic/CMFCColorButton::SetColor.md)|將按鈕的色彩。|  
|[CMFCColorButton::SetColorName](../Topic/CMFCColorButton::SetColorName.md)|設定色彩名稱。|  
|[CMFCColorButton::SetColumnsNumber](../Topic/CMFCColorButton::SetColumnsNumber.md)|設定資料行數色彩選擇器對話方塊中的。|  
|[CMFCColorButton::SetDocumentColors](../Topic/CMFCColorButton::SetDocumentColors.md)|指定在色彩選擇器對話方塊中顯示文件特定色彩的清單。|  
|[CMFCColorButton::SetPalette](../Topic/CMFCColorButton::SetPalette.md)|指定標準顯示色板。|  
|[CMFCColorButton::SizeToContent](../Topic/CMFCColorButton::SizeToContent.md)|根據它的文字和影像大小變更按鈕控制項的大小。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCColorButton::IsDrawXPTheme](../Topic/CMFCColorButton::IsDrawXPTheme.md)|指出目前色彩按鈕是否在 Windows XP 視覺化樣式顯示。|  
|[CMFCColorButton::OnDraw](../Topic/CMFCColorButton::OnDraw.md)|呼叫框架的按鈕顯示影像。|  
|[CMFCColorButton::OnDrawBorder](../Topic/CMFCColorButton::OnDrawBorder.md)|呼叫由架構會顯示按鈕的框線。|  
|[CMFCColorButton::OnDrawFocusRect](../Topic/CMFCColorButton::OnDrawFocusRect.md)|呼叫框架顯示焦點矩形，當按鈕具有焦點。|  
|[CMFCColorButton::OnShowColorPopup](../Topic/CMFCColorButton::OnShowColorPopup.md)|呼叫框架，該色彩選擇器對話方塊隨即顯示。|  
|[CMFCColorButton::RebuildPalette](../Topic/CMFCColorButton::RebuildPalette.md)|初始化 `m_pPalette` 保護資料成員設定為指定的調色盤或預設系統調色盤。|  
|[CMFCColorButton::UpdateColor](../Topic/CMFCColorButton::UpdateColor.md)|呼叫框架，當使用者選取色彩從色彩選擇器對話方塊中的調色盤。|  
  
### 資料成員  
  
|名稱|描述|  
|--------|--------|  
|`m_bAltColorDlg`|布林值。  如果 `TRUE`，架構會顯示 [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) 色彩對話方塊，而 *另一個* 按鈕被按下，則為，如果 `FALSE`，系統色彩對話方塊。  預設值是 `TRUE`。  如需詳細資訊，請參閱 [CMFCColorButton::EnableOtherButton](../Topic/CMFCColorButton::EnableOtherButton.md)。|  
|`m_bAutoSetFocus`|布林值。  如果 `TRUE`，架構會將色彩功能表的焦點，當功能表顯示，則為，如果 `FALSE`，不變更焦點。  預設值是 `TRUE`。|  
|[CMFCColorButton::m\_bEnabledInCustomizeMode](../Topic/CMFCColorButton::m_bEnabledInCustomizeMode.md)|表示自訂方式是否為色彩按鈕啟動。|  
|`m_Color`|[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) 值。  包含目前選取的色彩。|  
|`m_ColorAutomatic`|[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) 值。  包含目前選取的預設色彩。|  
|`m_Colors`|[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) 值 [CArray](../../mfc/reference/carray-class.md) 。  包含目前可用的色彩。|  
|`m_lstDocColors`|[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) 值 [CList](../../mfc/reference/clist-class.md) 。  包含目前文件的色彩。|  
|`m_nColumns`|整數。  在色彩方格中的資料行數目顯示色彩選擇功能表上的。|  
|`m_pPalette`|為 [CPalette](../../mfc/reference/cpalette-class.md)的指標。  包含可供目前色彩選取功能表的色彩。|  
|`m_pPopup`|為 [CMFCColorPopupMenu Class](../../mfc/reference/cmfccolorpopupmenu-class.md) 物件的指標。  顯示的色彩選取功能表上的 ，然後按一下  按鈕的色彩。|  
|`m_strAutoColorText`|字串。  「auto」按鈕的標籤在色彩選取功能表上的。|  
|`m_strDocColorsText`|字串。  按鈕的標籤以顯示文件色彩的色彩選取功能表上的。|  
|`m_strOtherText`|字串。  「另一個是」按鈕的標籤在色彩選取功能表上的。|  
  
## 備註  
 根據預設， `CMFCColorButton` 類別做為開啟色彩選擇器對話方塊中的按鈕。  色彩選擇器對話方塊中顯示自訂色彩選擇器的陣列小色彩按鈕和「其他」按鈕。  \(標準系統「其他」按鈕標記 \[**更多色彩…**\]\)。當使用者選取新的色彩時， `CMFCColorButton` 物件會反映這些變更並顯示所選取的色彩。  
  
 建立一個色彩按鈕控制項直接在您的程式碼，或是使用 \[**ClassWizard**\] 工具和對話方塊範本。  如果您直接建立色彩按鈕控制項，請將 `CMFCColorButton` 變數加入您的應用程式，然後呼叫建構函式，並 `CMFCColorButton` 的 `Create` 方法。  如果您使用 \[**ClassWizard**\]，請將 `CButton` 變數加入您的應用程式，然後從 `CButton` 變更引數的型別轉換為 `CMFCColorButton`。  
  
 色彩選擇器對話方塊 \([CMFCColorBar Class](../../mfc/reference/cmfccolorbar-class.md)\) 是 [CMFCColorButton::OnShowColorPopup](../Topic/CMFCColorButton::OnShowColorPopup.md) 方法時，便會顯示這個框架呼叫 `OnLButtonDown` 事件處理常式時。  [CMFCColorButton::OnShowColorPopup](../Topic/CMFCColorButton::OnShowColorPopup.md) 方法可以覆寫成支援自訂色彩的選項。  
  
 `CMFCColorButton` 物件告知其父色彩將變更傳送至 `WM_COMMAND | BN_CLICKED` 告知。  父代 [CMFCColorButton::GetColor](../Topic/CMFCColorButton::GetColor.md) 使用方法擷取目前色彩。  
  
## 範例  
 您可以使用類別，在 `CMFCColorButton` 的各種方法。下列範例將示範如何設定按鈕的色彩。  方法會將色彩按鈕和其資料列的色彩，並啟用自動和其他按鈕。  這個範例是 [狀態列示範範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_StatusBarDemo#10](../../mfc/reference/codesnippet/CPP/cmfccolorbutton-class_1.h)]  
[!code-cpp[NVC_MFC_StatusBarDemo#11](../../mfc/reference/codesnippet/CPP/cmfccolorbutton-class_2.cpp)]  
  
## 需求  
 **標題:** afxcolorbutton.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCButton Class](../../mfc/reference/cmfcbutton-class.md)   
 [CMFCColorBar Class](../../mfc/reference/cmfccolorbar-class.md)   
 [CMFCColorButton::OnShowColorPopup](../Topic/CMFCColorButton::OnShowColorPopup.md)   
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)   
 [CPalette Class](../../mfc/reference/cpalette-class.md)   
 [CArray Class](../../mfc/reference/carray-class.md)   
 [CList Class](../../mfc/reference/clist-class.md)   
 [CString](../../atl-mfc-shared/reference/cstringt-class.md)