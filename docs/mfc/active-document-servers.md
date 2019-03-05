---
title: 主動式文件伺服程式
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], servers
- servers [MFC], active document
- active document servers [MFC]
ms.assetid: 131fec1e-02a0-4305-a7ab-903b911232a7
ms.openlocfilehash: 7050b810bb5e1f0c240222cd9b8c4922ced4238a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270770"
---
# <a name="active-document-servers"></a>主動式文件伺服程式

裝載其他應用程式類型文件的主動式文件伺服程式 (例如 Word、Excel、PowerPoint) 稱為主動式文件。 和 OLE 內嵌物件 (只在其他文件的頁面中顯示) 不同的是，主動式文件提供完整的介面以及建立這些物件之伺服器應用程式的完整原生功能。 使用者可以使用他們最喜愛的應用程式完整功能 (如果支援主動式文件) 來建立文件，也可以將產生的專案視為單一實體。

主動式文件可能擁有多個頁面，而且隨時可以就地啟動。 主動式文件控制使用者介面，結合了其功能表與部分**檔案**並**協助**容器的功能表。 它們會佔用容器的整個編輯區域，並控制印表機頁面 (框線、頁尾等等) 的檢視和版面配置。

MFC 透過文件/檢視介面、命令分派對應、列印、功能表管理，以及登錄管理來實作主動式文件伺服程式。 特定程式設計需求會討論[主動式文件](../mfc/active-documents.md)。

MFC 支援與主動式文件[CDocObjectServer](../mfc/reference/cdocobjectserver-class.md)類別，衍生自[CCmdTarget](../mfc/reference/ccmdtarget-class.md)，並[CDocObjectServerItem](../mfc/reference/cdocobjectserveritem-class.md)衍生自[COleServerItem](../mfc/reference/coleserveritem-class.md)。 MFC 支援與主動式文件容器[COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)類別，衍生自[COleClientItem](../mfc/reference/coleclientitem-class.md)。

`CDocObjectServer` 會對應主動式文件介面，以及初始化並啟動主動式文件。 MFC 也提供巨集來處理主動式文件上的命令路由。 若要在您的應用程式中使用主動式文件，請在您的 StdAfx.h 檔案中包含 AfxDocOb.h。

一般 MFC 伺服器會連結自己的 `COleServerItem` 衍生類別。 MFC 應用程式精靈會產生這個類別，如果您選取**迷你伺服**或是**全伺服器**核取方塊，來提供您的應用程式伺服器複合文件的支援。 如果您同時選取**主動式文件伺服**核取方塊，MFC 應用程式精靈會產生一個衍生自類別`CDocObjectServerItem`改。


  `COleDocObjectItem` 類別允許讓 OLE 容器變成主動式文件容器。 您可以使用 MFC 應用程式精靈建立主動式文件容器可以選取**主動式文件容器**MFC 應用程式精靈 的 複合文件支援 頁面中核取方塊。 如需詳細資訊，請參閱 <<c0> [ 建立作用中的文件容器應用程式](../mfc/creating-an-active-document-container-application.md)。

## <a name="see-also"></a>另請參閱

[主動式文件內含項目](../mfc/active-document-containment.md)
