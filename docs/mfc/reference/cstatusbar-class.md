---
title: "CStatusBar Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CStatusBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStatusBar class"
  - "indicators"
  - "indicators, status bar"
  - "狀態列"
  - "status indicators"
ms.assetid: a3bde3db-e71c-4881-a3ca-1d5481c345ba
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CStatusBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

有文字資料列的控制列輸出窗格或「說明」。  
  
## 語法  
  
```  
class CStatusBar : public CControlBar  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CStatusBar::CStatusBar](../Topic/CStatusBar::CStatusBar.md)|建構 `CStatusBar` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CStatusBar::CommandToIndex](../Topic/CStatusBar::CommandToIndex.md)|取得指定顯示 ID. 的索引。|  
|[CStatusBar::Create](../Topic/CStatusBar::Create.md)|建立這個狀態列，將它附加至 `CStatusBar` 物件，並將初始字型和列高度。|  
|[CStatusBar::CreateEx](../Topic/CStatusBar::CreateEx.md)|建立含有其他樣式的 `CStatusBar` 物件 `CStatusBarCtrl` 內嵌物件的。|  
|[CStatusBar::DrawItem](../Topic/CStatusBar::DrawItem.md)|呼叫，以主控描繪狀態列控制項的視覺外觀變更時。|  
|[CStatusBar::GetItemID](../Topic/CStatusBar::GetItemID.md)|取得位於指定索引的說明 ID。|  
|[CStatusBar::GetItemRect](../Topic/CStatusBar::GetItemRect.md)|取得位於指定索引的顯示矩形。|  
|[CStatusBar::GetPaneInfo](../Topic/CStatusBar::GetPaneInfo.md)|取得顯示 ID、樣式和寬度指定索引的。|  
|[CStatusBar::GetPaneStyle](../Topic/CStatusBar::GetPaneStyle.md)|取得位於指定索引的顯示樣式。|  
|[CStatusBar::GetPaneText](../Topic/CStatusBar::GetPaneText.md)|取得指定索引上的顯示文字。|  
|[CStatusBar::GetStatusBarCtrl](../Topic/CStatusBar::GetStatusBarCtrl.md)|允許傳送至基礎通用控制項的直接存取。|  
|[CStatusBar::SetIndicators](../Topic/CStatusBar::SetIndicators.md)|設定顯示 ID。|  
|[CStatusBar::SetPaneInfo](../Topic/CStatusBar::SetPaneInfo.md)|設定顯示 ID、樣式和寬度指定索引的。|  
|[CStatusBar::SetPaneStyle](../Topic/CStatusBar::SetPaneStyle.md)|設定指定之索引處的顯示模式。|  
|[CStatusBar::SetPaneText](../Topic/CStatusBar::SetPaneText.md)|設定指定之索引的顯示文字。|  
  
## 備註  
 輸出窗格最常使用在訊息列和目前狀態指示。  範例包括簡短說明選擇的功能表命令和顯示 SCROLL LOCK、NUM LOCK 和其他按鍵狀態的功能表說明訊息行。  
  
 [CStatusBar::GetStatusBarCtrl](../Topic/CStatusBar::GetStatusBarCtrl.md)，成員函式新增至 MFC 4.0，可讓您利用 Windows 通用控制項支援狀態列自訂和其他功能。  `CStatusBar` 成員函式讓您最新 Windows 通用控制項的功能，不過，在中，當您呼叫 `GetStatusBarCtrl`時，您可以將狀態列 Windows 95 特性\/98 狀態列。  當您呼叫 `GetStatusBarCtrl`，它將會傳回 `CStatusBarCtrl` 物件的參考。  使用 Windows 通用控制項，請參閱 [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) 有關設計工具列的詳細資訊。  如需通用控制項的詳細資訊，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)][通用控制項](http://msdn.microsoft.com/library/windows/desktop/bb775493) 。  
  
 這個架構在最左方的顯示的陣列儲存資訊顯示在位置 0。  當您建立狀態列時，您可使用陣列架構與對應的顯示的字串識別項。  您可以使用字串 ID 或索引存取顯示。  
  
 根據預設，第一個顯示為「項目的」:其佔用其他窗格會顯示未使用的狀態列長度，因此，其他窗格靠右對齊。  
  
 若要建立狀態列，請依照下列步驟執行:  
  
1.  `CStatusBar` 建構物件。  
  
2.  呼叫 [建立](../Topic/CStatusBar::Create.md) \(或\) [CreateEx](../Topic/CStatusBar::CreateEx.md)函式建立狀態列視窗並附加至 `CStatusBar` 物件。  
  
3.  呼叫 [SetIndicators](../Topic/CStatusBar::SetIndicators.md) 關聯字串 ID 與每個顯示。  
  
 有三種方式更新狀態列窗格的文字:  
  
1.  呼叫更新只在  窗格中的 [CWnd::SetWindowText](../Topic/CWnd::SetWindowText.md) 0 的文字。  
  
2.  在狀態列中 `ON_UPDATE_COMMAND_UI` 處理常式的呼叫 [CCmdUI::SetText](../Topic/CCmdUI::SetText.md) 。  
  
3.  呼叫更新任何窗格的文字 [SetPaneText](../Topic/CStatusBar::SetPaneText.md) 。  
  
 呼叫更新狀態列窗格的樣式的 [SetPaneStyle](../Topic/CStatusBar::SetPaneStyle.md) 。  
  
 如需使用 `CStatusBar`的詳細資訊，請參閱本文 [在 MFC 狀態列實作](../../mfc/status-bar-implementation-in-mfc.md) 和 [Technical Note 31:控制項陣列。](../../mfc/tn031-control-bars.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `CStatusBar`  
  
## 需求  
 **Header:** afxext.h  
  
## 請參閱  
 [MFC 範例 CTRLBARS](../../top/visual-cpp-samples.md)   
 [MFC 範例 DLG CBR32](../../top/visual-cpp-samples.md)   
 [CControlBar Class](../../mfc/reference/ccontrolbar-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CStatusBarCtrl Class](../../mfc/reference/cstatusbarctrl-class.md)   
 [CControlBar Class](../../mfc/reference/ccontrolbar-class.md)   
 [CWnd::SetWindowText](../Topic/CWnd::SetWindowText.md)   
 [CStatusBar::SetIndicators](../Topic/CStatusBar::SetIndicators.md)