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
ms.openlocfilehash: a082a75ef0292e190e597f29be0cdc0bd0b497ef
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626232"
---
# <a name="menus-and-resources-container-additions"></a>功能表和資源：容器新增

本文說明需要在視覺編輯容器應用程式中對功能表和其他資源進行的變更。

在容器應用程式中，必須進行兩種類型的變更：修改現有的資源以支援 OLE 視覺編輯，以及新增用於就地啟用的新資源。 如果您使用 [應用程式精靈] 來建立容器應用程式，將會為您完成這些步驟，但可能需要進行一些自訂。

如果您未使用應用程式精靈，您可能會想要查看 OCLIENT。RC，此為 OCLIENT 範例應用程式的資源腳本，以查看如何執行這些變更。 請參閱 MFC OLE 範例[OCLIENT](../overview/visual-cpp-samples.md)。

本文涵蓋的主題包括：

- [新增容器功能表](#_core_container_menu_additions)

- [快速鍵對應表新增](#_core_container_application_accelerator_table_additions)

- [新增字串資料表](#_core_string_table_additions_for_container_applications)

## <a name="container-menu-additions"></a><a name="_core_container_menu_additions"></a>新增容器功能表

您必須將下列專案新增至 [編輯] 功能表：

|項目|目的|
|----------|-------------|
|**插入新物件**|開啟 [OLE 插入物件] 對話方塊，將連結或內嵌專案插入檔中。|
|**貼上連結**|將剪貼簿上的專案連結貼到檔中。|
|**OLE 動詞命令**|呼叫選取專案的主要動詞。 這個功能表項目的文字會變更，以反映所選項目的主要動詞。|
|**連結**|開啟 [OLE 編輯連結] 對話方塊來變更現有連結專案。|

除了本文所列的變更之外，您的來源檔案必須包含 AFXOLECL。RC，這是 MFC 程式庫執行所需的。 [插入新物件] 是唯一需要的功能表加入。 可以新增其他專案，但此處所列的是最常見的專案。

如果您想要支援包含專案的就地啟用，則必須為您的容器應用程式建立新的功能表。 此功能表包含檔案開啟時所使用的相同 [檔案] 功能表和視窗快顯功能表，但是在兩者之間有兩個分隔符號。 這些分隔符號是用來指示伺服器（元件）專案（應用程式）在就地啟動時應放置其功能表的位置。 如需此功能表合併技術的詳細資訊，請參閱功能表[和資源：功能表合併](menus-and-resources-menu-merging.md)。

## <a name="container-application-accelerator-table-additions"></a><a name="_core_container_application_accelerator_table_additions"></a>容器應用程式加速器資料表新增專案

如果您支援就地啟用，則需要對容器應用程式的快速鍵資料表資源進行小型變更。 第一項變更可讓使用者按下 esc 鍵（ESC）來取消就地編輯模式。 將下列專案新增至主要快速鍵對應表：

|ID|按鍵|類型|
|--------|---------|----------|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

第二項變更是建立新的快速鍵對應表，該資料表會對應至為就地啟用而建立的新功能表資源。 除了上述的 VK_ESCAPE 專案以外，此資料表還包含 [檔案] 和 [視窗] 功能表的專案。 下列範例是針對 MFC 範例[容器](../overview/visual-cpp-samples.md)中的就地啟用所建立的快速鍵對應表：

|ID|按鍵|類型|
|--------|---------|----------|
|ID_FILE_NEW|CTRL+N|**VIRTKEY**|
|ID_FILE_OPEN|CTRL+O|**VIRTKEY**|
|ID_FILE_SAVE|CTRL+S|**VIRTKEY**|
|ID_FILE_PRINT|CTRL+P|**VIRTKEY**|
|ID_NEXT_PANE|VK_F6|**VIRTKEY**|
|ID_PREV_PANE|SHIFT + VK_F6|**VIRTKEY**|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

## <a name="string-table-additions-for-container-applications"></a><a name="_core_string_table_additions_for_container_applications"></a>容器應用程式的字串資料表新增

容器應用程式之字串資料表的大部分變更都會對應至 [[容器] 功能表新增](#_core_container_menu_additions)中所述的其他功能表項目。 當每個功能表項目顯示時，他們會提供狀態列中顯示的文字。 例如，以下是應用程式精靈產生的字串資料表專案：

|ID|字串|
|--------|------------|
|IDP_OLE_INIT_FAILED|OLE 初始化失敗。 請確定 OLE 程式庫是正確的版本。|
|IDP_FAILED_TO_CREATE|無法建立物件。 請確定已在系統登錄中輸入物件。|

## <a name="see-also"></a>另請參閱

[功能表和資源 (OLE)](menus-and-resources-ole.md)<br/>
[功能表和資源：伺服器新增](menus-and-resources-server-additions.md)
