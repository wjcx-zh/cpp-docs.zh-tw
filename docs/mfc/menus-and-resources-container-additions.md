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
ms.openlocfilehash: c8da58316f471f7b7d26e142cc1dd1ccaa6ad8b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364785"
---
# <a name="menus-and-resources-container-additions"></a>功能表和資源：容器新增

本文介紹了需要在可視化編輯容器應用程式中對功能表和其他資源進行更改。

在容器應用程式中,需要進行兩種類型的更改:對現有資源進行修改以支援 OLE 可視化編輯和添加用於就地啟動的新資源。 如果使用應用程式精靈建立容器應用程式,這些步驟將為您完成,但它們可能需要一些自定義。

如果不使用應用程式精靈,則可能需要查看 OCLIENT。RC,OCLIENT 範例應用程式的資源文本,以查看這些更改是如何實現的。 請參考 MFC OLE 範例[OCLIENT](../overview/visual-cpp-samples.md)。

本文涵蓋的主題包括:

- [容器選單加入](#_core_container_menu_additions)

- [加速器表新增](#_core_container_application_accelerator_table_additions)

- [字串表加入](#_core_string_table_additions_for_container_applications)

## <a name="container-menu-additions"></a><a name="_core_container_menu_additions"></a>容器選單加入

您必須將以下項目加入編輯「編輯」選單:

|Item|目的|
|----------|-------------|
|**插入新物件**|打開"OLE 插入物件"對話框,將連結或嵌入的專案插入到文檔中。|
|**貼上連結**|將指向剪貼簿上專案的連結粘貼到文檔中。|
|**OLE 動詞**|調用所選項的主謂詞。 此選單項的文本將更改以反映所選項的主謂詞。|
|**連結**|打開"OLE 編輯連結"對話框以更改現有連結專案。|

除了本文中列出的更改之外,源檔還必須包含 AFXOLECL。RC,這是 Microsoft 基礎類庫實現所必需的。 插入新對像是唯一需要添加的菜單。 可以添加其他專案,但此處列出的專案是最常見的。

如果要支援包含項的就地啟動,則必須為容器應用程式創建新功能表。 此功能表由相同的文件選單和視窗彈出功能表組成,當文件打開時使用,但它有兩個分隔符放置在它們之間。 這些分隔符用於指示伺服器(元件)項(應用程式)在啟動時應將其功能表放置的位置。 有關此選單合併技術的詳細資訊,請參閱[選單和資源:選單合併](../mfc/menus-and-resources-menu-merging.md)。

## <a name="container-application-accelerator-table-additions"></a><a name="_core_container_application_accelerator_table_additions"></a>容器應用程式加速器表新增

如果支援就地啟動,則需要對容器應用程式的加速器表資源進行少量更改。 第一個更改允許使用者按轉義鍵 (ESC) 取消就地編輯模式。 將以下項目加入主加速器表:

|ID|Key|類型|
|--------|---------|----------|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

第二個更改是創建一個新的快速鍵表,該表對應於為就地啟動而創建的新菜單資源。 除了上面VK_ESCAPE條目外,此表還包含「檔和視窗」功能表的項目。 下面的範例是為 MFC 範例[CONTAINER](../overview/visual-cpp-samples.md)中為就地啟動而建立的加速器表:

|ID|Key|類型|
|--------|---------|----------|
|ID_FILE_NEW|CTRL+N|**VIRTKEY**|
|ID_FILE_OPEN|CTRL+O|**VIRTKEY**|
|ID_FILE_SAVE|CTRL+S|**VIRTKEY**|
|ID_FILE_PRINT|CTRL+P|**VIRTKEY**|
|ID_NEXT_PANE|VK_F6|**VIRTKEY**|
|ID_PREV_PANE|SHIFT_VK_F6|**VIRTKEY**|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

## <a name="string-table-additions-for-container-applications"></a><a name="_core_string_table_additions_for_container_applications"></a>容器應用程式的字串表新增

容器應用程式的字串表的大部分更改都對應於[容器功能表添加](#_core_container_menu_additions)中提及的其他功能表項。 當顯示每個功能表項時,它們提供狀態列中顯示的文本。 例如,下面是應用程式精靈產生的字串表條目:

|ID|String|
|--------|------------|
|IDP_OLE_INIT_FAILED|OLE 初始化失敗。 確保 OLE 庫是正確的版本。|
|IDP_FAILED_TO_CREATE|無法創建物件。 確保物件是在系統註冊表中輸入的。|

## <a name="see-also"></a>另請參閱

[功能表和資源 (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[功能表和資源：伺服器新增](../mfc/menus-and-resources-server-additions.md)
