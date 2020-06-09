---
title: 主動式文件伺服程式
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], servers
- servers [MFC], active document
- active document servers [MFC]
ms.assetid: 131fec1e-02a0-4305-a7ab-903b911232a7
ms.openlocfilehash: 58f2a63a8c640e6ae31640af680894763603e1d0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619145"
---
# <a name="active-document-servers"></a>主動式文件伺服程式

裝載其他應用程式類型文件的主動式文件伺服程式 (例如 Word、Excel、PowerPoint) 稱為主動式文件。 和 OLE 內嵌物件 (只在其他文件的頁面中顯示) 不同的是，主動式文件提供完整的介面以及建立這些物件之伺服器應用程式的完整原生功能。 使用者可以使用他們最喜愛的應用程式完整功能 (如果支援主動式文件) 來建立文件，也可以將產生的專案視為單一實體。

主動式文件可能擁有多個頁面，而且隨時可以就地啟動。 活動文檔會控制使用者**介面的一部分**，並使用容器的 [檔案] 和 [說明]**功能表來合併**其功能表。 它們會佔用容器的整個編輯區域，並控制印表機頁面 (框線、頁尾等等) 的檢視和版面配置。

MFC 透過文件/檢視介面、命令分派對應、列印、功能表管理，以及登錄管理來實作主動式文件伺服程式。 特定程式設計需求將在[活動文檔](active-documents.md)中討論。

MFC 支援具有[CDocObjectServer](reference/cdocobjectserver-class.md)類別的活動文檔，衍生自[CCmdTarget](reference/ccmdtarget-class.md)，而[CDocObjectServerItem](reference/cdocobjectserveritem-class.md)則衍生自[COleServerItem](reference/coleserveritem-class.md)。 MFC 支援具有[COleDocObjectItem](reference/coledocobjectitem-class.md)類別（衍生自[COleClientItem](reference/coleclientitem-class.md)）的活動文檔容器。

`CDocObjectServer` 會對應主動式文件介面，以及初始化並啟動主動式文件。 MFC 也提供巨集來處理主動式文件上的命令路由。 若要在您的應用程式中使用主動式文件，請在您的 StdAfx.h 檔案中包含 AfxDocOb.h。

一般 MFC 伺服器會連結自己的 `COleServerItem` 衍生類別。 如果您選取 [**迷你伺服器**] 或 [**完整伺服器**] 核取方塊，為您的應用程式伺服器提供複合檔案支援，則 MFC 應用程式精靈會為您產生此類別。 如果您同時選取 [**活動文檔伺服器**] 核取方塊，則 MFC 應用程式精靈會改為產生衍生自的類別 `CDocObjectServerItem` 。

`COleDocObjectItem` 類別允許讓 OLE 容器變成主動式文件容器。 您可以使用 [MFC 應用程式精靈] 建立活動文檔容器，方法是選取 [MFC 應用程式] [複合檔案支援] 頁面中的 [使用中**文檔容器**] 核取方塊。 如需詳細資訊，請參閱[建立活動文檔容器應用程式](creating-an-active-document-container-application.md)。

## <a name="see-also"></a>另請參閱

[主動式文件內含項目](active-document-containment.md)
