---
title: 功能表和資源：功能表合併
ms.date: 11/04/2016
helpviewer_keywords:
- status bars [MFC], OLE document applications
- visual editing [MFC], application menus and resources
- coordinating menu layouts [MFC]
- OLE containers [MFC], menus and resources
- toolbars [MFC], OLE document applications
- merging toolbar and status bar [MFC]
- menus [MFC], OLE document applications
ms.assetid: 80b6bb17-d830-4122-83f0-651fc112d4d1
ms.openlocfilehash: 03d27443f90634b5d787eee25acc951d24178f42
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626228"
---
# <a name="menus-and-resources-menu-merging"></a>功能表和資源：功能表合併

本文詳細說明 OLE 檔應用程式正確處理視覺化編輯和就地啟用的必要步驟。 就地啟用會對容器和伺服器（元件）應用程式造成挑戰。 使用者會保留在相同的框架視窗（在容器檔案的內容中），但實際上是執行另一個應用程式（伺服器）。 這需要協調容器和伺服器應用程式的資源。

本文涵蓋的主題包括：

- [功能表版面配置](#_core_menu_layouts)

- [工具列和狀態列](#_core_toolbars_and_status_bars)

## <a name="menu-layouts"></a><a name="_core_menu_layouts"></a>功能表版面配置

第一個步驟是協調功能表版面配置。 容器應用程式應該建立新的功能表，只有在內嵌專案已就地啟用時才會使用。 依照列出的順序，此功能表至少應包含下列內容：

1. 檔案功能表與開啟檔案時所使用的相同。 （通常不會在下一個專案之前放置任何其他功能表項目）。

1. 兩個連續的分隔符號。

1. [視窗] 功能表與開啟檔案時所使用的相同（僅限 MDI 應用程式中的容器應用程式）。 有些應用程式可能會有屬於這個群組的其他功能表，例如 [選項] 功能表，當內嵌專案就地啟用時，仍會保留在功能表上。

    > [!NOTE]
    >  可能會有其他會影響容器檔案視圖的功能表，例如 Zoom。 這些容器功能表會出現在此功能表資源的兩個分隔符號之間。

伺服器（元件）應用程式也應該特別建立新的功能表來進行就地啟用。 它應該類似于開啟檔案時使用的功能表，但不含功能表項目，例如操作伺服器檔的檔案和視窗，而不是資料。 此功能表通常包含下列各項：

1. [編輯] 功能表與開啟檔案時所使用的相同。

1. 分隔符號。

1. 物件編輯功能表，例如「塗抹」範例應用程式中的 [畫筆] 功能表。

1. 分隔符號。

1. [說明] 功能表。

如需範例，請查看容器和伺服器的一些範例就地功能表的版面配置。 已移除每個功能表項目的詳細資料，讓範例更清楚。 容器的就地功能表包含下列專案：

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

連續的分隔符號表示伺服器功能表的第一個部分應該移至何處。 現在，請查看伺服器的就地功能表：

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

此處的分隔符號指出容器功能表項目的第二個群組應移到哪個位置。 當此伺服器中的物件在此容器內啟用時，產生的功能表結構如下所示：

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

如您所見，分隔符號已取代為每個應用程式功能表的不同群組。

與就地功能表相關聯的快速鍵對應表也應該由伺服器應用程式提供。 容器會將它們併入其本身的快速鍵對應表中。

當內嵌專案就地啟用時，架構會載入就地功能表。 然後，它會向伺服器應用程式詢問其功能表以進行就地啟用，並將其插入至分隔符號所在的位置。 這就是功能表的結合方式。 您會從容器取得用於操作檔案和視窗位置的功能表，並從伺服器取得功能表，以便在專案上操作。

## <a name="toolbars-and-status-bars"></a><a name="_core_toolbars_and_status_bars"></a>工具列和狀態列

伺服器應用程式應該建立新的工具列，並將其點陣圖儲存在不同的檔案中。 應用程式精靈產生的應用程式會將這個點陣圖儲存在名為 ITOOLBAR 的檔案中。BMP. 當您的伺服器專案已就地啟動時，新的工具列會取代容器應用程式的工具列，而且應該包含與一般工具列相同的專案，但會移除代表檔案和視窗功能表上專案的圖示。

這個工具列會載入您的 `COleIPFrameWnd` 衍生類別中，由應用程式精靈為您建立。 狀態列是由容器應用程式處理。 如需就地框架視窗的執行詳細資訊，請參閱[伺服器：執行伺服器](servers-implementing-a-server.md)。

## <a name="see-also"></a>另請參閱

[功能表和資源 (OLE)](menus-and-resources-ole.md)<br/>
[啟用](activation-cpp.md)<br/>
[伺服器](servers.md)<br/>
[容器](containers.md)
