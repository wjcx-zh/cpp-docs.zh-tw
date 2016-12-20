---
title: "Connecting a Pop-up Menu to Your Application | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "pop-up menus, connecting to applications"
  - "context menus, connecting to applications"
  - "menus, pop-up"
  - "shortcut menus, connecting to applications"
ms.assetid: 295cbf0e-6416-478e-bc3d-472fb98e0e52
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Connecting a Pop-up Menu to Your Application
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### 將快顯功能表連接至您的應用程式  
  
1.  加入 [WM\_CONTEXTMENU](_win32_WM_CONTEXTMENU) 的訊息處理常式 \(舉例來說\)。  如需詳細資訊，請參閱[將訊息對應到函式](../mfc/reference/mapping-messages-to-functions.md)。  
  
2.  將下列程式碼加入至訊息處理常式：  
  
    ```  
    CMenu menu;  
    VERIFY(menu.LoadMenu(IDR_MENU1));  
    CMenu* pPopup = menu.GetSubMenu(0);  
    ASSERT(pPopup != NULL);  
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());  
    ```  
  
    > [!NOTE]
    >  訊息處理常式傳遞的 [CPoint](../atl-mfc-shared/reference/cpoint-class.md) **是在螢幕座標。**  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源檔加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **需求**  
  
 MFC  
  
## 請參閱  
 [Creating Pop\-up Menus](../windows/creating-pop-up-menus.md)   
 [Menu Editor](../mfc/menu-editor.md)   
 [功能表](_win32_Menus)