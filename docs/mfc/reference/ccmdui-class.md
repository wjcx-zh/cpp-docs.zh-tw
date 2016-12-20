---
title: "CCmdUI Class | Microsoft Docs"
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
  - "CCmdUI"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "按鈕 [C++], 更新為內容變更"
  - "CCmdUI class"
  - "command user interface"
  - "命令 [C++], updating UI"
  - "menus [C++], 更新為內容變更"
  - "狀態, updating user interface object"
  - "工具列 [C++], 更新"
  - "updating user interfaces for commands"
  - "使用者介面, 更新"
ms.assetid: 04eaaaf5-f510-48ab-b425-94665ba24766
caps.latest.revision: 21
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCmdUI Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 `ON_UPDATE_COMMAND_UI` 管理員在 `CCmdTarget`衍生該類別內使用。  
  
## 語法  
  
```  
class CCmdUI  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CCmdUI::ContinueRouting](../Topic/CCmdUI::ContinueRouting.md)|呼叫命令路由機制繼續在路由處理常式的鏈結中目前的訊息。|  
|[CCmdUI::Enable](../Topic/CCmdUI::Enable.md)|啟用或停用命令的使用者介面項目。|  
|[CCmdUI::SetCheck](../Topic/CCmdUI::SetCheck.md)|設定使用者介面項目的檢查狀態命令的。|  
|[CCmdUI::SetRadio](../Topic/CCmdUI::SetRadio.md)|如 `SetCheck` 成員函式，，只是無線群組作業。|  
|[CCmdUI::SetText](../Topic/CCmdUI::SetText.md)|設定使用者介面項目文字命令的。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CCmdUI::m\_nID](../Topic/CCmdUI::m_nID.md)|使用介面的物件 ID。|  
|[CCmdUI::m\_nIndex](../Topic/CCmdUI::m_nIndex.md)|使用介面之物件的索引。|  
|[CCmdUI::m\_pMenu](../Topic/CCmdUI::m_pMenu.md)|為 `CCmdUI` 所表示的功能表上指向物件。|  
|[CCmdUI::m\_pOther](../Topic/CCmdUI::m_pOther.md)|指向 \[視窗\] 物件傳送通知。|  
|[CCmdUI::m\_pSubMenu](../Topic/CCmdUI::m_pSubMenu.md)|為 `CCmdUI` 表示這個所包含的子功能表中的物件。|  
  
## 備註  
 `CCmdUI` 不具有基底類別。  
  
 當您的應用程式使用者拉下功能表時，每個功能表項目需要知道是否要顯示其標記為啟用或停用。  功能表命令的目標將實作 `ON_UPDATE_COMMAND_UI` 管理員提供此資訊。  針對每個在應用程式的命令使用者介面物件，請使用 \[屬性\] 視窗建立每個處理常式的訊息對應 \(Message Map 輸入和函式原型。  
  
 在功能表中拉下時，架構會搜尋並呼叫每個 `ON_UPDATE_COMMAND_UI` 管理員，每一個處理常式呼叫 `CCmdUI` 成員函式 \(例如 **啟用** 和 **核取**，然後，架構會適當地予以顯示每個功能表項目。  
  
 功能表項目可用來控制列按鈕或其他命令使用者介面物件取代，而不需要變更 `ON_UPDATE_COMMAND_UI` 處理常式中的程式碼。  
  
 下表彙總函式以各種命令使用者介面項目的 `CCmdUI` 角色的成員。  
  
|使用者介面項目|啟用|SetCheck|SetRadio|SetText|  
|-------------|--------|--------------|--------------|-------------|  
|Menu item|啟用或停用|檢查 \(×\) 或未指定|使用點的檢查 \(•\)|將項目的文字。|  
|工具列按鈕上|啟用或停用|選取 ，取消選取或不定。|和 `SetCheck`|\(不適用\)|  
|狀態列窗格|讓文字成為可見或不可見的|設定快顯或一般框線|和 `SetCheck`|將窗格設定文字|  
|在 `CDialogBar`一般按鈕|啟用或停用|核取或取消核取核取方塊。|和 `SetCheck`|設定按鈕文字|  
|在 `CDialogBar`一般控制項|啟用或停用|\(不適用\)|\(不適用\)|設定視窗文字|  
  
 如需詳細在使用這個類別，請參閱 [如何更新使用者介面物件](../../mfc/how-to-update-user-interface-objects.md)。  
  
## 繼承階層架構  
 `CCmdUI`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [MFC MDI 範例](../../top/visual-cpp-samples.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)