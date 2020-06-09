---
title: 主動式文件容器
ms.date: 11/19/2018
helpviewer_keywords:
- active documents [MFC], containers
- active document containers [MFC]
- containers [MFC], active document
- MFC COM, active document containment
ms.assetid: ba20183a-8b4c-440f-9031-e5fcc41d391b
ms.openlocfilehash: dc7017a205bedd716e5c87aa23ac96b257af2e16
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626026"
---
# <a name="active-document-containers"></a>主動式文件容器

活動文檔容器（例如 Microsoft Office 系結器或 Internet Explorer）可讓您在單一框架內處理不同應用程式類型的數個檔（而不是強迫您建立及使用每一種檔案類型的多個應用程式框架）。

MFC 會針對類別中的活動文檔容器提供完整支援 `COleDocObjectItem` 。 您可以使用 [MFC 應用程式精靈]，在 [MFC 應用程式精靈] 的 [**複合檔案支援**] 頁面上選取 [使用中**文檔容器**] 核取方塊，以建立活動文檔容器。 如需詳細資訊，請參閱[建立活動文檔容器應用程式](creating-an-active-document-container-application.md)。

如需活動文檔容器的詳細資訊，請參閱：

- [容器需求](#container_requirements)

- [檔網站物件](#document_site_objects)

- [查看網站物件](#view_site_objects)

- [框架物件](#frame_object)

- [說明功能表合併](help-menu-merging.md)

- [以程式設計方式列印](programmatic-printing.md)

- [命令目標](message-handling-and-command-targets.md)

## <a name="container-requirements"></a><a name="container_requirements"></a>容器需求

活動文檔容器中的使用中的檔案支援不只是介面的執行，也需要知道使用所包含物件的介面。 這同樣適用于現用檔延伸模組，其中容器也必須知道如何在使用中的檔本身上使用這些延伸模組介面。

整合活動文檔的活動文檔容器必須：

- 能夠透過介面處理物件儲存體 `IPersistStorage` ，也就是說，它必須提供 `IStorage` 實例給每個使用中的檔。

- 支援 OLE 檔的基本內嵌功能，強制 "site" 物件（每一檔或內嵌一個），其會執行 `IOleClientSite` 和 `IAdviseSink` 。

- 支援内嵌物件或活動文檔的就地啟用。 容器的網站物件必須執行 `IOleInPlaceSite` ，而且容器的框架物件必須提供 `IOleInPlaceFrame` 。

- 藉由執行來支援活動文檔的延伸模組， `IOleDocumentSite` 以提供容器與檔通訊的機制。 （選擇性）容器可以執行活動文檔介面 `IOleCommandTarget` ，並 `IContinueCallback` 挑選簡單的命令，例如列印或儲存。

Frame 物件、view 物件和 container 物件可以選擇性地執行 `IOleCommandTarget` ，以支援分派特定命令，如[命令目標](message-handling-and-command-targets.md)中所述。 View 和 container 物件也可以選擇性地執行 `IPrint` 和 `IContinueCallback` ，以支援程式設計的列印，如程式[設計的列印](programmatic-printing.md)中所述。

下圖顯示容器及其元件（左側）和作用中檔及其視圖（右側）之間的概念關聯性。 活動文檔會管理儲存體和資料，而此視圖會顯示或選擇性地列印該資料。 以粗體顯示的介面是使用中的檔案參與所需的介面;這些粗體和斜體都是選擇性的。 所有其他介面都是必要的。

![主動式文件容器介面](../mfc/media/vc37gj1.gif "主動式文件容器介面")

僅支援單一視圖的檔可以在單一實體類別上同時執行 view 和 document 元件（也就是其對應的介面）。 此外，一次只支援一個 view 的容器網站可以將檔網站和 view 網站結合成單一具體的網站類別。 不過，容器的框架物件必須保持不變，而且容器的檔元件只會包含在此處，以提供完整的架構。它不會受到活動文檔內含專案架構的影響。

## <a name="document-site-objects"></a><a name="document_site_objects"></a>檔網站物件

在活動文檔內含專案架構中，檔網站與 OLE 檔中的用戶端網站物件相同，並加入了 `IOleDocument` 介面：

```cpp
interface IOleDocumentSite : IUnknown
{
    HRESULT ActivateMe(IOleDocumentView *pViewToActivate);
}
```

檔網站在概念上是一個或多個「view site」物件的容器。 每個 view site 物件都會與檔網站所管理之檔的個別 view 物件相關聯。 如果容器僅支援每個檔網站的單一視圖，則它可以使用單一實體類別來執行檔網站和 view 網站。

## <a name="view-site-objects"></a><a name="view_site_objects"></a>查看網站物件

容器的 view site 物件會管理特定檔視圖的顯示空間。 除了支援標準 `IOleInPlaceSite` 介面，視圖網站通常也會 `IContinueCallback` 針對程式設計的列印控制項來執行。 （請注意，view 物件永遠不會查詢， `IContinueCallback` 因此它實際上可以在容器所需的任何物件上執行）。

支援多個 views 的容器必須能夠在檔網站內建立多個 view site 物件。 這會透過提供的個別啟用和停用服務來提供每個視圖 `IOleInPlaceSite` 。

## <a name="frame-object"></a><a name="frame_object"></a>Frame 物件

在大部分的情況下，容器的框架物件是在 OLE 檔中用於就地啟用的相同框架，也就是處理功能表和工具列的協調。 View 物件可透過存取此框架物件 `IOleInPlaceSite::GetWindowContext` ，這也會提供容器物件的存取權，該物件代表容器檔案（可以處理窗格層級的工具列協商和包含的物件列舉）。

活動文檔容器可以藉由新增來擴大框架 `IOleCommandTarget` 。 這可讓它接收源自作用中檔之使用者介面的命令，其方式與此介面允許容器傳送相同命令（例如，檔案**新增**、**開啟**、**另存**新檔、**列印**;**編輯 [複製**]、[**貼**上]、[**復原**] 和 [其他]）至活動文檔。 如需詳細資訊，請參閱[命令目標](message-handling-and-command-targets.md)。

## <a name="see-also"></a>另請參閱

[主動式文件內含項目](active-document-containment.md)
