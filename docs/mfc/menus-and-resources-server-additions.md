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
ms.openlocfilehash: 8366cd8b0376766b7914c94a24cef6598761a805
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375981"
---
# <a name="menus-and-resources-server-additions"></a>功能表和資源：伺服器新增

本文介紹了需要在可視化編輯伺服器(元件)應用程式中對菜單和其他資源進行更改。 伺服器應用程式需要對菜單結構和其他資源進行許多補充,因為它可以在以下三種模式之一啟動:獨立、嵌入或就地啟動。 如[功能表和資源 (OLE)](../mfc/menus-and-resources-ole.md)文章中所述,最多有四組功能表。 這四個都用於 MDI 全伺服器應用程式,而只有三個用於微型伺服器。 應用程式精靈將創建所需伺服器類型所需的功能表佈局。 可能需要進行一些自定義。

如果不使用應用程式嚮導,則可能需要查看 HIERSVR。RC,MFC 示例應用程式[HIERSVR](../overview/visual-cpp-samples.md)的資源腳本,用於查看這些更改是如何實現的。

本文涵蓋的主題包括:

- [伺服器選單加入](#_core_server_menu_additions)

- [加速器表新增](#_core_server_application_accelerator_table_additions)

- [字串表加入](../mfc/menus-and-resources-container-additions.md)

- [迷你伺服器附加功能](#_core_mini.2d.server_additions)

## <a name="server-menu-additions"></a><a name="_core_server_menu_additions"></a>伺服器選單加入

伺服器(元件)應用程式必須添加功能表資源以支援 OLE 可視化編輯。 在獨立模式下運行應用程式時使用的功能表不必更改,但在構建應用程式之前必須添加兩個新的菜單資源:一個支援就地啟動,一個支援伺服器完全打開。 兩個功能表資源都由完整伺服器和小型伺服器應用程式使用。

- 要支援就地啟動,必須創建與在獨立模式下運行時使用的功能表資源非常相似的菜單資源。 此功能表的區別是缺少「檔和視窗」項(以及處理應用程式(而不是資料的任何其他功能表項)缺失。 容器應用程式將提供這些功能表項。 有關此功能表合併技術的詳細資訊和範例,請參閱文章[「功能表和資源:功能表合併](../mfc/menus-and-resources-menu-merging.md)」。

- 要支援完全打開的啟動,必須創建與在獨立模式下運行時使用的功能表資源幾乎相同的菜單資源。 對此菜單資源的唯一修改是,某些項被重新措辭,以反映伺服器正在對嵌入在複合文檔中的項運行的事實。

除了本文中列出的更改外,您的資源檔還需要包括 AFXOLESV。RC,這是 Microsoft 基礎類庫實現所必需的。 此文件位於MFC_包括子目錄中。

## <a name="server-application-accelerator-table-additions"></a><a name="_core_server_application_accelerator_table_additions"></a>伺服器應用程式加速器表新增

必須向伺服器應用程式添加兩個新的加速器表資源;它們直接對應於前面描述的新菜單資源。 當伺服器應用程式就地啟動時,將使用第一個加速器表。 它由檢視的快捷鍵表中的所有條目組成,但綁定到「檔和視窗」功能表的條目除外。

第二個表幾乎是視圖加速器表的精確副本。 [伺服器功能表添加](#_core_server_menu_additions)中提及的完全打開功能表中所做的任何差異並行更改。

有關這些加速器表更改的範例,請將IDR_HIERSVRTYPE_SRVR_IP和IDR_HIERSVRTYPE_SRVR_EMB加速器表與HIERSVR中的IDR_MAINFRAME進行比較。RC 檔包含在 MFC OLE 範例[HIERSVR](../overview/visual-cpp-samples.md)中。 原位錶中缺少"文件和視窗"快速鍵,並且它們的確切副本位於嵌入表中。

## <a name="string-table-additions-for-server-applications"></a><a name="_core_string_table_additions_for_server_applications"></a>伺服器應用程式的字串表新增

伺服器應用程式中只需要添加一個字串表 - 一個字串表示 OLE 初始化失敗。 例如,下面是應用程式精靈產生的字串表條目:

|ID|String|
|--------|------------|
|IDP_OLE_INIT_FAILED|OLE 初始化失敗。 確保 OLE 庫是正確的版本。|

## <a name="miniserver-additions"></a><a name="_core_mini.2d.server_additions"></a>迷你伺服器附加功能

與上面列出的完整伺服器相同的附加功能適用於小型伺服器。 由於小型伺服器無法以獨立模式運行,因此其主菜單要小得多。 應用程式精靈建立的主選單只有一個文件功能表,僅包含"退出"和"左右"項。 小型伺服器的嵌入式和就地功能表和加速器與完整伺服器的功能表和加速器相同。

## <a name="see-also"></a>另請參閱

[功能表和資源 (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[功能表和資源：功能表合併](../mfc/menus-and-resources-menu-merging.md)
