---
title: "功能表和資源：伺服器新增 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDP_OLE_INIT_FAILED"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "快速鍵對應表 [C++], 伺服器應用程式"
  - "IDP_OLE_INIT_FAILED 巨集"
  - "OLE 初始化失敗"
  - "OLE 伺服器應用程式, 功能表和資源"
  - "OLE 視覺化編輯伺服器"
  - "資源 [MFC], 伺服器應用程式"
  - "伺服器應用程式, 快速鍵對應表"
  - "伺服器應用程式, OLE 功能表和資源"
  - "伺服器, 功能表新增"
  - "字串編輯, 視覺化編輯應用程式"
  - "字串資料表, 視覺化編輯應用程式"
  - "視覺化編輯, 應用程式功能表和資源"
ms.assetid: 56ce9e8d-8f41-4db8-8dee-e8b0702d057c
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 功能表和資源：伺服器新增
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明需要對功能表和其他資源在視覺化編輯伺服器\(元件\)應用程式的變更。  因為可以有三種方式之一啟動伺服器應用程式需要許多加入功能表結構與其他資源:獨立、內嵌或就地。  如 [功能表和資源 \(OLE\)](../mfc/menus-and-resources-ole.md) 文件中所述，最多四組功能表。  而只有三個為 miniserver，四個皆為 MDI 全伺服器應用程式使用。  應用程式精靈會建立您想要的伺服器的型別比要得功能表版面配置。  一些自訂可能是必要的。  
  
 如果您不使用應用程式精靈，您可能想查看 HIERSVR.RC， MFC 範例應用程式 [HIERSVR](../top/visual-cpp-samples.md) 的資源指令碼，查看這些變更如何實作。  
  
 在此文件中包含的主題：  
  
-   [伺服器功能表加入](#_core_server_menu_additions)  
  
-   [快速鍵對應表加入](#_core_server_application_accelerator_table_additions)  
  
-   [字串資料表加入](../mfc/menus-and-resources-container-additions.md)  
  
-   [Miniserver 加入](#_core_mini.2d.server_additions)  
  
##  <a name="_core_server_menu_additions"></a> 伺服器功能表加入  
 伺服器\(元件\)應用程式必須具有加入至支援 OLE 視覺化編輯的功能表資源。  當應用程式在獨立模式中執行時，不需要變更使用的功能表，不過，您必須在建立應用程式的前面加入兩個新的功能表資源：不支援就地啟動另一個是支援的伺服器完整地開啟。  完整和 miniserver 應用程式同時使用功能表資源。  
  
-   若要支援就地啟動，您必須建立非常類似在獨立模式的使用，當執行功能表資源的功能表資源。  在這個功能表的差異是檔案和視窗項目 \(和其他處理應用程式的功能表項目，而不是資料\) 遺失。  容器應用程式將提供這些功能表項目。  如需和這個功能表合併技術及範例的詳細資訊，請參閱這篇文章 [功能表和資源：功能表合併。](../mfc/menus-and-resources-menu-merging.md)。  
  
-   若要支援完全開啟啟動，您必須建立功能表資源幾乎完全相同對在獨立模式的使用，當執行功能表資源。  此功能表資源的唯一修改某些項目將會反映伺服器在複合文件中內嵌的項目作業的事實。  
  
 除了列出的變更以外在本文中，您的資源檔需要包含 AFXOLESV.RC，是 Microsoft Foundation Class 程式庫實作所需的。  這個檔案在 MFC \\ include 子目錄。  
  
##  <a name="_core_server_application_accelerator_table_additions"></a> 伺服器應用程式快速鍵對應表加入  
 必須將兩個新的快速鍵加入至伺服器應用程式；它們會直接對應至前述的新功能表資源。  第一個快速鍵對應表會在伺服器應用程式就地啟動時使用。  它由所有檢視的快速對應表除了與檔案和視窗功能表一起的所有項目所組成。  
  
 第二個資料表幾乎是檢視的快速鍵對應表完全相同的複本。  任何在 [伺服器功能表加入](#_core_server_menu_additions) 提及的完全開啟功能表作的任何差異平行變更。  
  
 如需這些快速鍵對應表變更的範例， **IDR\_HIERSVRTYPE\_SRVR\_IP** 和 **IDR\_HIERSVRTYPE\_SRVR\_EMB** 快速鍵對應表與在 MFC OLE 範例中包含的 HIERSVR.RC 檔案的 **IDR\_MAINFRAME** 比較 [HIERSVR](../top/visual-cpp-samples.md)。  檔案和視窗快速鍵從就地資料表遺失，而與他們完全相同的複本在內嵌資料表。  
  
##  <a name="_core_string_table_additions_for_server_applications"></a> 伺服器應用程式的字串資料表加入  
 只有一個字串資料表加入需要在伺服器應用程式─表示初始化失敗的字串 OLE 。  例如，這是應用程式精靈所產生的字串資料表項目：  
  
|ID|String|  
|--------|------------|  
|**IDP\_OLE\_INIT\_FAILED**|OLE 初始化失敗。  請確認 OLE 程式庫的版本是否正確。|  
  
##  <a name="_core_mini.2d.server_additions"></a> Miniserver 加入  
 同樣地加入應用程式 miniservers 做為全伺服器所列的項目。  由於 miniserver 在獨立模式下無法執行，其主功能表會較小。  應用程式精靈所建立的主功能表中只有一個檔案功能表上，只包含項目和匯出。  內嵌和就地功能表和快速鍵 miniservers 與伺服器相同。  
  
## 請參閱  
 [功能表和資源 \(OLE\)](../mfc/menus-and-resources-ole.md)   
 [功能表和資源：功能表合併](../mfc/menus-and-resources-menu-merging.md)