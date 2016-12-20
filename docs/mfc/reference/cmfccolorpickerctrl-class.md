---
title: "CMFCColorPickerCtrl Class | Microsoft Docs"
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
  - "CMFCColorPickerCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCColorPickerCtrl class"
ms.assetid: b9bbd03c-beb0-4b55-9765-9985fd05e5dc
caps.latest.revision: 33
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCColorPickerCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCColorPickerCtrl` 類別提供用來選取色彩的控制項提供的功能。  
  
## 語法  
  
```  
class CMFCColorPickerCtrl : public CButton  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCColorPickerCtrl::CMFCColorPickerCtrl](../Topic/CMFCColorPickerCtrl::CMFCColorPickerCtrl.md)|建構 `CMFCColorPickerCtrl` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCColorPickerCtrl::GetColor](../Topic/CMFCColorPickerCtrl::GetColor.md)|擷取使用者所選取的色彩。|  
|[CMFCColorPickerCtrl::GetHLS](../Topic/CMFCColorPickerCtrl::GetHLS.md)|擷取使用者所選取色彩的色調、飽和亮度和值。|  
|[CMFCColorPickerCtrl::GetHue](../Topic/CMFCColorPickerCtrl::GetHue.md)|擷取使用者選取色彩的色彩元件。|  
|[CMFCColorPickerCtrl::GetLuminance](../Topic/CMFCColorPickerCtrl::GetLuminance.md)|擷取使用者選取色彩的亮度元件。|  
|[CMFCColorPickerCtrl::GetSaturation](../Topic/CMFCColorPickerCtrl::GetSaturation.md)|擷取使用者選取色彩的飽和度元件。|  
|[CMFCColorPickerCtrl::SelectCellHexagon](../Topic/CMFCColorPickerCtrl::SelectCellHexagon.md)|設定目前色彩為指定的 RGB 色彩元件或指定的儲存格是定義的色彩。|  
|[CMFCColorPickerCtrl::SetColor](../Topic/CMFCColorPickerCtrl::SetColor.md)|設定目前色彩為指定的 RGB 色彩值。|  
|[CMFCColorPickerCtrl::SetHLS](../Topic/CMFCColorPickerCtrl::SetHLS.md)|設定目前色彩為指定的 HLS 色彩值。|  
|[CMFCColorPickerCtrl::SetHue](../Topic/CMFCColorPickerCtrl::SetHue.md)|變更目前選取之色彩的色彩元件。|  
|[CMFCColorPickerCtrl::SetLuminance](../Topic/CMFCColorPickerCtrl::SetLuminance.md)|變更目前選取之色彩的亮度元件。|  
|[CMFCColorPickerCtrl::SetLuminanceBarWidth](../Topic/CMFCColorPickerCtrl::SetLuminanceBarWidth.md)|設定亮度列的寬度 \(以色彩選擇器控制項。|  
|[CMFCColorPickerCtrl::SetOriginalColor](../Topic/CMFCColorPickerCtrl::SetOriginalColor.md)|設定中初始選取的色彩。|  
|[CMFCColorPickerCtrl::SetPalette](../Topic/CMFCColorPickerCtrl::SetPalette.md)|設定目前色板。|  
|[CMFCColorPickerCtrl::SetSaturation](../Topic/CMFCColorPickerCtrl::SetSaturation.md)|變更目前選取之色彩的飽和度元件。|  
|[CMFCColorPickerCtrl::SetType](../Topic/CMFCColorPickerCtrl::SetType.md)|設定色彩選擇器控制項型別示範。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCColorPickerCtrl::DrawCursor](../Topic/CMFCColorPickerCtrl::DrawCursor.md)|呼叫由架構在指向所選取色彩的游標目前所顯示。|  
  
## 備註  
 標準色彩從一個六角調色盤中選取，然後，自訂色彩會從使用紅色、綠色和藍色附註或色彩\/satuaration\/亮度附註，指定色彩的亮度列中選取。  
  
 下圖說明數 `CMFCColorPickerCtrl` 物件。  
  
 ![CMFCColorPickerCtrl 對話方塊](../../mfc/reference/media/colorpicker.png "ColorPicker")  
  
 `CMFCColorPickerCtrl` 支援兩組樣式。  hex 和 HEX\_GREYSCALE 模式與標準色彩選取適合。  選擇器和亮度模式與自訂色彩的選項是適當的。  
  
 執行下列步驟 `CMFCColorPickerCtrl` 結合控制項加入至對話方塊中:  
  
1.  如果您使用 \[**ClassWizard**\]，插入新的按鈕控制項加入至對話方塊範本 \(因為 `CMFCColorPickerCtrl` 類別從 `CButton` 類別繼承\)。  
  
2.  插入與新的按鈕控制項加入至對話方塊類別的成員變數。  然後從 `CButton` 變更變數型別加入至 `CMFCColorPickerCtrl`。  
  
3.  插入對話方塊類別的 `WM_INITDIALOG` 訊息處理常式。  在處理常式中，將型別、調色盤、第一個 `CMFCColorPickerCtrl` 控制項中所選取的色彩。  
  
## 範例  
 您可以使用類別，在 `CMFCColorPickerCtrl` 的各種方法。下列範例將示範如何設定 `CMFCColorPickerCtrl` 物件。  範例會示範如何設定選擇器控制項類型以及如何設定它的色彩、色彩、飽和亮度和。  這個範例是 [新的控制項範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!CODE [NVC_MFC_NewControls#4](../CodeSnippet/VS_Snippets_Misc/NVC_MFC_NewControls#4)]  
[!CODE [NVC_MFC_NewControls#5](../CodeSnippet/VS_Snippets_Misc/NVC_MFC_NewControls#5)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md)  
  
## 需求  
 **標題:** afxcolorpickerctrl.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCColorDialog Class](../../mfc/reference/cmfccolordialog-class.md)