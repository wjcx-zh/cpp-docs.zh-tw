---
title: 主動式文件容器
ms.date: 11/19/2018
helpviewer_keywords:
- active documents [MFC], containers
- active document containers [MFC]
- containers [MFC], active document
- MFC COM, active document containment
ms.assetid: ba20183a-8b4c-440f-9031-e5fcc41d391b
ms.openlocfilehash: e2005ffed592fa1de278e0f6339d94687a20fd06
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377390"
---
# <a name="active-document-containers"></a>主動式文件容器

活動文件容器(如 Microsoft Office Binder 或 Internet Explorer)允許您在單個框架中使用多個不同應用程式類型的文檔(而不是強制為每個文件類型創建和使用多個應用程式框架)。

MFC 為類`COleDocObjectItem`中的活動文檔容器提供完全支援。 您可以通過在 MFC 應用程式精靈的**複合文件支援**頁上選擇 **「活動文檔容器**」複選框,使用 MFC 應用程式精靈建立活動文件容器。 關於詳細資訊,請參閱[建立活動文件容器應用程式](../mfc/creating-an-active-document-container-application.md)。

有關活動文件容器的詳細資訊,請參閱:

- [集裝箱要求](#container_requirements)

- [文件網站物件](#document_site_objects)

- [檢視網站物件](#view_site_objects)

- [框架物件](#frame_object)

- [說明功能表合併](../mfc/help-menu-merging.md)

- [以程式設計方式列印](../mfc/programmatic-printing.md)

- [命令目標](../mfc/message-handling-and-command-targets.md)

## <a name="container-requirements"></a><a name="container_requirements"></a>集裝箱要求

活動文檔容器中的活動文檔支援不僅僅意味著介面實現:它還需要使用包含物件的介面的知識。 這同樣適用於活動文檔擴展,其中容器還必須知道如何在活動文檔本身上使用這些擴展介面。

整合活動文件的活動文件容器必須:

- 能夠透過`IPersistStorage`介面處理物件儲存,也就是說,它必須為每個活動文件提供實`IStorage`例 。

- 支援 OLE 文件的基本嵌入功能,`IOleClientSite`需要`IAdviseSink`實現和的「網站」物件(每個文檔或嵌入一個)。

- 支援就地啟動嵌入物件或活動文檔。 容器的網站物件必須實現`IOleInPlaceSite`,容器的畫面物件必須提供`IOleInPlaceFrame`。

- 通過實現`IOleDocumentSite`為容器提供與文檔對話的機制,支援活動文檔的擴展。 或者,容器可以實現活動文檔`IOleCommandTarget`介面`IContinueCallback`,並拾取簡單的命令,如列印或保存。

框架物件、檢視物件和容器物件可以選擇實現`IOleCommandTarget`以支援某些命令的調度,如[命令目標](../mfc/message-handling-and-command-targets.md)中所述。 檢視和容器物件也可以選擇實現`IPrint`和`IContinueCallback`,以支援程式設計列印,如[程式設計列印](../mfc/programmatic-printing.md)中所述。

下圖顯示了容器及其元件(左圖)與活動文檔及其檢視(右側)之間的概念關係。 活動文件管理儲存和數據,檢視顯示或選擇性地列印該資料。 粗體介面是主動參與文檔所需的介面;這些粗體和斜體是可選的。 所有其他介面是必需的。

![主動式文件容器介面](../mfc/media/vc37gj1.gif "主動式文件容器介面")

僅支援單個檢視的文檔可以在單個具體類上實現檢視和文檔元件(即其相應的介面)。 此外,一次僅支援一個檢視的容器網站可以將文檔網站和視圖網站合併到單個具體網站類中。 但是,容器的幀物件必須保持不同,並且容器的文檔元件僅在此處包含,以便完整地反映體系結構;它不受活動文件包含體系結構的影響。

## <a name="document-site-objects"></a><a name="document_site_objects"></a>文件網站物件

在活動文件包含架構結構中,文件站台與 OLE 文件中的用戶端網站物件相同,並`IOleDocument`添加介面:

```cpp
interface IOleDocumentSite : IUnknown
{
    HRESULT ActivateMe(IOleDocumentView *pViewToActivate);
}
```

文件網站在概念上是一個或多個"查看網站"物件的容器。 每個檢視網站物件都與文檔網站管理的文檔的各個檢視對象相關聯。 如果容器僅支援每個文檔網站的單個檢視,則可以使用單個具體類實現文檔網站和視圖網站。

## <a name="view-site-objects"></a><a name="view_site_objects"></a>檢視網站物件

容器的檢視站點物件管理文檔的特定檢視的顯示空間。 除了支持標準`IOleInPlaceSite`介面外,視圖網站通常還實現了`IContinueCallback`程式設計列印控制。 (請注意,視圖物件從不查詢`IContinueCallback`,因此它實際上可以在容器所需的任何對象上實現。

支援多個檢視的容器必須能夠在文件網站內創建多個檢視網站物件。 這為每個檢視提供了通過`IOleInPlaceSite`提供的單獨啟動和停用服務。

## <a name="frame-object"></a><a name="frame_object"></a>幀物件

容器的幀物件在大多數情況下與用於在 OLE 文檔中就地啟動的幀相同,即處理功能表和工具列協商的框架。 視圖物件可通過`IOleInPlaceSite::GetWindowContext`訪問此幀物件,該物件還提供對表示容器文件的容器物件的訪問(該物件可以處理窗格級工具列協商和包含的物件枚舉)。

活動文檔容器可以`IOleCommandTarget`通過添加 來增強幀。 這允許它接收源自活動文件使用者介面的命令,就像此介面允許容器發送相同的命令(如**檔案新**、**打開**、**儲存為**、**列印**等命令) 一樣。**將複製**複製「、」**貼上**「、」**複製**檔案。 有關詳細資訊,請參閱[指令目標](../mfc/message-handling-and-command-targets.md)。

## <a name="see-also"></a>另請參閱

[主動式文件內含項目](../mfc/active-document-containment.md)
