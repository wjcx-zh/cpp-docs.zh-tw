---
title: 主動式文件容器
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], containers
- active document containers [MFC]
- containers [MFC], active document
- MFC COM, active document containment
ms.assetid: ba20183a-8b4c-440f-9031-e5fcc41d391b
ms.openlocfilehash: ec2e4d11e00040cf0b94957db8466d127e0b5420
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50510834"
---
# <a name="active-document-containers"></a>主動式文件容器

主動式文件的容器，例如 Microsoft Office Binder 或 Internet Explorer 中，可讓您能夠使用不同的應用程式類型 （而不是強迫您建立及使用多個應用程式的框架，每個在單一範圍內的多份文件文件類型）。

MFC 中的主動式文件容器提供完整支援`COleDocObjectItem`類別。 您可以使用 MFC 應用程式精靈建立主動式文件容器可以選取**主動式文件容器** 核取方塊**複合文件支援**MFC 應用程式精靈頁面。 如需詳細資訊，請參閱 <<c0> [ 建立作用中的文件容器應用程式](../mfc/creating-an-active-document-container-application.md)。

如需主動式文件容器的詳細資訊，請參閱：

- [容器需求](#container_requirements)

- [文件站台物件](#document_site_objects)

- [檢視站台物件](#view_site_objects)

- [框架物件](#frame_object)

- [說明功能表合併](../mfc/help-menu-merging.md)

- [以程式設計方式列印](../mfc/programmatic-printing.md)

- [命令目標](../mfc/message-handling-and-command-targets.md)

##  <a name="container_requirements"></a> 容器需求

在使用中文件容器中的主動式文件支援表示只是多個介面實作： 您也必須使用包含物件之介面的知識。 這同樣適用於使用中文件副檔名，容器也必須知道如何使用這些延伸模組介面上的作用中的文件本身的位置。

整合的主動式文件的使用中文件容器必須：

- 能夠處理透過物件儲存體`IPersistStorage`介面，也就是它必須提供`IStorage`每個使用中文件的執行個體。

- 支援 OLE 文件，需要 [站台] 物件 （一個針對每個文件或內嵌） 的基礎內嵌功能實作`IOleClientSite`和`IAdviseSink`。

- 支援就地啟用的內嵌的物件或作用中的文件。 容器的站台物件必須實作`IOleInPlaceSite`而且必須提供容器的框架物件`IOleInPlaceFrame`。

- 藉由實作支援主動式文件的延伸模組`IOleDocumentSite`提供與文件容器的機制。 （選擇性） 容器可以實作主動式文件介面`IOleCommandTarget`和`IContinueCallback`挑選簡單的命令，例如列印或儲存。

框架物件、 檢視物件和容器物件可以選擇性地實作`IOleCommandTarget`中所述，支援特定的命令，將分派[命令目標](../mfc/message-handling-and-command-targets.md)。 檢視和容器物件可以選擇性地實作`IPrint`並`IContinueCallback`，以支援以程式設計方式列印，如所述[以程式設計方式列印](../mfc/programmatic-printing.md)。

下圖顯示容器和其元件 （左側），並使用中文件和自己的檢視 （右邊） 之間的概念的關聯性。 主動式文件管理儲存體和資料，並檢視顯示，或選擇性地列印該資料。 以粗體顯示的介面是所需的主動式文件參與;這些粗體和斜體是選擇性的。 需要的其他所有介面都。

![主動式文件容器介面](../mfc/media/vc37gj1.gif "vc37gj1")

支援單一檢視的文件可以在單一的具象類別上實作檢視 」 和 「 文件的元件 （也就是其對應的介面）。 此外，只支援一個檢視，一次的容器站台可以結合是文件及檢視網站的單一實體站台的類別。 容器的框架物件，不過，必須有所區別，以及容器的文件元件只是這裡包含提供完整的架構;它不會受到使用中文件內含項目結構。

##  <a name="document_site_objects"></a> 文件站台物件

在使用中文件內含項目架構中，文件網站等同於用戶端站台物件中 OLE 文件加上`IOleDocument`介面：

```cpp
interface IOleDocumentSite : IUnknown
{
    HRESULT ActivateMe(IOleDocumentView *pViewToActivate);
}
```

文件站台就概念而言是一或多個 「 檢視站台 」 物件的容器。 每個檢視站台物件是由文件網站的文件的個別檢視物件與相關聯。 如果容器僅支援每個文件網站的單一檢視，然後就可以實作文件網站，檢視站台使用單一的具象類別。

##  <a name="view_site_objects"></a> 檢視站台物件

容器的檢視站台物件會管理文件的特定檢視的顯示空間。 除了支援標準`IOleInPlaceSite`介面，檢視站台也通常會實作`IContinueCallback`以程式設計方式列印控制項。 (請注意，永遠不會查詢檢視物件`IContinueCallback`讓它可以實際實作上的任何物件的容器需要。)

支援多個檢視的容器必須能夠建立多個檢視的文件網站內的站台物件。 如此可提供每個檢視個別啟用和停用的服務提供透過`IOleInPlaceSite`。

##  <a name="frame_object"></a> 框架物件

容器的框架物件是，大部分的情況下，也就是用於就地啟動 OLE 文件中，同一個框架，另一個則會處理功能表和工具列的交涉。 檢視物件可存取此框架物件，可透過`IOleInPlaceSite::GetWindowContext`，這也會提供容器物件，代表容器文件 （它可以處理層級 窗格的工具列交涉和所選的物件的列舉型別） 的存取權。

主動式文件容器可以藉由新增擴充框架`IOleCommandTarget`。 這可讓它能夠接收命令，在使用中文件的使用者介面中都是來自相同的方式，這個介面可以讓容器來傳送相同的命令 (例如**開新檔案**，**開啟**， **另存**，**列印**;**編輯複本**，**貼上**，**復原**，等等) 到作用中的文件。 如需詳細資訊，請參閱 <<c0> [ 命令目標](../mfc/message-handling-and-command-targets.md)。

## <a name="see-also"></a>另請參閱

[主動式文件內含項目](../mfc/active-document-containment.md)

