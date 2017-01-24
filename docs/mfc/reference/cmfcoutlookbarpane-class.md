---
title: "CMFCOutlookBarPane Class | Microsoft Docs"
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
  - "CMFCOutlookBarPane"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CanBeRestored method"
  - "CMFCOutlookBarPane class"
  - "Dock method"
  - "IsChangeState method"
  - "OnBeforeFloat method"
  - "RestoreOriginalstate method"
  - "SmartUpdate method"
ms.assetid: 094e2ef3-a118-487e-a4cc-27626108fe08
caps.latest.revision: 30
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCOutlookBarPane Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 控制項可以插入至 Outlook 功能 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md) 衍生自 \([CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)\)。  Outlook 功能區窗格包含大型按鈕的資料行。  使用者可以捲動到按鈕清單中上下移動，如果大於窗格。  當使用者中斷與 Outlook 中建立 Outlook 功能區窗格，它在主框架視窗可以停駐或浮動。  
  
## 語法  
  
```  
class CMFCOutlookBarPane : public CMFCToolBar  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|`CMFCOutlookBarPane::CMFCOutlookBarPane`|預設建構函式。|  
|`CMFCOutlookBarPane::~CMFCOutlookBarPane`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCOutlookBarPane::AddButton](../Topic/CMFCOutlookBarPane::AddButton.md)|將按鈕加入至 Outlook 功能區窗格。|  
|[CMFCOutlookBarPane::CanBeAttached](../Topic/CMFCOutlookBarPane::CanBeAttached.md)|判斷是否可停駐窗格加入至另一個窗格或框架視窗。  \(覆寫 [CBasePane::CanBeAttached](../Topic/CBasePane::CanBeAttached.md)\)。|  
|`CMFCOutlookBarPane::CanBeRestored`|決定系統是否可以還原工具列到原來的狀態在自訂之後。  \(覆寫 [CMFCToolBar::CanBeRestored](../Topic/CMFCToolBar::CanBeRestored.md)\)。|  
|[CMFCOutlookBarPane::ClearAll](../Topic/CMFCOutlookBarPane::ClearAll.md)|釋放所使用的影像資源在 Outlook 功能區窗格。|  
|[CMFCOutlookBarPane::Create](../Topic/CMFCOutlookBarPane::Create.md)|建立 Outlook 功能區窗格。|  
|`CMFCOutlookBarPane::CreateObject`|由架構建立這個類別型別的動態執行個體。|  
|`CMFCOutlookBarPane::Dock`|呼叫框架內建 Outlook 功能區窗格。\(覆寫 `CPane::Dock`\)。|  
|[CMFCOutlookBarPane::EnablePageScrollMode](../Topic/CMFCOutlookBarPane::EnablePageScrollMode.md)|由按鈕指定在 Outlook 功能區窗格指捲動箭號是否有助於按鈕中透過網頁，或。|  
|[CMFCOutlookBarPane::GetRegularColor](../Topic/CMFCOutlookBarPane::GetRegularColor.md)|傳回 Outlook 功能區窗格的規則 \(非\) 選取的文字色彩。|  
|`CMFCOutlookBarPane::GetThisClass`|由框架以取得指向與這個類別型別的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件。|  
|[CMFCOutlookBarPane::IsBackgroundTexture](../Topic/CMFCOutlookBarPane::IsBackgroundTexture.md)|判斷是否有提供 Outlook 功能區窗格載入的背景影像。|  
|`CMFCOutlookBarPane::IsChangeState`|判斷浮動窗格是否可以修正。  \(覆寫 `CPane::IsChangeState`\)。|  
|[CMFCOutlookBarPane::IsDrawShadedHighlight](../Topic/CMFCOutlookBarPane::IsDrawShadedHighlight.md)|判斷按鈕框線是否遮蔽按鈕時，會反白顯示，而背景影像隨即顯示。|  
|`CMFCOutlookBarPane::OnBeforeFloat`|呼叫框架時，窗格會浮動。  \(覆寫 [CPane::OnBeforeFloat](../Topic/CPane::OnBeforeFloat.md)\)。|  
|[CMFCOutlookBarPane::RemoveButton](../Topic/CMFCOutlookBarPane::RemoveButton.md)|移除具有指定的命令 ID. 的按鈕|  
|`CMFCOutlookBarPane::RestoreOriginalstate`|還原工具列的原始狀態。  \(覆寫 [CMFCToolBar::RestoreOriginalState](../Topic/CMFCToolBar::RestoreOriginalState.md)\)。|  
|[CMFCOutlookBarPane::SetBackColor](../Topic/CMFCOutlookBarPane::SetBackColor.md)|設定背景色彩。|  
|[CMFCOutlookBarPane::SetBackImage](../Topic/CMFCOutlookBarPane::SetBackImage.md)|設定的背景影像。|  
|[CMFCOutlookBarPane::SetDefaultState](../Topic/CMFCOutlookBarPane::SetDefaultState.md)|重設 Outlook 功能區窗格為原始組按鈕。|  
|[CMFCOutlookBarPane::SetExtraSpace](../Topic/CMFCOutlookBarPane::SetExtraSpace.md)|設定按鈕周圍所使用的填補像素數目 Outlook 功能區窗格。|  
|[CMFCOutlookBarPane::SetTextColor](../Topic/CMFCOutlookBarPane::SetTextColor.md)|設定規則和反白顯示文字色彩在 Outlook 功能區的窗格。|  
|[CMFCOutlookBarPane::SetTransparentColor](../Topic/CMFCOutlookBarPane::SetTransparentColor.md)|設定 Outlook 功能區窗格的透明色彩。|  
|`CMFCOutlookBarPane::SmartUpdate`|內部用來更新 Outlook 功能區。  \(覆寫 `CMFCToolBar::SmartUpdate`\)。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCOutlookBarPane::EnableContextMenuItems](../Topic/CMFCOutlookBarPane::EnableContextMenuItems.md)|指定捷徑功能表項目在自訂模式顯示。|  
|[CMFCOutlookBarPane::RemoveAllButtons](../Topic/CMFCOutlookBarPane::RemoveAllButtons.md)|從 Outlook 功能區窗格移除所有按鈕。  \(覆寫 [CMFCToolBar::RemoveAllButtons](../Topic/CMFCToolBar::RemoveAllButtons.md)\)。|  
  
## 備註  
 如需如何實作 Outlook 功能區的詳細資訊，請參閱 [CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)。  
  
 如需 Outlook 功能區的範例，請參閱 OutlookDemo 範例專案。  
  
## 範例  
 下列範例示範如何使用 `CMFCOutlookBarPane` 類別的各種方法。  這個範例顯示如何建立 Outlook 功能區窗格，起始頁捲動模式，啟用停駐，並將 Outlook 功能區的背景色彩。  這個程式碼片段是 [Outlook 多重檢視範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_OutlookMultiViews#3](../../mfc/reference/codesnippet/CPP/cmfcoutlookbarpane-class_1.h)]  
[!code-cpp[NVC_MFC_OutlookMultiViews#4](../../mfc/reference/codesnippet/CPP/cmfcoutlookbarpane-class_2.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md)  
  
## 需求  
 **標題:** afxoutlookbarpane.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)   
 [CMFCOutlookBarTabCtrl Class](../../mfc/reference/cmfcoutlookbartabctrl-class.md)