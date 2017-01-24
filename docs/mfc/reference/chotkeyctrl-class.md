---
title: "CHotKeyCtrl Class | Microsoft Docs"
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
  - "CHotKeyCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHotKeyCtrl class"
  - "hot key controls"
  - "Windows common controls [C++], CHotKeyCtrl"
ms.assetid: 896f9766-0718-4f58-aab2-20325e118ca6
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CHotKeyCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 Windows 通用熱鍵控制項的功能。  
  
## 語法  
  
```  
class CHotKeyCtrl : public CWnd  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CHotKeyCtrl::CHotKeyCtrl](../Topic/CHotKeyCtrl::CHotKeyCtrl.md)|建構 `CHotKeyCtrl` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CHotKeyCtrl::Create](../Topic/CHotKeyCtrl::Create.md)|建立熱鍵控制項並將其附加至 `CHotKeyCtrl` 物件。|  
|[CHotKeyCtrl::CreateEx](../Topic/CHotKeyCtrl::CreateEx.md)|建立具有指定之視窗的延伸樣式的熱鍵控制項並將其附加至 `CHotKeyCtrl` 物件。|  
|[CHotKeyCtrl::GetHotKey](../Topic/CHotKeyCtrl::GetHotKey.md)|從熱鍵控制項擷取一個快速鍵的虛擬按鍵碼和輔助鍵旗標。|  
|[CHotKeyCtrl::GetHotKeyName](../Topic/CHotKeyCtrl::GetHotKeyName.md)|擷取金鑰名稱，在區域字元集，指派給熱鍵。|  
|[CHotKeyCtrl::GetKeyName](../Topic/CHotKeyCtrl::GetKeyName.md)|擷取金鑰名稱，在區域字元集，指派給指定的虛擬按鍵碼。|  
|[CHotKeyCtrl::SetHotKey](../Topic/CHotKeyCtrl::SetHotKey.md)|設定熱鍵控制項的快速鍵組合。|  
|[CHotKeyCtrl::SetRules](../Topic/CHotKeyCtrl::SetRules.md)|定義無效組合和預設修飾詞 \(Modifier\) 組合的熱鍵控制項。|  
  
## 備註  
 「熱鍵控制項」是可讓使用者建立熱鍵的視窗。  「熱鍵」是使用者可以按下快速執行動作的組合鍵。  \(例如，使用者可以建立啟動特定視窗並在疊置順序最頂端它\)、熱鍵熱鍵控制項會顯示使用者的選擇並確定使用者選取有效的按鍵組合。  
  
 這個控制項 \(也 `CHotKeyCtrl` 類別\) 給在 Windows 95 \/98 和 Windows NT 3.51 版之下的程式才能使用 \(含\) 以後版本。  
  
 當使用者選取的組合鍵時，應用程式可以從控制項擷取指定的組合鍵和使用 **WM\_SETHOTKEY** 訊息設定在系統中的快速鍵。  每當使用者按下快速鍵之後，從系統的任何部分時，  視窗中指定的 **WM\_SETHOTKEY** 訊息接收指定 **SC\_HOTKEY**的 `WM_SYSCOMMAND` 訊息。  這個訊息就會接收到的視窗。  快速鍵維持有效直到呼叫 **WM\_SETHOTKEY** 匯出的應用程式。  
  
 這個機制是取決於 **WM\_HOTKEY** 訊息和視窗 [RegisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646309) 和 [UnregisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646327) 函式支援不同的快速鍵。  
  
 如需使用 `CHotKeyCtrl`的資訊，請參閱 [控制項](../../mfc/controls-mfc.md) 和 [使用 CHotKeyCtrl](../../mfc/using-chotkeyctrl.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CHotKeyCtrl`  
  
## 需求  
 **Header:** afxcmn.h  
  
## 請參閱  
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)