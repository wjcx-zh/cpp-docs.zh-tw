---
title: 功能表和資源：容器新增
ms.date: 11/04/2016
f1_keywords:
- IDP_OLE_INIT_FAILED
- IDP_FAILED_TO_CREATE
- VK_ESCAPE
helpviewer_keywords:
- application accelerator table [MFC]
- VK_ESCAPE key [MFC]
- IDP_FAILED_TO_CREATE macro [MFC]
- visual editing, application menus and resources
- OLE containers [MFC], menus and resources
- accelerator tables [MFC], container applications
- IDP_OLE_INIT_FAILED macro [MFC]
- CONTAIN tutorial [MFC]
- Links menu item [MFC]
ms.assetid: 425448be-8ca0-412e-909a-a3a9ce845288
ms.openlocfilehash: ea4159f8eb60f43f60eacd5831ce148c81aeb572
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546610"
---
# <a name="menus-and-resources-container-additions"></a>功能表和資源：容器新增

這篇文章會說明所需對功能表和視覺化編輯容器應用程式中的其他資源所做的變更。

容器應用程式，在兩種類型的變更需要成為： 修改現有的資源，以支援 OLE 視覺化編輯和新增新的資源用於就地啟用。 如果您使用應用程式精靈 來建立容器應用程式時，會為您完成這些步驟，但它們可能需要一些自訂。

如果您不使用應用程式精靈，您可能想要查看 OCLIENT。RC，OCLIENT 範例應用程式，以查看如何實作這些變更的資源指令碼。 請參閱 MFC OLE 範例[OCLIENT](../visual-cpp-samples.md)。

本文章涵蓋的主題包括：

- [容器的功能表新增](#_core_container_menu_additions)

- [快速鍵對應表加入](#_core_container_application_accelerator_table_additions)

- [字串資料表加入](#_core_string_table_additions_for_container_applications)

##  <a name="_core_container_menu_additions"></a> 容器的功能表新增

您必須在 [編輯] 功能表中新增下列項目：

|項目|用途|
|----------|-------------|
|**插入新的物件**|開啟 [OLE 插入物件] 對話方塊中，若要插入的文件中的連結或內嵌的項目。|
|**貼上連結**|剪貼簿上貼文件項目的連結。|
|**OLE 指令動詞**|會呼叫選取的項目主要動詞命令。 此功能表項目變更，以反映選取項目的主要的動詞命令的文字。|
|**Links**|開啟 OLE 編輯連結 對話方塊中，若要變更現有連結的項目。|

這篇文章中所列的變更，除了原始程式檔必須包含 AFXOLECL。RC 中，也就是 Microsoft Foundation 類別庫實作所需。 插入新的物件是唯一需要的功能表。 可以新增其他項目，但此處所列的最常見。

如果您想要支援就地啟用包含的項目，您必須建立新的功能表容器應用程式。 這個功能表包含相同的 [檔案] 功能表和視窗檔案已開啟，但它有兩個它們之間的分隔符號時，使用的快顯功能表。 這些分隔符號來表示伺服器 （元件） 項目 （應用程式） 應該放置其功能表時就地啟用。 如需有關這個功能表合併的技巧的詳細資訊，請參閱[功能表和資源： 功能表合併](../mfc/menus-and-resources-menu-merging.md)。

##  <a name="_core_container_application_accelerator_table_additions"></a> 新增容器應用程式快速鍵對應表

不需要，如果您要支援就地啟用容器應用程式的快速鍵對應表資源的小型變更。 第一項變更可讓使用者按下 esc 鍵 (ESC)，若要取消的就地編輯模式。 將下列項目新增至主要的快速鍵對應表中：

|識別碼|Key|類型|
|--------|---------|----------|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

第二項變更，就是建立新的快速鍵對應表對應至新的功能表資源建立就地啟用。 這個資料表有除了以上的 VK_ESCAPE 項目之外的 [檔案和視窗] 功能表項目。 下列範例會建立就地啟用 MFC 範例中的快速鍵對應表[容器](../visual-cpp-samples.md):

|識別碼|Key|類型|
|--------|---------|----------|
|ID_FILE_NEW|CTRL+N|**VIRTKEY**|
|ID_FILE_OPEN|CTRL+O|**VIRTKEY**|
|ID_FILE_SAVE|CTRL+S|**VIRTKEY**|
|ID_FILE_PRINT|CTRL+P|**VIRTKEY**|
|ID_NEXT_PANE|VK_F6|**VIRTKEY**|
|ID_PREV_PANE|SHIFT + VK_F6|**VIRTKEY**|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

##  <a name="_core_string_table_additions_for_container_applications"></a> 字串資料表加入容器應用程式

大部分的容器應用程式的字串資料表的變更對應中所述的額外功能表項目[容器的功能表新增](#_core_container_menu_additions)。 它們提供顯示每個功能表項目時，[狀態] 列中顯示的文字。 例如，以下是應用程式精靈產生的字串資料表項目：

|識別碼|String|
|--------|------------|
|IDP_OLE_INIT_FAILED|OLE 初始化失敗。 請確定 OLE 程式庫的正確版本。|
|IDP_FAILED_TO_CREATE|無法建立物件。 請確定該物件已登錄在系統登錄中。|

## <a name="see-also"></a>另請參閱

[功能表和資源 (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[功能表和資源：伺服器新增](../mfc/menus-and-resources-server-additions.md)

