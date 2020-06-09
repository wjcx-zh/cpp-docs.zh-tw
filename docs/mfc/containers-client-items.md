---
title: 容器：用戶端項目
ms.date: 11/04/2016
helpviewer_keywords:
- OLE containers [MFC], client items
- client items and OLE containers
ms.assetid: 231528b5-0744-4f83-8897-083bf55ed087
ms.openlocfilehash: ad347c78fb6aa7af94b306a3edb538b9f740c305
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619010"
---
# <a name="containers-client-items"></a>容器：用戶端項目

本文說明哪些用戶端項目以及應用程式應該從哪些類別衍生其用戶端項目。

用戶端項目是屬於 OLE 容器應用程式的文件中所包含或參考的另一個應用程式的資料項目。 其資料包含在文件中的用戶端項目乃為內嵌；會連結至其資料是儲存在容器文件所參考的其他位置的項目。

OLE 應用程式中的檔類別衍生自類別[COleDocument](reference/coledocument-class.md) ，而不是從 `CDocument` 。 `COleDocument`類別繼承自 `CDocument` 使用 MFC 應用程式所依據的檔/視圖架構所需的所有功能。 `COleDocument` 也會定義將文件當做 `CDocItem` 物件集合的介面。 會提供數個 `COleDocument` 成員函式，用於加入、擷取和刪除該集合的項目。

每個容器應用程式應該從 `COleClientItem` 至少衍生一個類別。 這個類別的物件表示在這個 OLE 文件中內嵌或連結的項目。 除非從文件中刪除，否則這些物件會一直存在於包含這些物件的文件中。

`CDocItem`是和的基類 `COleClientItem` `COleServerItem` 。 分別從這兩個衍生的類別物件會做為 OLE 項目以及用戶端和伺服器應用程式之間的媒介。 每次新的 OLE 項目加入至文件，MFC 架構就會將用戶端應用程式的 `COleClientItem` 衍生類別的新物件，加入到 `CDocItem` 物件的文件集合中。

## <a name="see-also"></a>另請參閱

[容器](containers.md)<br/>
[容器：複合檔案](containers-compound-files.md)<br/>
[容器：使用者介面問題](containers-user-interface-issues.md)<br/>
[容器：進階功能](containers-advanced-features.md)<br/>
[COleClientItem 類別](reference/coleclientitem-class.md)<br/>
[COleServerItem 類別](reference/coleserveritem-class.md)
