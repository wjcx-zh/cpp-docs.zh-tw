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
ms.openlocfilehash: 1c524d6890cd7b86bcae2c40d8c602e7b04e751b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623429"
---
# <a name="active-document-containment"></a>主動式文件內含項目

活動文檔內含專案是一種技術，可提供用來處理檔的單一框架，而不會強迫您為每一種檔案類型建立和使用多個應用程式框架。 它與基本 OLE 技術不同之處在于，OLE 會使用複合檔案中的内嵌物件，其中只有單一內容可以是作用中。 使用活動文檔內含專案時，您可以在單一框架的內容中啟用整份檔（也就是整個應用程式，包括相關聯的功能表、工具列等等）。

活動文檔內含專案技術最初是針對執行 Office 系結程式的 Microsoft Office 所開發。 不過，此技術具有足夠的彈性，可支援 Office 系結以外的活動文檔容器，並可支援 Office 和 Office 相容應用程式以外的檔案伺服器。

主控活動文檔的應用程式稱為「[活動文檔」容器](active-document-containers.md)。 這類容器的範例包括 Microsoft Office 系結器或 Microsoft Internet Explorer。

活動文檔內含專案會實作為 OLE 檔的一組延伸模組，也就是 OLE 的複合檔案技術。 延伸模組是額外的介面，可讓內嵌的就地物件代表整個檔，而不是內嵌內容的單一部分。 如同使用 OLE 檔，活動文檔內含專案會使用一個容器來提供活動文檔的顯示空間，以及提供使用者介面和操作功能給使用中檔本身的伺服器。

[活動文檔伺服器](active-document-servers.md)是一種應用程式（例如 Word、Excel 或 PowerPoint），可支援一或多個活動文檔類別，其中每個物件本身都支援允許在適當容器中啟用物件的延伸模組介面。

使用中的[檔](active-documents.md)（從 Word 或 Excel 等作用中檔案伺服器提供）基本上是完整的傳統檔，內嵌為另一個活動文檔容器中的物件。 與内嵌物件不同的是，使用中的檔可以完整控制其頁面，而應用程式的完整介面（及其所有基礎命令和工具）可供使用者編輯。

使用中的檔與標準的 OLE embedded 物件的區別是最容易瞭解的。 遵循 OLE 慣例之後，内嵌物件會顯示在擁有它的檔頁面中，而檔則是由 OLE 容器管理。 容器會儲存内嵌物件的資料與檔的其餘部分。 不過，内嵌物件的限制，是因為它們不會控制其出現的頁面。

活動文檔容器應用程式的使用者可以使用他們最愛的應用程式（假設這些應用程式已啟用作用中檔）來建立活動文檔（稱為 Office 系結器中的區段），但是使用者可以將產生的專案當做單一實體來管理，其可唯一命名、儲存、列印等等。 同樣地，網際網路瀏覽器的使用者可以將整個網路（以及本機檔案系統）視為單一檔儲存實體，而且能夠從單一位置流覽該儲存體中的檔。

## <a name="sample-programs"></a>範例程式

- [MFCBIND](../overview/visual-cpp-samples.md)範例說明使用中的檔案容器應用程式的執行。

## <a name="see-also"></a>另請參閱

[MFC COM](mfc-com.md)
