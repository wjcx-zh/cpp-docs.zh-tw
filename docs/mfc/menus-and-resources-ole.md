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
ms.openlocfilehash: e705f28476df7b594f9648aee8317759211c66c9
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626203"
---
# <a name="menus-and-resources-ole"></a>功能表和資源 (OLE)

這一組文章說明在 MFC OLE 檔應用程式中使用功能表和資源的方式。

OLE 視覺編輯會將額外的需求放在功能表上，以及 OLE 檔應用程式所提供的其他資源，因為有許多模式可以啟動和使用容器和伺服器（元件）應用程式。 例如，完整伺服器應用程式可以在下列三種模式中執行：

- 獨立。

- 就地，用於編輯容器內容中的專案。

- 開啟，以編輯其容器內容外部的專案，通常會在個別的視窗中。

這需要三個不同的功能表配置，每個可能的應用程式模式都有一個版面配置。 每個新模式也需要快速鍵對應表。 容器應用程式不一定會支援就地啟用;如果有，則需要新的功能表結構和相關聯的快速鍵對應表。

就地啟用需要容器和伺服器應用程式必須與功能表、工具列和狀態列空間進行協調。 所有資源都必須牢記在心。 文章[功能表和資源：功能表合併](menus-and-resources-menu-merging.md)會詳細討論此主題。

由於這些問題，使用應用程式精靈所建立的 OLE 檔應用程式最多可以有四個不同的功能表和快速鍵對應表資源。 基於下列原因，會使用這些：

|資源名稱|使用|
|-------------------|---------|
|IDR_MAINFRAME|在 MDI 應用程式中使用（如果未開啟任何檔案，或在 SDI 應用程式中，不論開啟的檔案為何）。 這是非 OLE 應用程式中所使用的標準功能表。|
|IDR_ \<project> 類型|如果檔案已開啟，則在 MDI 應用程式中使用。 在應用程式獨立執行時使用。 這是非 OLE 應用程式中所使用的標準功能表。|
|IDR_ \<project> TYPE_SRVR_IP|當物件已就地開啟時，由伺服器或容器使用。|
|IDR_ \<project> TYPE_SRVR_EMB|由伺服器應用程式使用，如果未使用就地啟用就開啟物件。|

這些資源名稱中的每一個都代表一個功能表，通常是一個快速鍵對應表。 不是使用應用程式精靈所建立的 MFC 應用程式中，應該使用類似的配置。

下列文章討論與容器、伺服器，以及執行就地啟用所需的功能表合併相關的主題：

- [功能表和資源：容器新增](menus-and-resources-container-additions.md)

- [功能表和資源：伺服器新增](menus-and-resources-server-additions.md)

- [功能表和資源：功能表合併](menus-and-resources-menu-merging.md)

## <a name="see-also"></a>另請參閱

[OLE](ole-in-mfc.md)
