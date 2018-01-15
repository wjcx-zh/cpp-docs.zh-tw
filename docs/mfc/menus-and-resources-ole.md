---
title: "功能表和資源 (OLE) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: efe0a5f6dae2cece571eddabc4094ebb87df175b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="menus-and-resources-ole"></a>功能表和資源 (OLE)
本系列文件說明如何使用功能表和 MFC OLE 文件應用程式中的資源。  
  
 OLE 視覺化編輯放置於其他需求 [] 功能表和 OLE 文件應用程式提供的數目的兩個容器中的模式，因為其他資源和伺服器 （元件） 應用程式可啟動及使用。 例如，全伺服應用程式可以執行任何這三個模式：  
  
-   獨立執行。  
  
-   適當地編輯容器的內容中的項目。  
  
-   「 開啟 」，以便編輯其容器，通常在個別視窗中的項目內容之外。  
  
 這需要三種不同的功能表配置，其中一個應用程式的每種模式。 快速鍵對應表也會需要為每個新的模式物件。 容器應用程式可能會或可能不支援就地啟用。若是如此，它會需要新的功能表結構和相關聯的快速鍵對應表。  
  
 就地啟用需要容器和伺服器應用程式必須談判出功能表、 工具列和狀態列 列的空間。 記住，必須與這個設計的所有資源。 發行項[功能表和資源： 功能表合併](../mfc/menus-and-resources-menu-merging.md)涵蓋了本主題中詳細資料。  
  
 由於這些問題，使用應用程式精靈建立 OLE 文件應用程式可以有最多四個不同的功能表和快速鍵對應表資源。 這些可用，原因如下：  
  
|資源名稱|使用|  
|-------------------|---------|  
|**IDR_MAINFRAME**|使用 MDI 應用程式如果沒有檔案開啟，或開啟的檔案無論 SDI 應用程式。 這是在非 OLE 應用程式中使用的標準功能表。|  
|**IDR_\<專案 > 類型**|檔案開啟時，MDI 應用程式中使用。 執行獨立應用程式時使用。 這是在非 OLE 應用程式中使用的標準功能表。|  
|**IDR_\<專案 > TYPE_SRVR_IP**|物件開啟時就地使用伺服器或容器。|  
|**IDR_\<專案 > TYPE_SRVR_EMB**|如果不使用就地啟用開啟物件，使用的伺服器應用程式。|  
  
 每個這些資源名稱代表功能表和通常快速鍵對應表。 不會使用應用程式精靈建立的 MFC 應用程式中，應該使用類似的配置。  
  
 下列文章中討論的容器、 伺服器和功能表合併實作就地啟用所需的相關主題：  
  
-   [功能表和資源：容器新增](../mfc/menus-and-resources-container-additions.md)  
  
-   [功能表和資源：伺服器新增](../mfc/menus-and-resources-server-additions.md)  
  
-   [功能表和資源：功能表合併](../mfc/menus-and-resources-menu-merging.md)  
  
## <a name="see-also"></a>請參閱  
 [OLE](../mfc/ole-in-mfc.md)

