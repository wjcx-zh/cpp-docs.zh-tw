---
title: "CMouseManager Class | Microsoft Docs"
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
  - "CMouseManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMouseManager class"
ms.assetid: a4d05017-4e44-4a40-8b57-4ece0de20481
caps.latest.revision: 26
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMouseManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

允許使用者檢視關聯的不同命令與特定 [CView](../../mfc/reference/cview-class.md) 物件，在使用者按兩下中的時。  
  
## 語法  
  
```  
class CMouseManager : public CObject  
```  
  
## 成員  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMouseManager::AddView](../Topic/CMouseManager::AddView.md)|將物件加入至 `CView` \[**自訂**\] 對話方塊。  \[**自訂**\] 對話方塊可讓使用者與按兩下每個命令列出的檢視。|  
|[CMouseManager::GetViewDblClickCommand](../Topic/CMouseManager::GetViewDblClickCommand.md)|傳回正在執行的命令，當使用者按兩下提供檢視內時。|  
|[CMouseManager::GetViewIconId](../Topic/CMouseManager::GetViewIconId.md)|傳回圖示與所提供的檢視 ID.|  
|[CMouseManager::GetViewIdByName](../Topic/CMouseManager::GetViewIdByName.md)|傳回檢視 ID 與所提供的檢視名稱。|  
|[CMouseManager::GetViewNames](../Topic/CMouseManager::GetViewNames.md)|擷取所有加入的檢視名稱清單。|  
|[CMouseManager::LoadState](../Topic/CMouseManager::LoadState.md)|從 Windows 登錄載入 `CMouseManager` 狀態。|  
|[CMouseManager::SaveState](../Topic/CMouseManager::SaveState.md)|在  視窗的事件記錄 `CMouseManager` 狀態。|  
|[CMouseManager::SetCommandForDblClk](../Topic/CMouseManager::SetCommandForDblClk.md)|使這個提供的命令和所提供的檢視。|  
  
## 備註  
 `CMouseManager` 類別 `CView` 維護物件的集合。  每個檢視所識別的是依名稱和依 ID.  這些檢視 \[**自訂**\] 在  對話方塊隨即顯示。  使用者可以變更與所有檢視透過 \[**自訂**\] 對話方塊的命令。  當使用者在該檢視中，按兩下這個關聯的命令。  若要支援這個從程式設計的觀點來看，您必須處理 `WM_LBUTTONDBLCLK` 訊息和呼叫程式碼的 [CWinAppEx::OnViewDoubleClick](../Topic/CWinAppEx::OnViewDoubleClick.md) 函式。 `CView` 物件中。  
  
 您無法以手動方式建立 `CMouseManager` 物件。  會由應用程式架構建立。  會自動也會終結它，並在使用者結束應用程式。  若要取得指標應用程式的滑鼠處理常式，請呼叫 [CWinAppEx::GetMouseManager](../Topic/CWinAppEx::GetMouseManager.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMouseManager](../../mfc/reference/cmousemanager-class.md)  
  
## 需求  
 **標題:** afxmousemanager.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx Class](../../mfc/reference/cwinappex-class.md)   
 [鍵盤和滑鼠自訂](../../mfc/keyboard-and-mouse-customization.md)