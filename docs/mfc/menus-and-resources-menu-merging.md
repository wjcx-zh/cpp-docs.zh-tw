---
title: "功能表和資源：功能表合併 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "協調功能表配置"
  - "功能表 [C++], OLE 文件應用程式"
  - "合併工具列和狀態列"
  - "OLE 容器, 功能表和資源"
  - "狀態列, OLE 文件應用程式"
  - "工具列 [C++], OLE 文件應用程式"
  - "視覺化編輯, 應用程式功能表和資源"
ms.assetid: 80b6bb17-d830-4122-83f0-651fc112d4d1
caps.latest.revision: 9
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 功能表和資源：功能表合併
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這篇文章詳細步驟所需的 OLE 文件應用程式可以處理視覺化編輯和適當就地啟動。  就地啟用形成容器和伺服器元件 \(\) 應用程式的一個要求。  使用者在相同框架視窗保持 \(在容器文件的內容中\)，但是實際執行另一個應用程式 \(伺服器\)。  這需要在容器的資源和伺服器應用程式之間的協調。  
  
 在此文件中包含的主題:  
  
-   [功能表設定](#_core_menu_layouts)  
  
-   [工具列和狀態列](#_core_toolbars_and_status_bars)  
  
##  <a name="_core_menu_layouts"></a> 功能表設定  
 第一步是協調功能表設定。  如需詳細資訊，請參閱 [功能表程式設計考量](https://msdn.microsoft.com/en-us/library/ms647557.aspx) 中的 **Menu Creation** 部分在 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]。  
  
 只有在內嵌項目時，就地啟動容器應用程式應該建立要使用的新功能表。  在最小，此功能表應該包括，依列出的順序:  
  
1.  檔案功能表相同到使用的該檔案時是開啟的。\(其他功能表項目不會在下一個項目之前通常放置\)。  
  
2.  兩個連續的分隔符號。  
  
3.  視窗功能表相同到使用的該檔案時為開啟\(只有在 MDI 應用程式的容器應用程式\)。  某些應用程式可能有其他功能表，例如選項功能表，在這個群組中屬於，功能表，當內嵌項目時就地啟動。  
  
    > [!NOTE]
    >  可能會影響容器文件檢視的其他功能表，例如縮放。  這些容器功能表在此功能表資源出現在兩個分隔符號之間。  
  
 伺服器元件 \(\) 應用程式應該明確地建立新的功能表就地啟動的。  它應該類似於使用的功能表，當檔案開啟時，，，但是不用管理伺服器資料而不是資料的功能表項目，例如檔案和視窗。  通常，這個功能表包含下列項目:  
  
1.  編輯功能表相同到使用的該檔案時是開啟的。  
  
2.  Separator。  
  
3.  編輯功能表，例如在 Scribble 範例應用程式是一個功能表的物件。  
  
4.  Separator。  
  
5.  說明功能表。  
  
 如需範例，請參閱一些範例就地功能表設定為容器和伺服器。  移除每個功能表項目詳細資料讓範例更清楚。  容器的就地功能表具有下列項目:  
  
```  
IDR_CONTAINERTYPE_CNTR_IP MENU PRELOAD DISCARDABLE   
BEGIN  
    POPUP "&File C1"  
    MENUITEM SEPARATOR  
    POPUP "&Zoom C2"  
    MENUITEM SEPARATOR  
    POPUP "&Options C3"  
    POPUP "&Window C3"  
END  
```  
  
 連續分隔符號表示伺服器的功能表的第一個部分位置應該是。  現在請參閱伺服器的就地功能表:  
  
```  
IDR_SERVERTYPE_SRVR_IP MENU PRELOAD DISCARDABLE   
BEGIN  
    POPUP "&Edit S1"  
    MENUITEM SEPARATOR  
    POPUP "&Format S2"  
    MENUITEM SEPARATOR  
    POPUP "&Help S3"  
END  
```  
  
 此分隔符號表示容器功能表項目的第二個群組要移至。  產生的功能表結構，就會發生此伺服器的物件已啟動到位在這個容器如下所示:  
  
```  
BEGIN  
    POPUP "&File C1"  
    POPUP "&Edit S1"  
    POPUP "&Zoom C2"  
    POPUP "&Format S2"  
    POPUP "&Options C3  
    POPUP "&Window C3"  
    POPUP "&Help S3"  
END  
```  
  
 如您所見，分隔符號是每個應用程式的功能表的不同群組取代。  
  
 應該由伺服器應用程式也提供快速鍵對應表與就地功能表。  容器合併至其快速鍵對應表中。  
  
 當內嵌項目就地啟動時，架構會載入就地功能表。  然後要求其功能表的伺服器應用程式就地啟動 \(In\-Place Activation\) 並將它插入分隔符號的位置。  這是功能表的組合方式。  您從操作的容器取得功能表在檔案和視窗位置，因此，您從操作的伺服器中功能表項目。  
  
##  <a name="_core_toolbars_and_status_bars"></a> 工具列和狀態列  
 伺服器應用程式在不同的檔案中應該建立新的工具列和它的點陣圖。  應用程式精靈產生的應用程式在呼叫 ITOOLBAR.BMP 的檔案儲存點陣圖。  新的工具列取代容器應用程式的工具列，在您的伺服器項目就地啟動時，應該包含項目和您的一般工具列相同，不過，移除代表檔案和 Windows 功能表的圖示項目。  
  
 這個工具列中的 `COleIPFrameWnd`衍生類別載入，建立為您由應用程式精靈。  狀態列由容器應用程式處理。  如需就地框架視窗的實作的詳細資訊，請參閱 [伺服器:實作伺服器](../mfc/servers-implementing-a-server.md)。  
  
## 請參閱  
 [功能表和資源 \(OLE\)](../mfc/menus-and-resources-ole.md)   
 [啟用](../mfc/activation-cpp.md)   
 [伺服器](../mfc/servers.md)   
 [容器](../mfc/containers.md)