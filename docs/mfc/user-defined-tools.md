---
title: "使用者定義工具 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- user-defined tools (MFC Extensions)
ms.assetid: cb887421-78ce-4652-bc67-96a53984ccaa
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 17f0751a2cb3f78730ec948d737dc99b85c2e735
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="user-defined-tools"></a>使用者定義類型
MFC 支援使用者定義的工具。 使用者定義的工具是執行外部的使用者指定的程式的特殊命令。 您可以使用自訂程序來管理使用者定義的工具。 不過，您無法使用此程序如果應用程式物件不衍生自[CWinAppEx 類別](../mfc/reference/cwinappex-class.md)。 如需有關自訂的詳細資訊，請參閱[MFC 自訂](../mfc/customization-for-mfc.md)。  
  
 如果您啟用使用者定義的工具支援，自訂 對話方塊會自動包含**工具** 索引標籤。下圖顯示**工具**頁面。  
  
 ![工具索引標籤的 [自訂] 對話方塊](../mfc/media/custdialogboxtoolstab.png "custdialogboxtoolstab")  
自訂對話方塊的 工具索引標籤  
  
## <a name="enabling-user-defined-tools-support"></a>啟用使用者定義工具支援  
 若要啟用應用程式中的使用者定義的工具，請呼叫[CWinAppEx::EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools)。 不過，您必須先定義數個常數中當做參數使用此呼叫的應用程式的資源檔中。  
  
 資源編輯器中建立空的命令使用適當的命令識別碼。 在下列範例中，我們使用**ID_TOOLS_ENTRY**為命令識別碼。 此命令識別碼標記一個或多個功能表中，架構會插入使用者定義的工具的位置。  
  
 您必須設定保留某些連續識別碼來代表使用者定義的工具字串資料表中。 擱置在一旁的字串數目等於可定義使用者的使用者工具的最大數目。 在下列範例中，這些具名**ID_USER_TOOL1**透過**ID_USER_TOOL10**。  
  
 您可以提供建議給使用者，以協助他們選取目錄和引數將會呼叫外部程式的工具。 若要這樣做，請在資源編輯器中建立兩個快顯功能表。 在下列範例中，這些具名**IDR_MENU_ARGS**和**IDR_MENU_DIRS**。 對於這些功能表中的每個命令，請在您的應用程式的字串資料表中定義的字串。 字串的資源識別碼必須等於命令 id。  
  
 您也可以建立衍生的類別從[CUserTool 類別](../mfc/reference/cusertool-class.md)來取代預設的實作。 若要這樣做，請將您的衍生類別的執行階段資訊傳遞 CWinAppEx::EnableUserTools，而不是 RUNTIME_CLASS 中第四個參數 ([CUserTool 類別](../mfc/reference/cusertool-class.md))。  
  
 您定義的適當常數之後，請呼叫[CWinAppEx::EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools)來讓使用者定義的工具。  
  
 下列方法呼叫示範如何使用這些常數：  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#1](../mfc/codesnippet/cpp/user-defined-tools_1.cpp)]  
  
 在此範例中，工具 索引標籤將會包含在**自訂** 對話方塊。 此架構將會取代任何符合的命令 ID 的命令**ID_TOOLS_ENTRY**任何功能表與目前定義的使用者工具，每當使用者開啟該功能表的集合中。 命令 Id **ID_USER_TOOL1**透過**ID_USER_TOOL10**是保留供使用的使用者定義的工具。 類別[CUserTool 類別](../mfc/reference/cusertool-class.md)如何處理使用者工具的呼叫。 [工具] 索引標籤的**自訂**對話方塊會提供按鈕右邊的引數和目錄的項目欄位來存取功能表**IDR_MENU_ARGS**和**IDR_MENU_DIRS**.當使用者選取其中一個這些功能表命令時，架構將附加至適當的文字方塊具有等於命令 id。 資源識別碼的字串  
  
### <a name="including-predefined-tools"></a>其中包括預先定義的工具  
 如果您想要在應用程式啟動某些工具會預先定義，您必須覆寫[CFrameWnd::LoadFrame](../mfc/reference/cframewnd-class.md#loadframe)應用程式的主視窗的方法。 在該方法中，您必須執行下列步驟。  
  
##### <a name="to-add-new-tools-in-loadframe"></a>LoadFrame 中加入新的工具  
  
1.  取得指標[CUserToolsManager 類別](../mfc/reference/cusertoolsmanager-class.md)藉由呼叫物件[CWinAppEx::GetUserToolsManager](../mfc/reference/cwinappex-class.md#getusertoolsmanager)。  
  
2.  針對您想要建立每個工具，呼叫[CUserToolsManager::CreateNewTool](../mfc/reference/cusertoolsmanager-class.md#createnewtool)。 這個方法會傳回指標[CUserTool 類別](../mfc/reference/cusertool-class.md)物件並將新建立的使用者工具加入至工具的內部集合。 如果您提供的衍生類別的執行階段資訊[CUserTool 類別](../mfc/reference/cusertool-class.md)做為第四個參數的[CWinAppEx::EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools)， [CUserToolsManager::CreateNewTool](../mfc/reference/cusertoolsmanager-class.md#createnewtool)會具現化，並改為傳回該類別的執行個體。  
  
3.  對於每個工具，來設定其文字標籤設定`CUserTool::m_strLabel`並設定其命令藉由呼叫`CUserTool::SetCommand`。 預設實作[CUserTool 類別](../mfc/reference/cusertool-class.md)從指定的呼叫中的程式會自動擷取可用的圖示`SetCommand`。  
  
## <a name="see-also"></a>請參閱  
 [MFC 自訂](../mfc/customization-for-mfc.md)   
 [CUserTool 類別](../mfc/reference/cusertool-class.md)   
 [CUserToolsManager 類別](../mfc/reference/cusertoolsmanager-class.md)   
 [CWinAppEx 類別](../mfc/reference/cwinappex-class.md)




