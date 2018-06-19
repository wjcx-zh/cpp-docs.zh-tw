---
title: 功能表和資源： 功能表合併 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- status bars [MFC], OLE document applications
- visual editing [MFC], application menus and resources
- coordinating menu layouts [MFC]
- OLE containers [MFC], menus and resources
- toolbars [MFC], OLE document applications
- merging toolbar and status bar [MFC]
- menus [MFC], OLE document applications
ms.assetid: 80b6bb17-d830-4122-83f0-651fc112d4d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 252619872fc53e06629a4cbded7e3640131dc94a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351962"
---
# <a name="menus-and-resources-menu-merging"></a>功能表和資源：功能表合併
這篇文章說明 OLE 文件的應用程式來處理視覺化編輯，並就地啟用正確的必要步驟。 就地啟用會帶來的挑戰容器和伺服器 （元件） 的應用程式。 使用者會保留在同一個框架視窗 （在容器文件的內容），但實際上正在執行另一個應用程式 （伺服器）。 這需要的資源的容器和伺服器應用程式之間進行協調。  
  
 本文涵蓋的主題包括：  
  
- [功能表配置](#_core_menu_layouts)  
  
- [工具列和狀態列](#_core_toolbars_and_status_bars)  
  
##  <a name="_core_menu_layouts"></a> 功能表配置  
 第一個步驟是協調功能表配置。 如需詳細資訊，請參閱**功能表建立**一節中[功能表程式設計考量](https://msdn.microsoft.com/library/ms647557.aspx)Windows SDK 中。  
  
 容器應用程式應該建立了新的功能表，以就地啟動內嵌的項目時，才使用。 最小值，這個功能表應該包含下列命令，列出的順序：  
  
1.  當檔案開啟時所用相同的檔案 功能表。 （通常是其他功能表項目會放在下一個項目之前）。  
  
2.  兩個連續的分隔符號。  
  
3.  當檔案開啟時所用相同的視窗功能表 (只有當容器應用程式在 MDI 應用程式)。 某些應用程式可能會有其他功能表、 [選項] 功能表中，例如屬於此群組，當內嵌項目就地啟動時將保留在功能表中。  
  
    > [!NOTE]
    >  可能會影響容器文件，例如縮放檢視其他功能表。 這些容器的功能表會出現在這個功能表資源中的兩個分隔符號之間。  
  
 伺服器 （元件） 應用程式也應該建立專為就地啟動新的功能表。 它應該類似檔案開啟時所使用的功能表，但沒有功能表項目，例如檔案和管理伺服器文件，而不是資料的視窗。 一般而言，這個功能表包含下列：  
  
1.  [編輯] 功能表與檔案開啟時所使用的密碼完全相同。  
  
2.  分隔符號。  
  
3.  編輯功能表，例如 Scribble 範例應用程式中的 [畫筆] 的物件。  
  
4.  分隔符號。  
  
5.  [說明] 功能表。  
  
 如需範例，看看容器和伺服器的某些範例在就地功能表的版面配置。 若要讓範例更清楚已移除的每個功能表項目詳細資料。 容器的就地功能表還包含下列項目：  
  
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
  
 連續的分隔符號指示的伺服器 功能表的第一個部分應該在哪裡。 現在，請查看伺服器的就地功能表：  
  
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
  
 此處的分隔符號指示應容器功能表項目的第二個群組。 從這部伺服器的物件這個容器內就地啟動時所產生功能表結構看起來像這樣：  
  
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
  
 如您所見，分隔符號已取代為不同的每個應用程式的功能表群組。  
  
 在就地功能表與相關聯的快速鍵對應表也應該提供伺服器應用程式。 容器會將其合併至其本身的快速鍵對應表。  
  
 當內嵌項目就地啟動時，framework 就會載入在就地功能表。 它接著會要求其功能表的伺服器應用程式就地啟用，並將它分隔符號的插入。 這是功能表合併的方式。 從容器取得功能表來操作檔案和視窗的位置，並從伺服器取得功能表項目上運作。  
  
##  <a name="_core_toolbars_and_status_bars"></a> 工具列和狀態列  
 伺服器應用程式建立新的工具列中，儲存在個別檔案中的點陣圖。 應用程式精靈產生應用程式呼叫 ITOOLBAR 之檔案中儲存此點陣圖。BMP。 您的伺服器項目就地，啟動和應包含相同的項目，和一般工具列，但是移除圖示上的檔案和視窗的功能表項目時，新的工具列會取代容器應用程式的工具列。  
  
 這個工具列已載入您`COleIPFrameWnd`-衍生的類別，為您建立應用程式精靈。 狀態列是由容器應用程式處理。 更多的就地框架視窗實作的詳細資訊，請參閱[伺服器： 實作伺服器](../mfc/servers-implementing-a-server.md)。  
  
## <a name="see-also"></a>另請參閱  
 [功能表和資源 (OLE)](../mfc/menus-and-resources-ole.md)   
 [啟用](../mfc/activation-cpp.md)   
 [伺服器](../mfc/servers.md)   
 [容器](../mfc/containers.md)

