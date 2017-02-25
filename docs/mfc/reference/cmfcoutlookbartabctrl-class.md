---
title: "CMFCOutlookBarTabCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCOutlookBarTabCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCOutlookBarTabCtrl class"
ms.assetid: b1f2b3f7-cc59-49a3-99d8-7ff9b37c044b
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# CMFCOutlookBarTabCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

具有 \[**巡覽窗格**\] 視覺外觀在 Microsoft Outlook 中的索引標籤控制項。  
  
## 語法  
  
```  
class CMFCOutlookBarTabCtrl : public CMFCBaseTabCtrl  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|`CMFCOutlookBarTabCtrl::CMFCOutlookBarTabCtrl`|預設建構函式。|  
|`CMFCOutlookBarTabCtrl::~CMFCOutlookBarTabCtrl`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCOutlookBarTabCtrl::AddControl](../Topic/CMFCOutlookBarTabCtrl::AddControl.md)|將 Windows 控制項為 Outlook 功能區的新索引標籤。|  
|`CMFCOutlookBarTabCtrl::CalcRectEdit`|呼叫框架決定了在編輯方塊的維度在使用者提供一個索引標籤。  \(覆寫 `CMFCBaseTabCtrl::CalcRectEdit`\)。|  
|[CMFCOutlookBarTabCtrl::CanShowFewerPageButtons](../Topic/CMFCOutlookBarTabCtrl::CanShowFewerPageButtons.md)|呼叫由架構在調整大小作業期間判斷少量 Outlook 功能區索引標籤頁按鈕是否可以顯示與目前為可見的。|  
|[CMFCOutlookBarTabCtrl::CanShowMorePageButtons](../Topic/CMFCOutlookBarTabCtrl::CanShowMorePageButtons.md)|呼叫由架構在調整大小作業期間判斷詳細 Outlook 功能區索引標籤頁按鈕是否可以顯示與目前為可見的。|  
|[CMFCOutlookBarTabCtrl::Create](../Topic/CMFCOutlookBarTabCtrl::Create.md)|建立 Outlook 功能區索引標籤控制項。|  
|`CMFCOutlookBarTabCtrl::CreateObject`|由架構建立這個類別型別的動態執行個體。|  
|[CMFCOutlookBarTabCtrl::EnableAnimation](../Topic/CMFCOutlookBarTabCtrl::EnableAnimation.md)|指定發生在現用選項之間切換時的動畫是否已啟用。|  
|[CMFCOutlookBarTabCtrl::EnableInPlaceEdit](../Topic/CMFCOutlookBarTabCtrl::EnableInPlaceEdit.md)|指定使用者是否可以修改在 Outlook 中選項按鈕的文字標籤。  \(覆寫 [CMFCBaseTabCtrl::EnableInPlaceEdit](../Topic/CMFCBaseTabCtrl::EnableInPlaceEdit.md)\)。|  
|[CMFCOutlookBarTabCtrl::EnableScrollButtons](../Topic/CMFCOutlookBarTabCtrl::EnableScrollButtons.md)|呼叫框架啟用允許使用者在 Outlook 功能區窗格的按鈕移動的按鈕。|  
|`CMFCOutlookBarTabCtrl::FindTargetWnd`|識別包含指定點的窗格。  \(覆寫 [CMFCBaseTabCtrl::FindTargetWnd](../Topic/CMFCBaseTabCtrl::FindTargetWnd.md)\)。|  
|[CMFCOutlookBarTabCtrl::GetBorderSize](../Topic/CMFCOutlookBarTabCtrl::GetBorderSize.md)|傳回 Outlook 索引標籤控制項的框線大小。|  
|`CMFCOutlookBarTabCtrl::GetTabArea`|擷取索引標籤控制項的索引標籤範圍的大小和位置。  \(覆寫 [CMFCBaseTabCtrl::GetTabArea](../Topic/CMFCBaseTabCtrl::GetTabArea.md)\)。|  
|`CMFCOutlookBarTabCtrl::GetThisClass`|由框架以取得指向與這個類別型別的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件。|  
|[CMFCOutlookBarTabCtrl::GetVisiblePageButtons](../Topic/CMFCOutlookBarTabCtrl::GetVisiblePageButtons.md)||  
|[CMFCOutlookBarTabCtrl::IsAnimation](../Topic/CMFCOutlookBarTabCtrl::IsAnimation.md)|判斷發生在現用選項之間切換時的動畫是否已啟用。|  
|[CMFCOutlookBarTabCtrl::IsMode2003](../Topic/CMFCOutlookBarTabCtrl::IsMode2003.md)|判斷 Outlook 功能區索引標籤控制項是否在模擬 Microsoft Outlook 2003 年模式。|  
|`CMFCOutlookBarTabCtrl::IsPtInTabArea`|判斷某個點是否在索引標籤區域內。  \(覆寫 [CMFCBaseTabCtrl::IsPtInTabArea](../Topic/CMFCBaseTabCtrl::IsPtInTabArea.md)\)。|  
|`CMFCOutlookBarTabCtrl::IsTabDetachable`|判斷索引標籤是否為可拆的。  \(覆寫 [CMFCBaseTabCtrl::IsTabDetachable](../Topic/CMFCBaseTabCtrl::IsTabDetachable.md)\)。|  
|`CMFCOutlookBarTabCtrl::OnChangeTabs`|呼叫由架構，在插入索引標籤或移除。  \(覆寫 `CMFCBaseTabCtrl::OnChangeTabs`\)。|  
|[CMFCOutlookBarTabCtrl::OnShowFewerPageButtons](../Topic/CMFCOutlookBarTabCtrl::OnShowFewerPageButtons.md)|呼叫框架降低索引標籤是可見的頁面按鈕數目。|  
|[CMFCOutlookBarTabCtrl::OnShowMorePageButtons](../Topic/CMFCOutlookBarTabCtrl::OnShowMorePageButtons.md)|呼叫框架加入索引標籤是可見的頁面按鈕數目。|  
|[CMFCOutlookBarTabCtrl::OnShowOptions](../Topic/CMFCOutlookBarTabCtrl::OnShowOptions.md)|顯示 \[**巡覽窗格中選取**\] 對話方塊。|  
|`CMFCOutlookBarTabCtrl::RecalcLayout`|重新計算索引標籤控制項的內部配置。  \(覆寫 [CMFCBaseTabCtrl::RecalcLayout](../Topic/CMFCBaseTabCtrl::RecalcLayout.md)\)。|  
|[CMFCOutlookBarTabCtrl::SetActiveTab](../Topic/CMFCOutlookBarTabCtrl::SetActiveTab.md)|設定使用中的  索引標籤。  \(覆寫 [CMFCBaseTabCtrl::SetActiveTab](../Topic/CMFCBaseTabCtrl::SetActiveTab.md)\)。|  
|[CMFCOutlookBarTabCtrl::SetBorderSize](../Topic/CMFCOutlookBarTabCtrl::SetBorderSize.md)|設定 Outlook 索引標籤控制項的框線大小。|  
|[CMFCOutlookBarTabCtrl::SetPageButtonTextAlign](../Topic/CMFCOutlookBarTabCtrl::SetPageButtonTextAlign.md)|設定文字標籤的對齊在 Outlook 功能的選項按鈕。|  
|[CMFCOutlookBarTabCtrl::SetToolbarImageList](../Topic/CMFCOutlookBarTabCtrl::SetToolbarImageList.md)|設定包含圖示會出現在 Outlook 底部顯示在 Outlook 2003 年模式的點陣圖 \(請參閱 [CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)\)。|  
|[CMFCOutlookBarTabCtrl::SetVisiblePageButtons](../Topic/CMFCOutlookBarTabCtrl::SetVisiblePageButtons.md)||  
  
## 備註  
 若要建立具有停駐支援的 Outlook 禁止，請使用 `CMFCOutlookBar` 物件裝載 Outlook 功能區索引標籤控制項。  如需詳細資訊，請參閱 [CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)。  
  
## 範例  
 下列範例示範如何初始化 `CMFCOutlookBarTabCtrl` 物件，以及使用各種方法在 `CMFCOutlookBarTabCtrl` 類別。  這個範例示範如何啟用就地編輯在 Outlook 功能區的索引標籤頁按鈕的文字標籤，以啟用動畫，可讓使用者在 Outlook 功能區窗格的按鈕捲動，設定 Outlook 索引標籤控制項的框線大小，並將文字標籤對齊在 Outlook 中選項按鈕的捲動控制代碼。   這個程式碼片段是 [Outlook 示範範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!CODE [NVC_MFC_OutlookDemo#1](../CodeSnippet/VS_Snippets_Misc/NVC_MFC_OutlookDemo#1)]  
[!CODE [NVC_MFC_OutlookDemo#2](../CodeSnippet/VS_Snippets_Misc/NVC_MFC_OutlookDemo#2)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)  
  
 [CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md)  
  
## 需求  
 **標題:** afxoutlookbartabctrl.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCBaseTabCtrl Class](../../mfc/reference/cmfcbasetabctrl-class.md)   
 [CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)   
 [CMFCOutlookBarPane Class](../../mfc/reference/cmfcoutlookbarpane-class.md)