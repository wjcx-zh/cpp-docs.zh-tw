---
title: "CDockState Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDockState"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDockState class"
  - "dock state"
  - "docking control bars"
  - "docking tool windows"
  - "位置, control bar"
  - "大小"
  - "大小, control bar"
  - "狀態, dockable control bar"
ms.assetid: 09e7c10b-3abd-4cb2-ad36-42420fe6bc36
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CDockState Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

載入的序列化 `CObject` 類別，解除安裝或清除一個或多個停駐控制項的狀態保存在記憶體中 \(檔案\)。  
  
## 語法  
  
```  
class CDockState : public CObject  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDockState::Clear](../Topic/CDockState::Clear.md)|清除內建狀態資訊。|  
|[CDockState::GetVersion](../Topic/CDockState::GetVersion.md)|擷取儲存於中的狀態列的版本號碼。|  
|[CDockState::LoadState](../Topic/CDockState::LoadState.md)|從登錄或 .INI 檔擷取狀態資訊。|  
|[CDockState::SaveState](../Topic/CDockState::SaveState.md)|儲存狀態資訊至登錄或 INI 檔案。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CDockState::m\_arrBarInfo](../Topic/CDockState::m_arrBarInfo.md)|有些屬性是儲存在中的內建狀態資訊的指標以及每一個控制列的項目。|  
  
## 備註  
 內建狀態由  列的大小和位置，以及是否停駐。  當擷取儲存於中的內建狀態， `CDockState` 檢查列的位置時，則為，如果這個列的目前螢幕上設定不是可見的， `CDockState` 名稱上的位置，使其成為可見的。  `CDockState` 的主要用途是儲存多個控制項的整個狀態和認可的二進位形式會儲存和載入的登錄，應用程式的 .INI 檔，或狀態以 `CArchive` 物件內容的一部分。  
  
 此分隔列可以是任何可停駐控制列，包括一個工具列、狀態列或對話方塊列。  `CDockState` 物件寫入和讀取來回傳遞檔案 `CArchive` 物件。  
  
 [CFrameWnd::GetDockState](../Topic/CFrameWnd::GetDockState.md) 擷取所有框架視窗的 `CControlBar` 狀態資訊物件並將它放入 `CDockState` 物件。  您可以撰寫 `CDockState` 物件的內容至儲存區的使用 [序列化](../Topic/CObject::Serialize.md) 或 [CDockState::SaveState](../Topic/CDockState::SaveState.md)。  如果您稍後要還原的控制列狀態在框架視窗中，您可以用 `Serialize` 或 [CDockState::LoadState](../Topic/CDockState::LoadState.md)載入狀態，則會使用 [CFrameWnd::SetDockState](../Topic/CFrameWnd::SetDockState.md) 應用儲存狀態到框架視窗的控制列。  
  
 如需內建控制項的詳細資訊，請參閱 Microsoft 知識庫文件 [控制項陣列。](../../mfc/control-bars.md)、 [工具列:停駐、浮動](../../mfc/docking-and-floating-toolbars.md)和 [框架視窗](../../mfc/frame-windows.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDockState`  
  
## 需求  
 **Header:** afxadv.h  
  
## 請參閱  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)