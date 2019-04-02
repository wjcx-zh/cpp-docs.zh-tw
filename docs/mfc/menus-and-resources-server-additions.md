---
title: 功能表和資源：伺服器新增項目
ms.date: 11/04/2016
f1_keywords:
- IDP_OLE_INIT_FAILED
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
ms.openlocfilehash: 85c7b6059a868e93c6c6a7ebbd7b08dac3233612
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58767195"
---
# <a name="menus-and-resources-server-additions"></a>功能表和資源：伺服器新增項目

這篇文章會說明所需對功能表和視覺化編輯伺服器 （元件） 應用程式中的其他資源所做的變更。 伺服器應用程式需要許多新增項目功能表結構及其他資源，因為它可以啟動三個模式之一： 獨立、 內嵌，或在地方。 中所述[功能表和資源 (OLE)](../mfc/menus-and-resources-ole.md)文章，有四組功能表的最大值。 所有的四個用於 MDI 全伺服應用程式，而只有三個適用於迷你伺服程式。 應用程式精靈 會建立功能表配置所需的您想要的伺服器類型。 您可能需要一些自訂。

如果您不使用應用程式精靈，您可能想要查看 HIERSVR。MFC 範例應用程式的資源指令碼，RC [HIERSVR](../overview/visual-cpp-samples.md)，以查看如何實作這些變更。

本文章涵蓋的主題包括：

- [伺服器 功能表新增項目](#_core_server_menu_additions)

- [快速鍵對應表加入](#_core_server_application_accelerator_table_additions)

- [字串資料表加入](../mfc/menus-and-resources-container-additions.md)

- [Miniserver 新增項目](#_core_mini.2d.server_additions)

##  <a name="_core_server_menu_additions"></a> 伺服器 功能表新增項目

伺服器 （元件） 應用程式必須加入以支援 OLE 視覺化編輯功能表資源。 在獨立模式中執行應用程式時使用的功能表就不需要變更，但之前建置應用程式，您必須新增兩個新的功能表資源： 另一種支援就地啟用，以支援完全開啟伺服器的另一個。 完整和迷你伺服應用程式會使用這兩個功能表資源。

- 若要支援就地啟用，您必須建立功能表資源，非常類似於在獨立模式中執行時所使用的功能表資源。 在此功能表中的差異是檔案和視窗項目 （以及應用程式，並不是資料處理的任何其他功能表項目） 會遺失。 容器應用程式將會提供這些功能表項目。 如需技巧的範例，此功能表合併和等等的詳細資訊，請參閱文章[功能表和資源：功能表合併](../mfc/menus-and-resources-menu-merging.md)。

- 若要支援完全開啟啟動，您必須建立功能表資源幾乎完全相同的功能表資源在獨立模式中執行時。 唯一的修改，此功能表資源時，某些項目會改寫以反映伺服器正在運作的事實，內嵌在複合文件中的項目。

除了這篇文章中所列的變更，您的資源檔必須包含 AFXOLESV。RC 中，也就是 Microsoft Foundation 類別庫實作所需。 這個檔案位於 MFC\Include 子目錄。

##  <a name="_core_server_application_accelerator_table_additions"></a> 新增伺服器應用程式快速鍵對應表

兩個新的快速鍵對應表資源必須新增至伺服器應用程式;它們直接對應到新的功能表資源先前所述。 就地啟動伺服器應用程式時，會使用第一個快速鍵對應表。 它會組成檢視表的快速鍵對應表中的所有項目，但這些繫結至該檔案並視窗功能表。

第二個資料表是幾乎完全相同複本的檢視表的快速鍵對應表。 任何差異中所述完全開啟的功能表中所做的變更[Server 功能表新增](#_core_server_menu_additions)。

如需這些快速鍵對應表變更的範例，比較使用 HIERSVR 中 IDR_MAINFRAME IDR_HIERSVRTYPE_SRVR_IP 和 IDR_HIERSVRTYPE_SRVR_EMB 快速鍵對應表。RC 檔包含在 MFC OLE 範例[HIERSVR](../overview/visual-cpp-samples.md)。 檔案和視窗加速器會就地資料表中遺失，並位於內嵌的資料表中的完整複本。

##  <a name="_core_string_table_additions_for_server_applications"></a> 字串資料表加入伺服器應用程式

加入只有一個字串資料表，不需要伺服器應用程式，以表示 OLE 初始化失敗的字串。 例如，以下是應用程式精靈產生的字串資料表項目：

|識別碼|String|
|--------|------------|
|IDP_OLE_INIT_FAILED|OLE 初始化失敗。 請確定 OLE 程式庫的正確版本。|

##  <a name="_core_mini.2d.server_additions"></a> Miniserver 新增項目

相同的新增項目套用迷你伺服程式，作為以上所列的完整伺服器。 迷你伺服程式無法在獨立模式中執行，因為其主功能表會小很多。 應用程式精靈所建立的主功能表還包含只有檔案 功能表，其中包含只是項目結束和關於。 內嵌和就地功能表和迷你伺服程式的快速鍵是全伺服器相同。

## <a name="see-also"></a>另請參閱

[功能表和資源 (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[功能表和資源：合併的功能表](../mfc/menus-and-resources-menu-merging.md)
