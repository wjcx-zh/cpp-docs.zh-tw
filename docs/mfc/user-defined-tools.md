---
title: "使用者定義類型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "使用者定義工具 (MFC 擴充功能)"
ms.assetid: cb887421-78ce-4652-bc67-96a53984ccaa
caps.latest.revision: 18
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用者定義類型
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 支援使用者定義的工具。  一個使用者定義的工具是執行外部，使用者指定的程式的特殊命令。  您可以使用自訂的程序處理使用者定義的工具。  不過，因此，如果您的應用程式物件從 [CWinAppEx Class](../mfc/reference/cwinappex-class.md)，不是衍生自您無法使用這個程序。  如需自訂的詳細資訊，請參閱 [MFC 自訂](../mfc/customization-for-mfc.md)。  
  
 如果啟用了使用者定義的工具支援，自訂對話方塊會自動包含 \[**工具**\] 索引標籤。  下圖顯示 \[**工具**\] 頁面。  
  
 ![&#91;自訂&#93; 對話方塊中的 &#91;工具&#93; 索引標籤](../mfc/media/custdialogboxtoolstab.png "CustDialogBoxToolsTab")  
自訂對話方塊工具選項  
  
## 啟用使用者定義的工具支援  
 若要啟用應用程式的使用者定義的工具，請呼叫 [CWinAppEx::EnableUserTools](../Topic/CWinAppEx::EnableUserTools.md)。  不過，您必須先定義在應用程式資源檔中的數個常數當做參數傳遞至這個呼叫。  
  
 在資源編輯器中建立使用適當的命令 ID. 的假的命令  在下列範例中，我們會使用 **ID\_TOOLS\_ENTRY**做為命令識別碼 .  這個命令 ID 指示架構中插入使用者定義工具一或多個功能表的位置。  
  
 您可以在字串資料表內必須保留一些連續 ID 代表使用者定義的工具。  您保留字串數目與的使用者工具最大數目相等的使用者定義。  在下列範例中，這些命名為 **ID\_USER\_TOOL1** 透過 **ID\_USER\_TOOL10**。  
  
 您可以為使用者提供建議協助它們會呼叫做為工具的外部程式選取目錄和引數。  若要這麼做，請在資源編輯器中兩個快顯功能表。  在下列範例中這些命名為 **IDR\_MENU\_ARGS** 和 **IDR\_MENU\_DIRS**。  對於這些功能表中的每一個命令，請定義字串在應用程式字串資料表內。  字串的資源識別碼必須等於命令 ID.  
  
 您也可以從 [CUserTool Class](../mfc/reference/cusertool-class.md) 的衍生類別取代預設實作。  若要這麼做，請將您的衍生類別的執行階段資訊做為第四個參數在 CWinAppEx::EnableUserTools，而不是 RUNTIME\_CLASS \([CUserTool Class](../mfc/reference/cusertool-class.md)\)。  
  
 在定義適當的常數之後，呼叫啟用使用者定義工具的 [CWinAppEx::EnableUserTools](../Topic/CWinAppEx::EnableUserTools.md) 。  
  
 下列方法會顯示如何使用這些常數:  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#1](../mfc/codesnippet/CPP/user-defined-tools_1.cpp)]  
  
 在此範例中，工具選項將會包含在 \[**自訂**\] 對話方塊。  架構會取代所有命令符合任何功能表的命令 ID **ID\_TOOLS\_ENTRY** 含有目前定義的使用者工具，每次使用者開啟該功能表。  命令 ID **ID\_USER\_TOOL1** 透過 **ID\_USER\_TOOL10** 是保留給使用者定義工具的使用。  [CUserTool Class](../mfc/reference/cusertool-class.md) 類別處理對使用者工具。  \[**自訂**\] 對話方塊的工具選項在引數和目錄項目欄位右邊的按鈕來存取功能表的 **IDR\_MENU\_ARGS** 和 **IDR\_MENU\_DIRS**。，當使用者選取命令從這些功能表的其中一個時，架構會附加到適當的文字方塊有資源 ID 等於命令 ID. 的字串  
  
### 包含預先定義的工具  
 如果您要定義在應用程式啟動的一些工具，您必須覆寫主視窗的 [CFrameWnd::LoadFrame](../Topic/CFrameWnd::LoadFrame.md) 方法應用程式。  在該方法中，您必須執行下列步驟。  
  
##### 加入新的工具在 LoadFrame  
  
1.  取得指標對 [CUserToolsManager Class](../mfc/reference/cusertoolsmanager-class.md) 物件藉由呼叫 [CWinAppEx::GetUserToolsManager](../Topic/CWinAppEx::GetUserToolsManager.md)。  
  
2.  針對您要建立的每個工具，稱為 [CUserToolsManager::CreateNewTool](../Topic/CUserToolsManager::CreateNewTool.md)。  這個方法會傳回指標對 [CUserTool Class](../mfc/reference/cusertool-class.md) 物件並加入新建立之使用者工具至工具的內部集合。  如果您為 [CUserTool Class](../mfc/reference/cusertool-class.md) 衍生的類別提供了執行階段資訊做為 [CWinAppEx::EnableUserTools](../Topic/CWinAppEx::EnableUserTools.md)第四個參數， [CUserToolsManager::CreateNewTool](../Topic/CUserToolsManager::CreateNewTool.md) 會具現化並傳回該類別的執行個體。  
  
3.  對於每個工具，將 `CUserTool::m_strLabel` 設定其文字標籤並呼叫 `CUserTool::SetCommand`設定它的命令。  [CUserTool Class](../mfc/reference/cusertool-class.md) 的預設實作會在對 `SetCommand`的呼叫所指定的程式自動擷取可用的圖示。  
  
## 請參閱  
 [MFC 自訂](../mfc/customization-for-mfc.md)   
 [CUserTool Class](../mfc/reference/cusertool-class.md)   
 [CUserToolsManager Class](../mfc/reference/cusertoolsmanager-class.md)   
 [CWinAppEx Class](../mfc/reference/cwinappex-class.md)