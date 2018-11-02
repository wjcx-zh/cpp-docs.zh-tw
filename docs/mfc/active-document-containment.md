---
title: 主動式文件內含項目
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- MFC, COM support
- active document containers [MFC], about active document containers
- MFC COM, active document containment
ms.assetid: b8dfa74b-75ce-47df-b75e-fc87b7f7d687
ms.openlocfilehash: 22111a8b2f7048d9f62d9e3e2f6c270fdc9bace3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612377"
---
# <a name="active-document-containment"></a>主動式文件內含項目

主動式文件內含項目是一種技術，提供單一的框架，在其中處理文件，而不是強迫您建立和使用每個文件類型的多個應用程式框架。 它不同於基本 OLE 技術，OLE 適用於內嵌的物件，只需要一小段的內容可以是作用中的複合文件中所示。 主動式文件內含項目，使用中，您可以啟用整份文件 （也就是整個應用程式，包括相關聯的功能表、 工具列和等等） 的單一框架的內容中。

主動式文件內含項目技術原先是針對實作 Office Binder 的 Microsoft Office 開發。 不過，技術是有足夠的彈性，以支援 Office Binder 以外的主動式文件容器，而且可支援文件伺服程式 Office 和 Office 相容的應用程式以外。

裝載作用中的文件之應用程式會呼叫[主動式文件容器](../mfc/active-document-containers.md)。 這類容器的範例是 Microsoft Office Binder 或 Microsoft Internet Explorer。

一組延伸模組 ole 文件的 OLE 複合文件技術被實作主動式文件內含項目。 擴充功能是允許的可內嵌在就地物件來代表整份文件，而不是單一的內嵌內容的其他介面。 如同 OLE 文件中，使用中文件內含項目會使用提供主動式文件，並提供使用者介面和操作功能的作用中的文件本身的伺服器中的顯示空間的容器。

[主動式文件伺服](../mfc/active-document-servers.md)是應用程式 （例如 Word、 Excel 或 PowerPoint） 支援一或多個作用中的文件類別，其中每個物件本身支援允許要在中啟用物件的延伸模組介面適當的容器。

[主動式文件](../mfc/active-documents.md)（例如 Word 或 Excel 的使用中文件伺服器提供） 是本質上的完整規模、 傳統文件內嵌為另一個使用中文件容器中的物件。 不同於內嵌物件，主動式文件具有完全控制其頁面中，而且完整的介面，將應用程式 （具有所有其基礎命令和工具） 是提供給使用者，以進行編輯。

主動式文件助您了解藉由區分從標準的 OLE 內嵌物件。 遵循 OLE 的慣例，內嵌的物件是內擁有它的文件頁面會顯示，可在文件由 OLE 容器。 容器會儲存文件的其餘部分的內嵌的物件的資料。 不過，內嵌的物件的限制，在於它們並不會控制它們出現的頁面。

主動式文件容器應用程式的使用者可以建立主動式文件 （稱為 Office Binder 中的各節） 使用他們最愛的應用程式 （前提是這些應用程式都支援主動式文件），但使用者可以管理做為產生的專案單一實體，可以唯一地命名、 儲存、 列印，依此類推。 同樣地，在網際網路瀏覽器的使用者可以視為整個網路，以及本機檔案系統中，瀏覽該儲存體，從單一位置中的文件的功能的單一文件儲存體實體。

## <a name="sample-programs"></a>範例程式

- [MFCBIND](../visual-cpp-samples.md)範例說明使用中文件容器應用程式的實作。

## <a name="see-also"></a>另請參閱

[MFC COM](../mfc/mfc-com.md)

