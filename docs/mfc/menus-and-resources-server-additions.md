---
title: "功能表和資源： 伺服器加入 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDP_OLE_INIT_FAILED
dev_langs: C++
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
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 65417079c3241feca9c43e058026674c6e35d18b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="menus-and-resources-server-additions"></a>功能表和資源：伺服器新增
這篇文章會說明需要功能表和其他視覺編輯伺服器 （元件） 應用程式中的資源進行的變更。 伺服器應用程式需要許多的新增項目，功能表結構和其他資源，因為它可以啟動在三種模式之一： 獨立、 內嵌的或在地方。 中所述[功能表和資源 (OLE)](../mfc/menus-and-resources-ole.md)發行項，最多四組功能表。 所有四個用於 MDI 全伺服應用程式，而只有三個適用於迷你伺服程式。 應用程式精靈會建立功能表配置所需的您想要的伺服器類型。 您可能需要某項自訂作業。  
  
 如果您不使用應用程式精靈，您可能想要查看 HIERSVR。RC 中，MFC 範例應用程式的資源指令碼[HIERSVR](../visual-cpp-samples.md)，以查看如何實作這些變更。  
  
 本文涵蓋的主題包括：  
  
-   [伺服器功能表新增](#_core_server_menu_additions)  
  
-   [快速鍵對應表加入](#_core_server_application_accelerator_table_additions)  
  
-   [字串資料表加入](../mfc/menus-and-resources-container-additions.md)  
  
-   [Miniserver 新增項目](#_core_mini.2d.server_additions)  
  
##  <a name="_core_server_menu_additions"></a>伺服器功能表新增  
 伺服器 （元件） 應用程式必須加入以支援 OLE 視覺化編輯功能表資源。 獨立模式中執行應用程式時所使用的功能表就不需要變更，但是建置應用程式之前，您必須新增兩個新的功能表資源： 另一種支援就地啟用，以支援完全開啟的伺服器的另一個。 完整和迷你伺服應用程式會使用兩個功能表資源。  
  
-   若要支援就地啟用，您必須建立功能表資源，非常類似於在獨立模式中執行時所使用的功能表資源。 此功能表中的差異是檔案和視窗項目 （以及應用程式，而非資料處理的任何其他功能表項目） 會遺失。 容器應用程式將會提供這些功能表項目。 如需詳細資訊和此功能表合併的技巧的範例，請參閱文章[功能表和資源： 功能表合併](../mfc/menus-and-resources-menu-merging.md)。  
  
-   若要支援完全開啟啟動，您必須建立功能表資源幾乎完全相同的功能表資源在獨立模式中執行時。 此功能表資源的唯一修改是某些項目會以內嵌於複合文件中的項目上反映伺服器正在運作的事實改寫。  
  
 除了在本文中所列的變更，您的資源檔必須包含 AFXOLESV。RC 時，所需的 Microsoft Foundation 類別庫實作。 這個檔案位於 MFC\Include 子目錄。  
  
##  <a name="_core_server_application_accelerator_table_additions"></a>伺服器應用程式快速鍵對應表加入  
 兩個新的快速鍵對應表資源必須新增至伺服器應用程式。它們直接對應到新的功能表資源先前所述。 就地啟動伺服器應用程式時，會使用第一個的快速鍵對應表。 它會組成檢視的快速鍵對應表中的所有項目，除了檔案和視窗功能表。  
  
 第二個資料表是幾乎完全相同複本檢視的快速鍵對應表。 任何差異平行中所述完全開啟的功能表中所做的變更[伺服器功能表加入](#_core_server_menu_additions)。  
  
 如需這些快速鍵對應表變更的範例，請比較**IDR_HIERSVRTYPE_SRVR_IP**和**IDR_HIERSVRTYPE_SRVR_EMB**快速鍵對應表與**IDR_MAINFRAME**在 HIERSVR。RC 檔包含在 MFC OLE 範例[HIERSVR](../visual-cpp-samples.md)。 檔案和視窗快速鍵就地資料表中遺失，而與副本中內嵌的資料表。  
  
##  <a name="_core_string_table_additions_for_server_applications"></a>字串資料表加入伺服器應用程式  
 只能有一個字串資料表是必要的伺服器應用程式，以表示 OLE 初始化失敗的字串。 例如，以下是應用程式精靈產生的字串資料表項目：  
  
|ID|字串|  
|--------|------------|  
|**IDP_OLE_INIT_FAILED**|OLE 初始化失敗。 請確定 OLE 程式庫的正確版本。|  
  
##  <a name="_core_mini.2d.server_additions"></a>Miniserver 新增項目  
 加入項目套用與以上所列的迷你伺服程式的完整伺服器。 迷你伺服程式無法在獨立模式中執行，因為其主功能表是小很多。 應用程式精靈所建立的主功能表還包含只有檔案 功能表，只包含項目結束和關於。 內嵌和就地功能表和迷你伺服程式的快速鍵都與完整伺服器相同的。  
  
## <a name="see-also"></a>另請參閱  
 [功能表和資源 (OLE)](../mfc/menus-and-resources-ole.md)   
 [功能表和資源：功能表合併](../mfc/menus-and-resources-menu-merging.md)

