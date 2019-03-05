---
title: 功能表和資源 (OLE)
ms.date: 11/04/2016
helpviewer_keywords:
- OLE visual editing servers [MFC]
- status bars [MFC], OLE document applications
- visual editing [MFC], application menus and resources
- string tables [MFC], visual editing applications
- OLE containers [MFC], menus and resources
- OLE applications [MFC], menus and resources
- OLE server applications [MFC], menus and resources
- toolbars [MFC], OLE document applications
- string editing [MFC], visual editing applications
- server applications [MFC], OLE menus and resources
- applications [OLE], menus and resources
- menus [MFC], OLE document applications
- in-place activation [MFC], OLE menus and resources
- containers [MFC], OLE container applications
- OLE menus and resources [MFC]
ms.assetid: 52bfa086-7d3d-466f-94c7-c7061f3bdb3a
ms.openlocfilehash: 4e8f8c7fa8e24349a741b99822f13d5473373e17
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57268521"
---
# <a name="menus-and-resources-ole"></a>功能表和資源 (OLE)

此群組的文章說明如何使用功能表和 MFC OLE 文件應用程式中的資源。

OLE 視覺化編輯置於其他需求的功能表，然後由 OLE 文件的應用程式，因為有幾個模式的這兩個容器中的其他資源可以啟動伺服器 （元件） 應用程式，並使用。 例如，全伺服應用程式可以執行上述任何三個模式：

- 獨立項目。

- 在編輯內容中的項目容器的位置。

- 「 開啟 」，以便進行編輯內容以外的項目，其容器，通常在不同的視窗。

這需要三個個別的功能表配置，一個用於應用程式的每個可能的模式。 快速鍵對應表也會需要為每個新的模式。 容器應用程式可能會或可能不支援就地啟用;若是如此，它會需要新的功能表結構和相關聯的快速鍵對應表。

在就地啟用要求的容器和伺服器應用程式必須交涉功能表、 工具列和狀態列 列的空間。 記住，所有資源必須與這個都設計。 發行項[功能表和資源：功能表合併](../mfc/menus-and-resources-menu-merging.md)涵蓋此主題的詳細資料。

由於這些問題，使用應用程式精靈建立 OLE 文件應用程式可以有最多四個不同的功能表和快速鍵對應表資源。 這些用於原因如下：

|資源名稱|使用|
|-------------------|---------|
|IDR_MAINFRAME|使用 MDI 應用程式如果沒有檔案開啟，或在 SDI 應用程式不論開啟的檔案。 這是在非 OLE 應用程式中使用的標準功能表。|
|IDR_\<project>TYPE|如果是開啟的檔案，請使用 MDI 應用程式中。 執行獨立應用程式時使用。 這是在非 OLE 應用程式中使用的標準功能表。|
|IDR_\<project>TYPE_SRVR_IP|當物件開啟時，請使用伺服器或容器。|
|IDR_\<project>TYPE_SRVR_EMB|如果不使用就地啟用開啟物件，使用的伺服器應用程式。|

每個這些資源名稱代表功能表和通常快速鍵對應表。 不使用應用程式精靈 建立 MFC 應用程式中應以類似的機制。

下列文章會討論容器、 伺服器和功能表合併實作就地啟用所需的相關主題：

- [功能表和資源：容器新增](../mfc/menus-and-resources-container-additions.md)

- [功能表和資源：伺服器新增項目](../mfc/menus-and-resources-server-additions.md)

- [功能表和資源：合併的功能表](../mfc/menus-and-resources-menu-merging.md)

## <a name="see-also"></a>另請參閱

[OLE](../mfc/ole-in-mfc.md)
