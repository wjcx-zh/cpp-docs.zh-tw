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
ms.openlocfilehash: 149af83bd53b7a97fd264bd6b18701fc9f64ea1f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364762"
---
# <a name="menus-and-resources-menu-merging"></a>功能表和資源：功能表合併

本文詳細介紹了 OLE 文件應用程式正確處理視覺編輯和就地啟動所需的步驟。 就地啟動對容器和伺服器(元件)應用程式都構成挑戰。 使用者保留在同一幀視窗中(在容器文檔的上下文中),但實際上正在運行另一個應用程式(伺服器)。 這需要容器和伺服器應用程式的資源之間的協調。

本文涵蓋的主題包括:

- [選單佈局](#_core_menu_layouts)

- [工具列與狀態列](#_core_toolbars_and_status_bars)

## <a name="menu-layouts"></a><a name="_core_menu_layouts"></a>選單佈局

第一步是協調功能表佈局。 容器應用程式應創建一個新功能表,僅在嵌入專案就地啟動時使用。 至少,此功能表應按列出的順序包含以下內容:

1. 檔案選單與打開檔時使用的文件功能表相同。 (通常不會在下一個項之前放置其他功能表項。

1. 兩個連續分隔符。

1. 視窗功能表與打開檔時使用的視窗功能表相同(僅當 MDI 應用程式中的容器應用程式時)。 某些應用程式可能具有屬於此組中的其他功能表(如"選項"選單),當嵌入項啟動到位時,該功能表將保留在菜單上。

    > [!NOTE]
    >  可能還有其他影響容器文檔視圖的功能表,如"縮放"。 這些容器功能表出現在此功能表資源中的兩個分隔符之間。

伺服器(元件)應用程式還應創建一個新功能表,專門用於就地啟動。 它應類似於打開檔時使用的功能表,但沒有功能表項,如操作伺服器文檔而不是資料的檔和視窗。 通常,此選單包括以下內容:

1. 編輯選單與打開檔時使用的功能表相同。

1. 分隔符號。

1. 物件編輯功能表,如"塗鴉"範例應用程式中的"筆"功能表。

1. 分隔符號。

1. 幫助功能表。

例如,查看容器和伺服器的一些範例就地功能表的佈局。 已刪除每個功能表項的詳細資訊,以使示例更清晰。 容器的就地選單具有以下條目:

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

連續分隔符指示伺服器功能表的第一部分應轉到何處。 現在查看伺服器的就地選單:

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

此處的分隔符指示第二組容器功能表項應轉到何處。 當此伺服器中的物件在此容器內就地啟動時,生成的功能表結構如下所示:

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

如您所見,分隔符已替換為每個應用程式功能表的不同組。

與就地功能表關聯的加速器表也應由伺服器應用程式提供。 容器將將它們合併到自己的加速器表中。

當嵌入的專案就地啟動時,框架將載入就地選單。 然後,它要求伺服器應用程式提供其功能表進行就地啟動,並將其插入分離器的位置。 這是功能表的組合方式。 從容器獲取用於在檔和視窗放置上操作的功能表,並從伺服器獲取用於對專案操作的菜單。

## <a name="toolbars-and-status-bars"></a><a name="_core_toolbars_and_status_bars"></a>工具列與狀態列

伺服器應用程式應創建新工具列,並將其位圖存儲在單獨的檔中。 應用程式精靈生成的應用程式將此位圖儲存在名為 ITOOLBAR 的檔案中。Bmp。 當伺服器的專案就位啟動時,新工具列將替換容器應用程式的工具列,並且應該包含與普通工具列相同的專案,但刪除表示「檔和視窗」功能表上項的圖示。

此工具列載入到派生`COleIPFrameWnd`類中,由應用程式精靈為您創建。 狀態列由容器應用程式處理。 有關就地幀視窗實現的詳細資訊,請參閱[伺服器:實現伺服器](../mfc/servers-implementing-a-server.md)。

## <a name="see-also"></a>另請參閱

[功能表和資源 (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[啟用](../mfc/activation-cpp.md)<br/>
[伺服器](../mfc/servers.md)<br/>
[容器](../mfc/containers.md)
