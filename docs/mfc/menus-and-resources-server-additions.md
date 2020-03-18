---
title: 功能表和資源：伺服器新增
ms.date: 11/04/2016
helpviewer_keywords:
- OLE visual editing servers [MFC]
- accelerator tables [MFC], server applications
- visual editing [MFC], application menus and resources
- server applications [MFC], accelerator table
- string tables [MFC], visual editing applications
- servers [MFC], menu additions
- resources [MFC], server applications
- OLE server applications [MFC], menus and resources
- string editing [MFC], visual editing applications
- IDP_OLE_INIT_FAILED macro [MFC]
- server applications [MFC], OLE menus and resources
- OLE initialization failure [MFC]
ms.assetid: 56ce9e8d-8f41-4db8-8dee-e8b0702d057c
ms.openlocfilehash: c1dfd059572c433e8fd7ccaf6e5c48e880f59cad
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445193"
---
# <a name="menus-and-resources-server-additions"></a>功能表和資源：伺服器新增

本文說明需要對視覺編輯服務器（元件）應用程式中的功能表和其他資源進行的變更。 伺服器應用程式需要對功能表結構和其他資源進行許多新增，因為它可以在三種模式中啟動：獨立、內嵌或就地。 如[功能表和資源（OLE）](../mfc/menus-and-resources-ole.md)一文所述，最多可有四組功能表。 這四個全都用於 MDI 完整伺服器應用程式，而只有三個用於一個袖珍伺服器。 應用程式精靈將會建立所需伺服器類型所需的功能表配置。 可能需要進行一些自訂。

如果您未使用應用程式精靈，您可能會想要查看 HIERSVR。RC，適用于 MFC 範例應用程式[HIERSVR](../overview/visual-cpp-samples.md)的資源腳本，以查看這些變更的執行方式。

本文涵蓋的主題包括：

- [新增伺服器功能表](#_core_server_menu_additions)

- [快速鍵對應表新增](#_core_server_application_accelerator_table_additions)

- [新增字串資料表](../mfc/menus-and-resources-container-additions.md)

- [新增的袖珍](#_core_mini.2d.server_additions)

##  <a name="_core_server_menu_additions"></a>新增伺服器功能表

伺服器（元件）應用程式必須已加入功能表資源，以支援 OLE 視覺效果編輯。 在獨立模式中執行應用程式時所使用的功能表不需要變更，但您必須在建立應用程式之前加入兩個新的功能表資源：一個用來支援就地啟用，另一個則支援完全開啟的伺服器。 全和袖珍應用程式都使用這兩個功能表資源。

- 若要支援就地啟用，您必須建立與在獨立模式中執行時所使用的功能表資源非常類似的功能表資源。 此功能表中的差異在於遺漏檔案和視窗專案（以及處理應用程式的任何其他功能表項目，而不是資料）。 容器應用程式會提供這些功能表項目。 如需的詳細資訊，以及此功能表合併技術的範例，請參閱文章功能表[和資源：功能表合併](../mfc/menus-and-resources-menu-merging.md)。

- 若要支援完全開啟的啟用，您必須建立與在獨立模式中執行時所使用的功能表資源幾乎相同的功能表資源。 此功能表資源的唯一修改是改寫一些專案，以反映伺服器在內嵌于複合檔案中的專案上運作的事實。

除了本文所列的變更之外，您的資源檔也必須包含 AFXOLESV。RC，這是 MFC 程式庫執行所需的。 此檔案位於 MFC\Include 子目錄中。

##  <a name="_core_server_application_accelerator_table_additions"></a>伺服器應用程式加速器資料表新增專案

您必須將兩個新的快速鍵對應表資源加入伺服器應用程式中。它們直接對應到先前所述的新功能表資源。 當伺服器應用程式已啟用時，會使用第一個快速鍵對應表。 它包含視圖的快速鍵對應表中的所有專案，但系結至 [檔案] 和 [視窗] 功能表除外。

第二個數據表幾乎是視圖快速鍵對應表的確切複本。 在 [[伺服器] 功能表新增](#_core_server_menu_additions)專案中所述的完整開啟功能表中，任何差異的平行變更。

如需這些快速鍵對應表變更的範例，請將 IDR_HIERSVRTYPE_SRVR_IP 和 IDR_HIERSVRTYPE_SRVR_EMB 快速鍵對應表與 HIERSVR 中的 IDR_MAINFRAME 進行比較。包含在 MFC OLE 範例[HIERSVR](../overview/visual-cpp-samples.md)中的 RC 檔案。 就地資料表中缺少檔案和視窗加速器，而且它們的完整複本位於內嵌資料表中。

##  <a name="_core_string_table_additions_for_server_applications"></a>伺服器應用程式的字串資料表新增專案

伺服器應用程式中只需要加入一個字串資料表，這是表示 OLE 初始化失敗的字串。 例如，以下是應用程式精靈產生的字串資料表專案：

|ID|String|
|--------|------------|
|IDP_OLE_INIT_FAILED|OLE 初始化失敗。 請確定 OLE 程式庫是正確的版本。|

##  <a name="_core_mini.2d.server_additions"></a>新增的袖珍

相同的新增專案也適用于 miniservers，如以上所列的完整伺服器。 因為無法在獨立模式中執行「袖珍」，所以其主要功能表會變得很小。 應用程式精靈所建立的主功能表只有 [檔案] 功能表，其中只包含 [結束] 和 [關於] 專案。 適用于 miniservers 的內嵌和就地功能表和加速器與完整伺服器相同。

## <a name="see-also"></a>另請參閱

[功能表和資源 (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[功能表和資源：功能表合併](../mfc/menus-and-resources-menu-merging.md)
