---
title: "CMFCRibbonGallery Class | Microsoft Docs"
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
  - "CMFCRibbonGallery"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonGallery class"
ms.assetid: 9734c9c9-981c-4b3f-8c59-264fd41811b4
caps.latest.revision: 28
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonGallery Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作 Office 2007 的功能區陳列庫。  
  
## 語法  
  
```  
class CMFCRibbonGallery : public CMFCRibbonButton  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonGallery::CMFCRibbonGallery](../Topic/CMFCRibbonGallery::CMFCRibbonGallery.md)|建構和 `CMFCRibbonGallery` 初始化物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonGallery::AddGroup](../Topic/CMFCRibbonGallery::AddGroup.md)|若要加入新群組加入至這個組件庫。|  
|[CMFCRibbonGallery::AddSubItem](../Topic/CMFCRibbonGallery::AddSubItem.md)|若要加入新的功能表項目加入至下拉式功能表。|  
|[CMFCRibbonGallery::Clear](../Topic/CMFCRibbonGallery::Clear.md)|清除的內容陳列庫。|  
|[CMFCRibbonGallery::EnableMenuResize](../Topic/CMFCRibbonGallery::EnableMenuResize.md)|啟用或停用調整功能表面板。|  
|[CMFCRibbonGallery::EnableMenuSideBar](../Topic/CMFCRibbonGallery::EnableMenuSideBar.md)|在快顯功能表左邊啟用或停用此提要欄位。|  
|[CMFCRibbonGallery::GetCompactSize](../Topic/CMFCRibbonGallery::GetCompactSize.md)|\(覆寫 [CMFCRibbonButton::GetCompactSize](../Topic/CMFCRibbonButton::GetCompactSize.md)\)。|  
|[CMFCRibbonGallery::GetDroppedDown](../Topic/CMFCRibbonGallery::GetDroppedDown.md)|\(覆寫 [CMFCRibbonBaseElement::GetDroppedDown](../Topic/CMFCRibbonBaseElement::GetDroppedDown.md)\)。|  
|[CMFCRibbonGallery::GetGroupName](../Topic/CMFCRibbonGallery::GetGroupName.md)|傳回位於指定索引處的群組名稱。|  
|[CMFCRibbonGallery::GetGroupOffset](../Topic/CMFCRibbonGallery::GetGroupOffset.md)||  
|[CMFCRibbonGallery::GetIconsInRow](../Topic/CMFCRibbonGallery::GetIconsInRow.md)|會傳回的項目數功能區陳列庫。|  
|[CMFCRibbonGallery::GetItemToolTip](../Topic/CMFCRibbonGallery::GetItemToolTip.md)|傳回與陳列庫中某個項目的工具提示文字。|  
|[CMFCRibbonGallery::GetLastSelectedItem](../Topic/CMFCRibbonGallery::GetLastSelectedItem.md)|傳回最後一個項目的索引使用者選取的陳列庫的。|  
|[CMFCRibbonGallery::GetPaletteID](../Topic/CMFCRibbonGallery::GetPaletteID.md)|傳回目前圖庫的命令 ID。|  
|[CMFCRibbonGallery::GetRegularSize](../Topic/CMFCRibbonGallery::GetRegularSize.md)|\(覆寫 [CMFCRibbonButton::GetRegularSize](../Topic/CMFCRibbonButton::GetRegularSize.md)\)。|  
|[CMFCRibbonGallery::GetSelectedItem](../Topic/CMFCRibbonGallery::GetSelectedItem.md)||  
|[CMFCRibbonGallery::HasMenu](../Topic/CMFCRibbonGallery::HasMenu.md)|\(覆寫 [CMFCRibbonButton::HasMenu](../Topic/CMFCRibbonButton::HasMenu.md)\)。|  
|[CMFCRibbonGallery::IsButtonMode](../Topic/CMFCRibbonGallery::IsButtonMode.md)|指定這個一般模式庫是否在圖庫按鈕中。|  
|[CMFCRibbonGallery::IsMenuResizeEnabled](../Topic/CMFCRibbonGallery::IsMenuResizeEnabled.md)|指定功能表調整大小是否啟用或停用。|  
|[CMFCRibbonGallery::IsMenuResizeVertical](../Topic/CMFCRibbonGallery::IsMenuResizeVertical.md)||  
|[CMFCRibbonGallery::IsMenuSideBar](../Topic/CMFCRibbonGallery::IsMenuSideBar.md)|指定這個提要欄位是否啟用或停用。|  
|[CMFCRibbonGallery::OnAfterChangeRect](../Topic/CMFCRibbonGallery::OnAfterChangeRect.md)|\(覆寫 `CMFCRibbonButton::OnAfterChangeRect`\)。|  
|[CMFCRibbonGallery::OnDraw](../Topic/CMFCRibbonGallery::OnDraw.md)|\(覆寫 [CMFCRibbonButton::OnDraw](../Topic/CMFCRibbonButton::OnDraw.md)\)。|  
|[CMFCRibbonGallery::OnEnable](../Topic/CMFCRibbonGallery::OnEnable.md)|\(覆寫 `CMFCRibbonBaseElement::OnEnable`\)。|  
|[CMFCRibbonGallery::OnRTLChanged](../Topic/CMFCRibbonGallery::OnRTLChanged.md)|\(覆寫 [CMFCRibbonBaseElement::OnRTLChanged](../Topic/CMFCRibbonBaseElement::OnRTLChanged.md)\)。|  
|[CMFCRibbonGallery::RedrawIcons](../Topic/CMFCRibbonGallery::RedrawIcons.md)|重繪陳列庫。|  
|[CMFCRibbonGallery::RemoveItemToolTips](../Topic/CMFCRibbonGallery::RemoveItemToolTips.md)|從  庫中的所有項目移除工具提示。|  
|[CMFCRibbonGallery::SelectItem](../Topic/CMFCRibbonGallery::SelectItem.md)||  
|[CMFCRibbonGallery::SetACCData](../Topic/CMFCRibbonGallery::SetACCData.md)|\(覆寫 [CMFCRibbonButton::SetACCData](../Topic/CMFCRibbonButton::SetACCData.md)\)。|  
|[CMFCRibbonGallery::SetButtonMode](../Topic/CMFCRibbonGallery::SetButtonMode.md)|指定是否顯示功能區陳列庫做為下拉式按鈕或做為調色盤直接在功能區上。|  
|[CMFCRibbonGallery::SetGroupName](../Topic/CMFCRibbonGallery::SetGroupName.md)|設定群組名稱。|  
|[CMFCRibbonGallery::SetIconsInRow](../Topic/CMFCRibbonGallery::SetIconsInRow.md)|定義項目數目表示圖庫的資料列。|  
|[CMFCRibbonGallery::SetItemToolTip](../Topic/CMFCRibbonGallery::SetItemToolTip.md)|將某個項目的工具提示文字在陳列庫。|  
|[CMFCRibbonGallery::SetPalette](../Topic/CMFCRibbonGallery::SetPalette.md)|調色盤附加至功能區陳列庫。|  
|[CMFCRibbonGallery::SetPaletteID](../Topic/CMFCRibbonGallery::SetPaletteID.md)|定義在 `WM_COMMAND` 訊息傳送的命令 ID，當陳列庫項目已選取時。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonGallery::OnDrawPaletteIcon](../Topic/CMFCRibbonGallery::OnDrawPaletteIcon.md)|呼叫由架構，在繪製圖庫圖示。|  
  
## 備註  
 圖庫按鈕的行為如同一個規則功能表按鈕，但它會顯示陳列庫，當使用者開啟時。  當您選取陳列庫中建立項目，這個架構與按鈕關聯的命令 ID `WM_COMMAND` 資訊一起傳送。  當您處理訊息時，您應該呼叫 [CMFCRibbonGallery::GetLastSelectedItem](../Topic/CMFCRibbonGallery::GetLastSelectedItem.md) 判斷哪個項目從陳列庫中選取。  
  
## 範例  
 下列範例會在 `CMFCRibbonGallery` 類別會示範如何使用各種方法設定 `CMFCRibbonGallery` 物件。  在範例圖庫說明如何指定項目數目的每個資料列，以調整功能表面板，在快顯功能表左邊啟用提要欄位和顯示功能區陳列庫做為調色盤直接在功能區列。  這個程式碼片段是 [繪製用戶端範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_DrawClient#6](../../mfc/reference/codesnippet/CPP/cmfcribbongallery-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md) [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md) [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)  
  
## 需求  
 **標題:** afxRibbonPaletteGallery.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton Class](../../mfc/reference/cmfcribbonbutton-class.md)   
 [CMFCRibbonGalleryMenuButton Class](../../mfc/reference/cmfcribbongallerymenubutton-class.md)