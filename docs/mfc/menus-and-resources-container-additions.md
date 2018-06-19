---
title: 功能表和資源： 容器新增 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- IDP_OLE_INIT_FAILED
- IDP_FAILED_TO_CREATE
- VK_ESCAPE
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c71e8a79652a86ba412ef829ac1151256d1bf65
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350649"
---
# <a name="menus-and-resources-container-additions"></a>功能表和資源：容器新增
這篇文章會說明需要功能表和其他視覺編輯容器應用程式中的資源進行的變更。  
  
 容器應用程式中，兩種類型的變更需要進行： 修改現有的資源，以支援 OLE 視覺化編輯並加入新的資源用於就地啟用。 如果您使用應用程式精靈建立容器應用程式時，會為您完成這些步驟，但它們可能會需要某項自訂作業。  
  
 如果您不使用應用程式精靈，您可能想要查看 OCLIENT。RC OCLIENT 範例應用程式，以查看如何實作這些變更的資源指令碼。 請參閱 MFC OLE 範例[OCLIENT](../visual-cpp-samples.md)。  
  
 本文涵蓋的主題包括：  
  
-   [容器的功能表新增](#_core_container_menu_additions)  
  
-   [快速鍵對應表加入](#_core_container_application_accelerator_table_additions)  
  
-   [字串資料表加入](#_core_string_table_additions_for_container_applications)  
  
##  <a name="_core_container_menu_additions"></a> 容器的功能表新增  
 您必須在 [編輯] 功能表中新增下列項目：  
  
|項目|用途|  
|----------|-------------|  
|**插入新的物件**|開啟 OLE 的 插入物件對話方塊中，若要連結或內嵌的項目插入文件。|  
|**貼上連結**|將項目的連結剪貼簿貼到文件。|  
|**OLE 指令動詞**|會呼叫選取的項目主要動詞命令。 此功能表項目會變更以反映選取之項目的主要的動詞命令的文字。|  
|**Links**|開啟 OLE [編輯連結] 對話方塊來變更現有連結的項目。|  
  
 除了在本文中所列的變更，原始程式檔必須包含 AFXOLECL。RC 時，所需的 Microsoft Foundation 類別庫實作。 插入新的物件是唯一需要的功能表新增。 可以加入其他項目，但此處所列是最常見。  
  
 如果您想要支援就地啟用的包含的項目，您必須建立新的功能表容器應用程式。 這個功能表包含相同的 [檔案] 功能表和視窗檔案是開啟的但它有兩種它們之間的分隔符號時使用的快顯功能表。 表示伺服器 （元件） 項目 （應用程式） 應該放置其功能表時就地啟動這些分隔符號。 如需有關這個功能表合併的技術的詳細資訊，請參閱[功能表和資源： 功能表合併](../mfc/menus-and-resources-menu-merging.md)。  
  
##  <a name="_core_container_application_accelerator_table_additions"></a> 容器應用程式快速鍵對應表加入  
 不需要，如果您要支援就地啟用容器應用程式的快速鍵對應表資源的小型變更。 第一項變更可讓使用者按 escape 鍵 (ESC) 取消就地編輯模式。 將下列項目加入至主要快速鍵對應表：  
  
|識別碼|Key|類型|  
|--------|---------|----------|  
|**ID_CANCEL_EDIT_CNTR**|VK_ESCAPE|**針對 VIRTKEY**|  
  
 第二項變更是建立新的快速鍵對應表對應至為就地啟動建立新的功能表資源。 這個資料表有除了檔案和視窗的功能表項目**VK_ESCAPE**以上項目。 下列範例會建立就地啟用 MFC 範例中的快速鍵對應表[容器](../visual-cpp-samples.md):  
  
|識別碼|Key|類型|  
|--------|---------|----------|  
|`ID_FILE_NEW`|CTRL+N|**針對 VIRTKEY**|  
|`ID_FILE_OPEN`|CTRL+O|**針對 VIRTKEY**|  
|**ID_FILE_SAVE**|CTRL+S|**針對 VIRTKEY**|  
|**ID_FILE_PRINT**|CTRL+P|**針對 VIRTKEY**|  
|**ID_NEXT_PANE**|VK_F6|**針對 VIRTKEY**|  
|**ID_PREV_PANE**|SHIFT + VK_F6|**針對 VIRTKEY**|  
|**ID_CANCEL_EDIT_CNTR**|VK_ESCAPE|**針對 VIRTKEY**|  
  
##  <a name="_core_string_table_additions_for_container_applications"></a> 容器應用程式的字串資料表加入  
 大部分的容器應用程式的字串資料表的變更會對應至所述的額外功能表項目[容器功能表加入](#_core_container_menu_additions)。 它們提供顯示每個功能表項目時，[狀態] 列中顯示的文字。 例如，以下是應用程式精靈產生的字串資料表項目：  
  
|識別碼|String|  
|--------|------------|  
|**IDP_OLE_INIT_FAILED**|OLE 初始化失敗。 請確定 OLE 程式庫的正確版本。|  
|**IDP_FAILED_TO_CREATE**|無法建立物件。 請確定該物件已登錄在系統登錄。|  
  
## <a name="see-also"></a>另請參閱  
 [功能表和資源 (OLE)](../mfc/menus-and-resources-ole.md)   
 [功能表和資源：伺服器新增](../mfc/menus-and-resources-server-additions.md)

