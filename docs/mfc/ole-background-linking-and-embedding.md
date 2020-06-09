---
title: OLE 背景：連結與內嵌
ms.date: 11/04/2016
helpviewer_keywords:
- OLE embedded items [MFC]
- item types [MFC], defined
- item types [MFC]
- OLE [MFC], linked items
- linked items (OLE) [MFC]
- embedded objects [MFC]
- OLE items [MFC], types
ms.assetid: 11107711-eb96-4099-8f5c-7910bb3ecb75
ms.openlocfilehash: 6b6032d2e772728495d4ddb1dbfaa5daf7348b60
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619878"
---
# <a name="ole-background-linking-and-embedding"></a>OLE 背景：連結與內嵌

在容器應用程式中使用 [貼上] 命令可以建立內嵌元件或內嵌項目。 內嵌項目的來源資料會儲存為包含該項目之 OLE 文件的一部分。 如此一來，文書處理器文件的文件檔案就可以包含文字，也可以包含點陣圖、圖表、公式，或任何其他類型的資料。

OLE 提供另一種方式來合併來自另一個應用程式的資料：建立連結的元件或連結的項目，或連結。 建立連結項目的步驟與建立內嵌項目類似，只是您使用的是 [貼上連結] 命令，而非 [貼上] 命令。 不同於內嵌元件，連結的元件會儲存原始資料的路徑，通常是在不同的檔案中。

例如，如果您正在使用文書處理器文件，並對某些試算表儲存格建立一個連結的項目，則連結項目的資料會儲存在原始的試算表文件中。 文書處理器文件只會包含指定可以找到項目位置的資訊，也就是說，其中包含原始試算表文件的連結。 當您按兩下儲存格時，會啟動試算表應用程式，同時會從其儲存的位置載入原始的試算表元件。

每個 OLE 項目 (不管是內嵌或連結) 都具有與其相關聯的類型，該類型取決於建立該項目的應用程式。 例如，Microsoft Paintbrush 項目是一種項目的類型，而 Microsoft Excel 項目則是另一種類型。 不過，某些應用程式可以建立一種以上的項目類型。 例如，Microsoft Excel 可以建立工作表項目、圖表項目和巨集表項目。 每個專案都可以使用類別識別碼或**CLSID**，以唯一的方式由系統識別。

## <a name="see-also"></a>另請參閱

[OLE 背景](ole-background.md)<br/>
[OLE 背景：容器和伺服器](ole-background-containers-and-servers.md)<br/>
[容器：用戶端項目](containers-client-items.md)<br/>
[伺服器：伺服器項目](servers-server-items.md)
