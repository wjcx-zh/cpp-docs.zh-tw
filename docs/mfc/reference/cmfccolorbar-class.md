---
title: "CMFCColorBar Class | Microsoft Docs"
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
  - "CMFCColorBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCColorBar class"
  - "CMFCColorBar::m_bInternal data member"
  - "CMFCColorBar::m_bIsEnabled data member"
  - "CMFCColorBar::m_bIsTearOff data member"
  - "CMFCColorBar::m_BoxSize data member"
  - "CMFCColorBar::m_bShowDocColorsWhenDocked data member"
  - "CMFCColorBar::m_bStdColorDlg data member"
  - "CMFCColorBar::m_ColorAutomatic data member"
  - "CMFCColorBar::m_ColorNames data member"
  - "CMFCColorBar::m_colors data member"
  - "CMFCColorBar::m_ColorSelected data member"
  - "CMFCColorBar::m_lstDocColors data member"
  - "CMFCColorBar::m_nCommandID data member"
  - "CMFCColorBar::m_nHorzMargin data member"
  - "CMFCColorBar::m_nHorzOffset data member"
  - "CMFCColorBar::m_nNumColumns data member"
  - "CMFCColorBar::m_nNumColumnsVert data member"
  - "CMFCColorBar::m_nNumRowsHorz data member"
  - "CMFCColorBar::m_nRowHeight data member"
  - "CMFCColorBar::m_nVertMargin data member"
  - "CMFCColorBar::m_nVertOffset data member"
  - "CMFCColorBar::m_Palette data member"
  - "CMFCColorBar::m_pParentBtn data member"
  - "CMFCColorBar::m_pParentRibbonBtn data member"
  - "CMFCColorBar::m_pWndPropList data member"
  - "CMFCColorBar::m_strAutoColor data member"
  - "CMFCColorBar::m_strDocColors data member"
  - "CMFCColorBar::m_strOtherColor data member"
ms.assetid: 4756ee40-25a5-4cee-af7f-acab7993d1c7
caps.latest.revision: 35
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCColorBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCColorBar` 類別表示可以選擇在文件或應用程式之色彩的內建的控制列。  
  
## 語法  
  
```  
class CMFCColorBar : public CMFCPopupMenuBar  
```  
  
## Members  
  
### 受保護的建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCColorBar::CMFCColorBar](../Topic/CMFCColorBar::CMFCColorBar.md)|建構 `CMFCColorBar` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCColorBar::ContextToSize](../Topic/CMFCColorBar::ContextToSize.md)|計算要包含在 \[色軸的按鈕控制項的垂直和水平框線然後調整這些按鈕的位置。|  
|[CMFCColorBar::CreateControl](../Topic/CMFCColorBar::CreateControl.md)|建立至色軸控制項視窗中，將它附加至 `CMFCColorBar` 物件，並調整控制項包含指定色彩的色板。|  
|[CMFCColorBar::Create](../Topic/CMFCColorBar::Create.md)|建立至色軸控制視窗並將其附加至 `CMFCColorBar` 物件。|  
|[CMFCColorBar::EnableAutomaticButton](../Topic/CMFCColorBar::EnableAutomaticButton.md)|顯示或隱藏自動按鈕。|  
|[CMFCColorBar::EnableOtherButton](../Topic/CMFCColorBar::EnableOtherButton.md)|啟用或停用可讓使用者選取多個色彩對話方塊的顯示。|  
|[CMFCColorBar::GetColor](../Topic/CMFCColorBar::GetColor.md)|擷取目前所選取的色彩。|  
|[CMFCColorBar::GetCommandID](../Topic/CMFCColorBar::GetCommandID.md)|擷取目前的色軸控制的命令 ID。|  
|[CMFCColorBar::GetHighlightedColor](../Topic/CMFCColorBar::GetHighlightedColor.md)|擷取表示色彩的色彩按鈕具有焦點，也就是按鈕作用中。|  
|[CMFCColorBar::GetHorzMargin](../Topic/CMFCColorBar::GetHorzMargin.md)|擷取水平框線，也就是在左側或右側色彩儲存格和工作區界限之間的空間。|  
|[CMFCColorBar::GetVertMargin](../Topic/CMFCColorBar::GetVertMargin.md)|擷取垂直框線，也就是在頂端之間的空間色彩或下方的儲存格和工作區界限。|  
|[CMFCColorBar::IsTearOff](../Topic/CMFCColorBar::IsTearOff.md)|指示目前的色軸是否可停駐。|  
|[CMFCColorBar::SetColor](../Topic/CMFCColorBar::SetColor.md)|設定目前選取的色彩。|  
|[CMFCColorBar::SetColorName](../Topic/CMFCColorBar::SetColorName.md)|設定新名稱指定的色彩。|  
|[CMFCColorBar::SetCommandID](../Topic/CMFCColorBar::SetCommandID.md)|設定為色軸控制項新的命令 ID。|  
|[CMFCColorBar::SetDocumentColors](../Topic/CMFCColorBar::SetDocumentColors.md)|設定用於目前文件的色彩清單。|  
|[CMFCColorBar::SetHorzMargin](../Topic/CMFCColorBar::SetHorzMargin.md)|設定水平框線，也就是在左側或右側色彩儲存格和工作區界限之間的空間。|  
|[CMFCColorBar::SetVertMargin](../Topic/CMFCColorBar::SetVertMargin.md)|設定垂直框線，也就是在頂端之間的空間色彩或下方的儲存格和工作區界限。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCColorBar::AdjustLocations](../Topic/CMFCColorBar::AdjustLocations.md)|調整色彩按鈕的位置在 \[色軸控制項。|  
|[CMFCColorBar::AllowChangeTextLabels](../Topic/CMFCColorBar::AllowChangeTextLabels.md)|表示色彩按鈕文字標籤是否可以變更。|  
|[CMFCColorBar::AllowShowOnList](../Topic/CMFCColorBar::AllowShowOnList.md)|表示對色軸控制物件是否可以出現在工具列上的  清單中的自訂處理序。|  
|[CMFCColorBar::CalcSize](../Topic/CMFCColorBar::CalcSize.md)|呼叫框架做為配置計算處理序的一部分。|  
|[CMFCColorBar::CreatePalette](../Topic/CMFCColorBar::CreatePalette.md)|初始化具有色彩中的調色盤中指定的色彩。|  
|[CMFCColorBar::GetColorGridSize](../Topic/CMFCColorBar::GetColorGridSize.md)|計算資料列和資料行在 \[色軸控制項的方格。|  
|[CMFCColorBar::GetExtraHeight](../Topic/CMFCColorBar::GetExtraHeight.md)|計算目前的色軸要求中顯示其他使用者介面項目 \(例如 \[**其他**\] 按鈕，文件、色彩等等，額外的高度。|  
|[CMFCColorBar::InitColors](../Topic/CMFCColorBar::InitColors.md)|使用色彩的色調 \(使用指定的調色盤或系統預設調色盤。|  
|[CMFCColorBar::OnKey](../Topic/CMFCColorBar::OnKey.md)|呼叫框架，當使用者按下某個鍵盤按鍵。|  
|[CMFCColorBar::OnSendCommand](../Topic/CMFCColorBar::OnSendCommand.md)|呼叫框架結束快顯控制項階層架構。|  
|[CMFCColorBar::OnUpdateCmdUI](../Topic/CMFCColorBar::OnUpdateCmdUI.md)|呼叫由架構來啟用或停用對色軸控制項的使用者介面項目在項目上顯示。|  
|[CMFCColorBar::OpenColorDialog](../Topic/CMFCColorBar::OpenColorDialog.md)|開啟色彩對話方塊。|  
|[CMFCColorBar::Rebuild](../Topic/CMFCColorBar::Rebuild.md)|完全重新繪製至色軸控制項。|  
|[CMFCColorBar::SelectPalette](../Topic/CMFCColorBar::SelectPalette.md)|設定指定之裝置內容的邏輯調色盤到目前的色軸父控制項的按鈕的調色盤。|  
|[CMFCColorBar::SetPropList](../Topic/CMFCColorBar::SetPropList.md)|設定 `m_pWndPropList` 保護資料成員設定為指定的指標屬性方格控制項。|  
|[CMFCColorBar::ShowCommandMessageString](../Topic/CMFCColorBar::ShowCommandMessageString.md)|要求主控對話色軸控制更新在狀態列的訊息列框架視窗。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|`m_bInternal`|判斷的布林值 \(Boolean\) 欄位是否滑鼠事件處理常式。  通常，滑鼠事件處理常式，在這個欄位是 `TRUE` 時，自訂方式是 `FALSE`。|  
|`m_bIsEnabled`|布林 \(Boolean\) 值控制是否啟用。|  
|`m_bIsTearOff`|布林值 \(Boolean\) 至色軸控制項是否支援停駐。|  
|`m_BoxSize`|在 \[色軸指定方格中的儲存格大小的 [CSize](../../atl-mfc-shared/reference/csize-class.md) 物件。|  
|`m_bShowDocColorsWhenDocked`|指示是否顯示文件色彩的布林值，當呼叫色軸停駐。  如需詳細資訊，請參閱 [CMFCColorBar::SetDocumentColors](../Topic/CMFCColorBar::SetDocumentColors.md)。|  
|`m_bStdColorDlg`|指示是否顯示標準系統色彩對話方塊或 [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) 對話方塊的布林值。  如需詳細資訊，請參閱 [CMFCColorBar::EnableOtherButton](../Topic/CMFCColorBar::EnableOtherButton.md)。|  
|`m_ColorAutomatic`|儲存目前的自動色彩的 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) 。  如需詳細資訊，請參閱 [CMFCColorBar::EnableOtherButton](../Topic/CMFCColorBar::EnableOtherButton.md)。|  
|`m_ColorNames`|相關聯的一組物件的 [CMap](../../mfc/reference/cmap-class.md) RGB 色彩與其名稱。|  
|`m_colors`|的 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) 值 [CArray](../../mfc/reference/carray-class.md) 包含色彩的色軸顯示控制項。|  
|`m_ColorSelected`|色彩是使用者可以在色軸控制項中目前選取的 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) 值。|  
|`m_lstDocColors`|的 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) 值 [CList](../../mfc/reference/clist-class.md) 包含色彩目前用於文件。|  
|`m_nCommandID`|為色彩按鈕的命令 ID 的不帶正負號的整數。|  
|`m_nHorzMargin`|是在色彩之間的水平框線的整數色彩在方格中。|  
|`m_nHorzOffset`|為按鈕的中心色彩的水平位移的整數。  除了之外，色彩，否則，請按一下按鈕顯示的文字或影像這個值是很重要的。|  
|`m_nNumColumns`|是資料行數色彩的色軸控制項 ID 的整數。|  
|`m_nNumColumnsVert`|是資料行數色彩是垂直方向的方格的整數。|  
|`m_nNumRowsHorz`|是資料行數色彩一個水平方向的方格的整數。|  
|`m_nRowHeight`|是色彩資料列高度的整數色彩在方格中。|  
|`m_nVertMargin`|是在色彩之間的垂直框線的整數色彩在方格中。|  
|`m_nVertOffset`|為按鈕的中心色彩的垂直位移的整數。  除了之外，色彩，否則，請按一下按鈕顯示的文字或影像這個值是很重要的。|  
|`m_Palette`|套用至色軸控制色彩的 [CPalette](../../mfc/reference/cpalette-class.md) 。|  
|`m_pParentBtn`|造成目前按鈕的父代的 [CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md) 物件的指標。  如果色彩工具列的按鈕控制項階層架構或在色彩屬性方格控制項中，這個值是很重要的。|  
|`m_pParentRibbonBtn`|是在功能區上且為目前按鈕的父代按鈕的 [CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md) 物件的指標。  如果色彩工具列的按鈕控制項階層架構或在色彩屬性方格控制項中，這個值是很重要的。|  
|`m_pWndPropList`|為 [CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md) 物件的指標。|  
|`m_strAutoColor`|是文字。 \[**自動**\] 按鈕顯示的 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 。  如需詳細資訊，請參閱 [CMFCColorBar::EnableAutomaticButton](../Topic/CMFCColorBar::EnableAutomaticButton.md)。|  
|`m_strDocColors`|是文字文件色彩按鈕顯示的 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 。  如需詳細資訊，請參閱 [CMFCColorBar::SetDocumentColors](../Topic/CMFCColorBar::SetDocumentColors.md)。|  
|`m_strOtherColor`|是文字在 *另一個* 按鈕顯示的 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 。  如需詳細資訊，請參閱 [CMFCColorBar::EnableOtherButton](../Topic/CMFCColorBar::EnableOtherButton.md)。|  
  
## 備註  
 通常，您不會直接建立 `CMFCColorBar` 物件。  相反地， [CMFCColorMenuButton Class](../../mfc/reference/cmfccolormenubutton-class.md) \(用於功能表和工具列\) 或 [CMFCColorButton Class](../../mfc/reference/cmfccolorbutton-class.md) 建立 `CMFCColorBar` 物件。  
  
 `CMFCColorBar` 類別提供了下列功能:  
  
-   自動調整文件色彩清單。  
  
-   與文件狀態一起儲存並還原其狀態。  
  
-   處理「Auto」按鈕。  
  
-   使用 [CMFCColorPickerCtrl Class](../../mfc/reference/cmfccolorpickerctrl-class.md) 控制選取自訂色彩。  
  
-   \(如果使用建立 [CMFCColorMenuButton Class](../../mfc/reference/cmfccolormenubutton-class.md)\)，支援「Tear\-Off」狀態。  
  
 合併 `CMFCColorBar` 功能加入至您的應用程式:  
  
1.  建立一個規則功能表按鈕並指派其 ID，例如 ID\_CHAR\_COLOR。  
  
2.  在框架視窗類別中，覆寫方法 [CFrameWndEx::OnShowPopupMenu](../Topic/CFrameWndEx::OnShowPopupMenu.md) 並以 [CMFCColorMenuButton Class](../../mfc/reference/cmfccolormenubutton-class.md) 物件取代規則功能表按鈕 \(藉由呼叫 [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md)\)。  
  
3.  將所有樣式並在 [CMFCColorMenuButton Class](../../mfc/reference/cmfccolormenubutton-class.md) 建立期間啟用或停用 `CMFCColorBar` 物件的功能。  架構會呼叫 `CreatePopupMenu` 方法之後， `CMFCColorMenuButton` 物件動態建立 `CMFCColorBar` 物件。  
  
 當使用者按一下 \[色軸控制項按鈕時，架構會使用 `ON_COMMAND` 巨集將告知色軸控制項的父代。  在巨集，命令 ID 參數是您指派至步驟 1 的值 \(在本例中為 ID\_CHAR\_COLOR 色軸按鈕控制項\)。  如需詳細資訊，請參閱 [CMFCColorMenuButton Class](../../mfc/reference/cmfccolormenubutton-class.md)、 [CMFCColorButton Class](../../mfc/reference/cmfccolorbutton-class.md)、 [CMFCColorPickerCtrl Class](../../mfc/reference/cmfccolorpickerctrl-class.md)、 [CFrameWndEx Class](../../mfc/reference/cframewndex-class.md)和 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md) 類別。  
  
## 範例  
 您可以使用類別，在 `CMFCColorBar` 的各種方法。下列範例將示範如何設定至色軸。  方法設定層級，且垂直框線，讓另一個按鈕，建立對色軸控制 Windows 和集合目前所選取的色彩。  這個範例是 [新的控制項範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!CODE [NVC_MFC_NewControls#1](../CodeSnippet/VS_Snippets_Misc/NVC_MFC_NewControls#1)]  
[!CODE [NVC_MFC_NewControls#2](../CodeSnippet/VS_Snippets_Misc/NVC_MFC_NewControls#2)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)  
  
 [CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)  
  
## 需求  
 **標題:** afxcolorbar.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)