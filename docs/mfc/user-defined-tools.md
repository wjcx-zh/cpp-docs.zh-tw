---
title: 使用者定義類型
ms.date: 11/19/2018
helpviewer_keywords:
- user-defined tools (MFC Extensions)
ms.assetid: cb887421-78ce-4652-bc67-96a53984ccaa
ms.openlocfilehash: df8ba98fa1986052bae82b2afbdf40725298bef7
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175726"
---
# <a name="user-defined-tools"></a>使用者定義類型

MFC 支援使用者定義的工具。 使用者定義的工具是執行外部的使用者指定的程式的特殊命令。 您可以使用自訂程序來管理使用者定義的工具。 不過，您無法使用此程序如果您的應用程式的物件不衍生自[CWinAppEx 類別](../mfc/reference/cwinappex-class.md)。 如需有關自訂的詳細資訊，請參閱 < [MFC 自訂](../mfc/customization-for-mfc.md)。

如果您啟用使用者定義的工具支援，自訂 對話方塊會自動包含**工具** 索引標籤。如下圖所示**工具**頁面。

![工具索引標籤的 [自訂] 對話方塊](../mfc/media/custdialogboxtoolstab.png "工具 索引標籤，在 [自訂] 對話方塊") <br/>
自訂對話方塊的 工具索引標籤

## <a name="enabling-user-defined-tools-support"></a>啟用使用者定義工具支援

若要啟用應用程式中的使用者定義的工具，請呼叫[CWinAppEx::EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools)。 不過，您必須先定義數個常數在資源檔來作為參數，這個呼叫的應用程式中。

在資源編輯器中建立的 dummy 的命令，使用適當的命令 id。 在下列範例中，我們會使用`ID_TOOLS_ENTRY`做為命令識別碼。 這個命令識別碼將標記的位置，在一或多個功能表中，架構會在該處插入使用者定義的工具。

您必須設定保留某些連續識別碼字串資料表中的代表使用者定義的工具。 擱置在一旁的字串數目等於使用者可以定義的使用者工具的最大數目。 在下列範例中，這些都命名為`ID_USER_TOOL1`透過`ID_USER_TOOL10`。

您可以提供建議給使用者，以協助他們選取工具的目錄和引數，就會呼叫外部程式。 若要這樣做，請在資源編輯器中建立兩個快顯功能表。 在下列範例中，這些具名`IDR_MENU_ARGS`和`IDR_MENU_DIRS`。 這些功能表中的每個命令，請在您的應用程式的字串資料表中定義的字串。 字串的資源識別碼必須等於命令識別碼。

您也可以建立從衍生的類別[CUserTool 類別](../mfc/reference/cusertool-class.md)取代預設實作。 若要這樣做，傳遞您的衍生類別的執行階段資訊做為 CWinAppEx::EnableUserTools，而不是 RUNTIME_CLASS 的第四個參數 ([CUserTool 類別](../mfc/reference/cusertool-class.md))。

定義適當的常數之後，請呼叫[CWinAppEx::EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools)啟用使用者定義的工具。

下列方法呼叫會示範如何使用這些常數：

[!code-cpp[NVC_MFC_VisualStudioDemo#1](../mfc/codesnippet/cpp/user-defined-tools_1.cpp)]

在此範例中，工具 索引標籤將會包含在**自訂** 對話方塊。 此架構將會取代任何符合的命令 ID 的命令`ID_TOOLS_ENTRY`在每次使用者開啟該功能表時，目前定義的使用者工具組的任何功能表。 命令 Id`ID_USER_TOOL1`透過`ID_USER_TOOL10`僅保留以供用於使用者定義的工具。 此類別[CUserTool 類別](../mfc/reference/cusertool-class.md)處理的使用者工具的呼叫。 工具 索引標籤**自訂** 對話方塊會提供按鈕右邊的引數和目錄的項目欄位來存取功能表**IDR_MENU_ARGS**和**IDR_MENU_DIRS**.時使用者會選取其中一個這些功能表命令，架構會將附加到適當的文字方塊中具有等於命令 id。 資源識別碼的字串

### <a name="including-predefined-tools"></a>其中包括預先定義的工具

如果您想要預先定義的應用程式啟動時的一些工具，您必須覆寫[CFrameWnd::LoadFrame](../mfc/reference/cframewnd-class.md#loadframe)的應用程式的主視窗的方法。 在該方法中，您必須執行下列步驟。

##### <a name="to-add-new-tools-in-loadframe"></a>LoadFrame 中加入新的工具

1. 取得指標[CUserToolsManager 類別](../mfc/reference/cusertoolsmanager-class.md)藉由呼叫物件[CWinAppEx::GetUserToolsManager](../mfc/reference/cwinappex-class.md#getusertoolsmanager)。

1. 針對您想要建立每個工具，呼叫[CUserToolsManager::CreateNewTool](../mfc/reference/cusertoolsmanager-class.md#createnewtool)。 這個方法傳回的指標[CUserTool 類別](../mfc/reference/cusertool-class.md)物件並將新建立的使用者工具加入至內部集合的工具。 如果您提供的衍生類別的執行階段資訊[CUserTool 類別](../mfc/reference/cusertool-class.md)的第四個參數作為[CWinAppEx::EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools)， [CUserToolsManager::CreateNewTool](../mfc/reference/cusertoolsmanager-class.md#createnewtool)將會具現化，並改為傳回該類別的執行個體。

1. 對於每個工具，來設定它的文字標籤設定`CUserTool::m_strLabel`並設定其命令，藉由呼叫`CUserTool::SetCommand`。 預設實作[CUserTool 類別](../mfc/reference/cusertool-class.md)會自動從指定的呼叫中的程式中擷取可用的圖示`SetCommand`。

## <a name="see-also"></a>另請參閱

[MFC 自訂](../mfc/customization-for-mfc.md)<br/>
[CUserTool 類別](../mfc/reference/cusertool-class.md)<br/>
[CUserToolsManager 類別](../mfc/reference/cusertoolsmanager-class.md)<br/>
[CWinAppEx 類別](../mfc/reference/cwinappex-class.md)
