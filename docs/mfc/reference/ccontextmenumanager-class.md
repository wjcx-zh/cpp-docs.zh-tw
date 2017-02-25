---
title: "CContextMenuManager Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CContextMenuManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CContextMenuManager class"
ms.assetid: 1de20640-243c-47e1-85de-1baa4153bc83
caps.latest.revision: 32
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 33
---
# CContextMenuManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CContextMenuManager` 物件處理捷徑功能表，也稱為內容功能表。  
  
## 語法  
  
```  
class CContextMenuManager : public CObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CContextMenuManager::CContextMenuManager](../Topic/CContextMenuManager::CContextMenuManager.md)|建構 `CContextMenuManager` 物件。|  
|`CContextMenuManager::~CContextMenuManager`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CContextMenuManager::AddMenu](../Topic/CContextMenuManager::AddMenu.md)|將新的捷徑功能表。|  
|[CContextMenuManager::GetMenuById](../Topic/CContextMenuManager::GetMenuById.md)|將控制代碼傳回給功能表與提供的資源 ID。.|  
|[CContextMenuManager::GetMenuByName](../Topic/CContextMenuManager::GetMenuByName.md)|將控制代碼傳回給符合提供的功能表名稱的功能表。|  
|[CContextMenuManager::GetMenuNames](../Topic/CContextMenuManager::GetMenuNames.md)|傳回功能表名稱清單。|  
|[CContextMenuManager::LoadState](../Topic/CContextMenuManager::LoadState.md)|裝載在 Windows 登錄中儲存的捷徑功能表。|  
|[CContextMenuManager::ResetState](../Topic/CContextMenuManager::ResetState.md)|清除內容功能表處理常式的捷徑功能表。|  
|[CContextMenuManager::SaveState](../Topic/CContextMenuManager::SaveState.md)|將捷徑功能表附加至 Windows 登錄中。|  
|[CContextMenuManager::SetDontCloseActiveMenu](../Topic/CContextMenuManager::SetDontCloseActiveMenu.md)|控制項 `CContextMenuManager` 是否關閉使用中的捷徑功能表，因為它會顯示新的捷徑功能表。|  
|[CContextMenuManager::ShowPopupMenu](../Topic/CContextMenuManager::ShowPopupMenu.md)|顯示指定的捷徑功能表。|  
|[CContextMenuManager::TrackPopupMenu](../Topic/CContextMenuManager::TrackPopupMenu.md)|顯示指定的捷徑功能表。  傳回選取的功能表命令的索引。|  
  
## 備註  
 `CContextMenuManager` 處理捷徑功能表並確定它們都有一致的外觀。  
  
 您無法以手動方式建立 `CContextMenuManager` 物件。  您的應用程式架構建立 `CContextMenuManager` 物件。  不過，在中，當您的應用程式初始化時，應該呼叫 [CWinAppEx::InitContextMenuManager](../Topic/CWinAppEx::InitContextMenuManager.md) 。  在初始化內容處理常式之後，請使用方法 [CWinAppEx::GetContextMenuManager](../Topic/CWinAppEx::GetContextMenuManager.md) 取得指標給您應用程式的內容處理常式。  
  
 您可以建立捷徑功能表在執行階段時呼叫 `AddMenu`。  如果您想要顯示功能表，而不用先接收使用者的輸入，請呼叫 `ShowPopupMenu`。  `TrackPopupMenu` ，當您想要建立功能表和等候使用者輸入時，使用。  `TrackPopupMenu` 傳回索引選項的命令或 0，如果使用者關閉，但未選取任何項目。  
  
 `CContextMenuManager` 也可以儲存和載入它的狀態至 Windows 登錄中。  
  
## 範例  
 當 `CContextMenuManager` 物件顯示新的快顯功能表時，下列範例會示範如何將功能表加入至 `CContextMenuManager` 物件以及如何不關閉使用中的快顯功能表。  這個程式碼片段是 [自訂呼叫範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_CustomPages#4](../../mfc/reference/codesnippet/CPP/ccontextmenumanager-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)  
  
## 需求  
 **標題:** afxcontextmenumanager.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx Class](../../mfc/reference/cwinappex-class.md)   
 [CWinAppEx::InitContextMenuManager](../Topic/CWinAppEx::InitContextMenuManager.md)