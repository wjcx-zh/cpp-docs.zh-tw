---
title: "CMFCStatusBar Class | Microsoft Docs"
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
  - "CMFCStatusBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCStatusBar class"
ms.assetid: f2960d1d-f4ed-41e8-bd99-0382b2f8d88e
caps.latest.revision: 36
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCStatusBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCStatusBar` 類別實作一個狀態列類似 `CStatusBar` 類別。  不過， `CMFCStatusBar` 類別具有 `CStatusBar` 類別所提供的功能，例如能夠顯示影像、動畫和進度列，而且也可以回應滑鼠按兩下 。  
  
## 語法  
  
```  
class CMFCStatusBar : public CPane  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCStatusBar::CalcFixedLayout](../Topic/CMFCStatusBar::CalcFixedLayout.md)|\(覆寫 [CBasePane::CalcFixedLayout](../Topic/CBasePane::CalcFixedLayout.md)\)。|  
|[CMFCStatusBar::CommandToIndex](../Topic/CMFCStatusBar::CommandToIndex.md)||  
|[CMFCStatusBar::Create](../Topic/CMFCStatusBar::Create.md)|建立控制項並將其附加至 [CPane](../../mfc/reference/cpane-class.md) 物件。  \(覆寫 [CPane::Create](../Topic/CPane::Create.md)\)。|  
|[CMFCStatusBar::CreateEx](../Topic/CMFCStatusBar::CreateEx.md)|建立控制項並將其附加至 [CPane](../../mfc/reference/cpane-class.md) 物件。  \(覆寫 [CPane::CreateEx](../Topic/CPane::CreateEx.md)\)。|  
|[CMFCStatusBar::DoesAllowDynInsertBefore](../Topic/CMFCStatusBar::DoesAllowDynInsertBefore.md)|判斷其他窗格是否能夠以動態方式插入這個窗格和父框架之間。  \(覆寫 [CBasePane::DoesAllowDynInsertBefore](../Topic/CBasePane::DoesAllowDynInsertBefore.md)\)。|  
|[CMFCStatusBar::EnablePaneDoubleClick](../Topic/CMFCStatusBar::EnablePaneDoubleClick.md)|啟用或停用處理在狀態列的按兩下滑鼠。|  
|[CMFCStatusBar::EnablePaneProgressBar](../Topic/CMFCStatusBar::EnablePaneProgressBar.md)|顯示在指定的窗格的進度列。|  
|[CMFCStatusBar::GetCount](../Topic/CMFCStatusBar::GetCount.md)|傳回窗格數目的各組件提供物件。|  
|[CMFCStatusBar::GetDrawExtendedArea](../Topic/CMFCStatusBar::GetDrawExtendedArea.md)||  
|[CMFCStatusBar::GetExtendedArea](../Topic/CMFCStatusBar::GetExtendedArea.md)||  
|[CMFCStatusBar::GetItemID](../Topic/CMFCStatusBar::GetItemID.md)||  
|[CMFCStatusBar::GetItemRect](../Topic/CMFCStatusBar::GetItemRect.md)||  
|[CMFCStatusBar::GetPaneInfo](../Topic/CMFCStatusBar::GetPaneInfo.md)||  
|[CMFCStatusBar::GetPaneProgress](../Topic/CMFCStatusBar::GetPaneProgress.md)||  
|[CMFCStatusBar::GetPaneStyle](../Topic/CMFCStatusBar::GetPaneStyle.md)|傳回窗格樣式。  \(覆寫 [CBasePane::GetPaneStyle](../Topic/CBasePane::GetPaneStyle.md)\)。|  
|[CMFCStatusBar::GetPaneText](../Topic/CMFCStatusBar::GetPaneText.md)||  
|[CMFCStatusBar::GetPaneWidth](../Topic/CMFCStatusBar::GetPaneWidth.md)|傳回的寬度，以像素為單位，狀態列中指定的窗格。|  
|[CMFCStatusBar::GetTipText](../Topic/CMFCStatusBar::GetTipText.md)|傳回這個狀態列的指定窗格的工具提示文字。|  
|[CMFCStatusBar::InvalidatePaneContent](../Topic/CMFCStatusBar::InvalidatePaneContent.md)|指定無效的窗格並重新繪製的內容。|  
|[CMFCStatusBar::PreCreateWindow](../Topic/CMFCStatusBar::PreCreateWindow.md)|呼叫框架視窗中視窗的建立之前附加至這個 `CWnd` 物件。  \(覆寫 [CWnd::PreCreateWindow](../Topic/CWnd::PreCreateWindow.md)\)。|  
|[CMFCStatusBar::SetDrawExtendedArea](../Topic/CMFCStatusBar::SetDrawExtendedArea.md)||  
|[CMFCStatusBar::SetIndicators](../Topic/CMFCStatusBar::SetIndicators.md)||  
|[CMFCStatusBar::SetPaneAnimation](../Topic/CMFCStatusBar::SetPaneAnimation.md)|將動畫加入至指定的窗格。|  
|[CMFCStatusBar::SetPaneBackgroundColor](../Topic/CMFCStatusBar::SetPaneBackgroundColor.md)|設定這個狀態列中指定的  窗格的背景色彩。|  
|[CMFCStatusBar::SetPaneIcon](../Topic/CMFCStatusBar::SetPaneIcon.md)|設定這個狀態列的指定窗格中顯示圖示。|  
|[CMFCStatusBar::SetPaneInfo](../Topic/CMFCStatusBar::SetPaneInfo.md)||  
|[CMFCStatusBar::SetPaneProgress](../Topic/CMFCStatusBar::SetPaneProgress.md)|設定進度列的目前進度狀態列窗格的指定的。|  
|[CMFCStatusBar::SetPaneStyle](../Topic/CMFCStatusBar::SetPaneStyle.md)|將窗格設定的樣式。  \(覆寫 [CBasePane::SetPaneStyle](../Topic/CBasePane::SetPaneStyle.md)\)。|  
|[CMFCStatusBar::SetPaneText](../Topic/CMFCStatusBar::SetPaneText.md)||  
|[CMFCStatusBar::SetPaneTextColor](../Topic/CMFCStatusBar::SetPaneTextColor.md)|設定這個狀態列中指定的  窗格中的文字色彩。|  
|[CMFCStatusBar::SetPaneWidth](../Topic/CMFCStatusBar::SetPaneWidth.md)|設定在狀態列中的  窗格中指定像素的寬度。|  
|[CMFCStatusBar::SetTipText](../Topic/CMFCStatusBar::SetTipText.md)|設定這個狀態列的指定窗格的工具提示文字。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCStatusBar::OnDrawPane](../Topic/CMFCStatusBar::OnDrawPane.md)|呼叫框架，並重新繪製這個狀態列的窗格。|  
  
## 備註  
 下圖顯示在狀態列的 [狀態列示範範例](../../top/visual-cpp-samples.md) 嘗試從應用程式的。  
  
 ![CMFCStatusBar 範例](../../mfc/reference/media/cmfcstatusbar.png "CMFCStatusBar")  
  
## 範例  
 下列範例會示範應用程式使用的使用者 `CMFCStatusBar` 類別的各種方法的區域變數。  這些變數在 StatusBarDemoView.h 宣告。  主要畫面格 \(例如\) 會在 MainFrm.h 宣告，文件會 StatusBarDemoDoc.h 宣告，因此，這個檢視就 StatusBarDemoView.h 宣告。  這個程式碼片段是 [狀態列示範範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_StatusBarDemo#9](../../mfc/reference/codesnippet/CPP/cmfcstatusbar-class_1.h)]  
  
## 範例  
 下列範例示範如何藉由引入 `GetStatusBar` 方法在 MainFrm.h 然後呼叫這個方法取得 `CMFCStatusBar` 物件的參考。 `GetStatusBar` 方法在 StatusBarDemoView.h。  這個程式碼片段是 [狀態列示範範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_StatusBarDemo#7](../../mfc/reference/codesnippet/CPP/cmfcstatusbar-class_2.h)]  
[!code-cpp[NVC_MFC_StatusBarDemo#8](../../mfc/reference/codesnippet/CPP/cmfcstatusbar-class_3.h)]  
  
## 範例  
 下列範例示範如何呼叫 `CMFCStatusBar` 類別的各種方法在 StatusBarDemoView.cpp。  在 MainFrm.h 常數宣告。  這個範例顯示如何設定圖示，將狀態列窗格的工具提示文字，會顯示指定之窗格中的進度列，將動畫加入至指定的窗格中，設定文字和狀態列窗格的寬度，並設定進度列的目前進度顯示狀態列窗格的。  這個程式碼片段是 [狀態列示範範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_StatusBarDemo#6](../../mfc/reference/codesnippet/CPP/cmfcstatusbar-class_4.h)]  
[!code-cpp[NVC_MFC_StatusBarDemo#1](../../mfc/reference/codesnippet/CPP/cmfcstatusbar-class_5.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo#2](../../mfc/reference/codesnippet/CPP/cmfcstatusbar-class_6.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo#3](../../mfc/reference/codesnippet/CPP/cmfcstatusbar-class_7.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo#4](../../mfc/reference/codesnippet/CPP/cmfcstatusbar-class_8.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo#5](../../mfc/reference/codesnippet/CPP/cmfcstatusbar-class_9.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)  
  
## 需求  
 **標題:** afxstatusbar.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CPane Class](../../mfc/reference/cpane-class.md)   
 [CStatusBar Class](../../mfc/reference/cstatusbar-class.md)