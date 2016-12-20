---
title: "功能表和資源：容器新增 | Microsoft Docs"
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
  - "IDP_FAILED_TO_CREATE"
  - "VK_ESCAPE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "快速鍵對應表 [C++], 容器應用程式"
  - "應用程式快速鍵對應表 [C++]"
  - "CONTAIN 教學課程"
  - "IDP_FAILED_TO_CREATE 巨集"
  - "IDP_OLE_INIT_FAILED 巨集"
  - "連結功能表項目"
  - "OLE 容器, 功能表和資源"
  - "視覺化編輯, 應用程式功能表和資源"
  - "VK_ESCAPE 鍵"
ms.assetid: 425448be-8ca0-412e-909a-a3a9ce845288
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 功能表和資源：容器新增
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明需要對功能表和其他資源在視覺化編輯容器應用程式的變更。  
  
 在容器應用程式，變更的兩種需要進行:對現有資源的修改對支援在就地啟動的新資源的 OLE 視覺化編輯及增加。  如果您使用應用程式精靈來建立您的容器應用程式，這些步驟將為您完成，但是，可能需要一些自訂。  
  
 如果您不使用應用程式精靈，您可能想查看 OCLIENT.RC， OCLIENT 範例應用程式的資源指令碼，查看這些變更的方式實作。  請參閱 MFC OLE [OCLIENT](../top/visual-cpp-samples.md)範例。  
  
 在此文件中包含的主題:  
  
-   [容器功能表加入](#_core_container_menu_additions)  
  
-   [快速鍵對應表加入](#_core_container_application_accelerator_table_additions)  
  
-   [字串資料表加入](#_core_string_table_additions_for_container_applications)  
  
##  <a name="_core_container_menu_additions"></a> 容器功能表加入  
 您必須將下列項目加入至編輯功能表:  
  
|項目|用途|  
|--------|--------|  
|**插入新物件**|開啟 OLE 插入物件對話方塊插入連結或內嵌的項目至文件。|  
|**貼上連結**|貼上連結到剪貼簿的項目至文件。|  
|**OLE 動詞命令**|呼叫選取之項目的主要動詞命令。  此功能表項目的文字會變更以反映選取的項目的主要動詞命令。|  
|**連結**|開啟 OLE 編輯連結對話方塊來變更現有連接的項目。|  
  
 除了列出的變更以外在本文中，您的原始程式檔必須包含 AFXOLECL.RC，對於 MFC 程式庫實作所需的。  將新的物件是唯一必要功能表加入。  其他項目可以增加，不過，所列的這裡是最常見的。  
  
 如果您要支援包含項目的就地啟動，您必須建立自己的容器應用程式的新功能表。  這個功能表包含相同檔案功能表，而 Windows 快顯功能表使用了檔案時是開啟的，不過，它有兩個分隔符號被放置在兩者之間。  這些分隔符號可用來指示伺服器元件 \(\) 項目 \(應用程式\) 要放置其功能表，當就地啟動。  如需這個功能表合併技術的詳細資訊，請參閱 [功能表和資源:功能表合併。](../mfc/menus-and-resources-menu-merging.md)。  
  
##  <a name="_core_container_application_accelerator_table_additions"></a> 容器應用程式快速鍵對應表加入  
 對容器應用程式的快速鍵對應表資源進行小幅變更為需要支援就地啟動。  第一個變更允許使用者按 Esc 鍵 \(ESC\) 取消這個就地編輯模式。  將下列項目加入至主要快速鍵對應表:  
  
|ID|Key|型別|  
|--------|---------|--------|  
|**ID\_CANCEL\_EDIT\_CNTR**|VK\_ESCAPE|**VIRTKEY**|  
  
 第二個變更是建立對應於就地啟動 \(In\-Place Activation\) 建立的新功能表資源的新的快速鍵對應表。  這個資料表具有檔案和 Windows 功能表項目的頂端 **VK\_ESCAPE** 輸入之外。  下列範例是在 MFC [容器](../top/visual-cpp-samples.md)範例的就地啟動 \(In\-Place Activation\) 建立的快速鍵對應表:  
  
|ID|Key|型別|  
|--------|---------|--------|  
|`ID_FILE_NEW`|CTRL\+N|**VIRTKEY**|  
|`ID_FILE_OPEN`|CTRL\+O|**VIRTKEY**|  
|**ID\_FILE\_SAVE**|CTRL\+S|**VIRTKEY**|  
|**ID\_FILE\_PRINT**|CTRL\+P|**VIRTKEY**|  
|**ID\_NEXT\_PANE**|VK\_F6|**VIRTKEY**|  
|**ID\_PREV\_PANE**|SHIFT\+VK\_F6|**VIRTKEY**|  
|**ID\_CANCEL\_EDIT\_CNTR**|VK\_ESCAPE|**VIRTKEY**|  
  
##  <a name="_core_string_table_additions_for_container_applications"></a> 容器應用程式的字串資料表加入  
 大部分的字串資料表的變更容器應用程式對應至 [容器功能表加入](#_core_container_menu_additions)提及的其他功能表項目。  在每個功能表項目顯示時，會提供在狀態列中顯示的文字。  例如，這個應用程式精靈所產生的字串資料表項目:  
  
|ID|String|  
|--------|------------|  
|**IDP\_OLE\_INIT\_FAILED**|OLE 初始化失敗。  請確認 OLE 程式庫的版本是否正確。|  
|**IDP\_FAILED\_TO\_CREATE**|無法建立物件。  請確認該物件已登錄在系統登錄中。|  
  
## 請參閱  
 [功能表和資源 \(OLE\)](../mfc/menus-and-resources-ole.md)   
 [功能表和資源：伺服器新增](../mfc/menus-and-resources-server-additions.md)