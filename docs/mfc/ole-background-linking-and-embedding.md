---
title: OLE 背景： 連結和內嵌 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE embedded items [MFC]
- item types [MFC], defined
- item types [MFC]
- OLE [MFC], linked items
- linked items (OLE) [MFC]
- embedded objects [MFC]
- OLE items [MFC], types
ms.assetid: 11107711-eb96-4099-8f5c-7910bb3ecb75
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c5dc7a5770c98323187dbabcd8c2a7bb9eb652de
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ole-background-linking-and-embedding"></a>OLE 背景：連結與內嵌
在容器應用程式中使用 [貼上] 命令可以建立內嵌元件或內嵌項目。 內嵌項目的來源資料會儲存為包含該項目之 OLE 文件的一部分。 如此一來，文書處理器文件的文件檔案就可以包含文字，也可以包含點陣圖、圖表、公式，或任何其他類型的資料。  
  
 OLE 提供另一種方式來合併來自另一個應用程式的資料：建立連結的元件或連結的項目，或連結。 建立連結項目的步驟與建立內嵌項目類似，只是您使用的是 [貼上連結] 命令，而非 [貼上] 命令。 不同於內嵌元件，連結的元件會儲存原始資料的路徑，通常是在不同的檔案中。  
  
 例如，如果您正在使用文書處理器文件，並對某些試算表儲存格建立一個連結的項目，則連結項目的資料會儲存在原始的試算表文件中。 文書處理器文件只會包含指定可以找到項目位置的資訊，也就是說，其中包含原始試算表文件的連結。 當您按兩下儲存格時，會啟動試算表應用程式，同時會從其儲存的位置載入原始的試算表元件。  
  
 每個 OLE 項目 (不管是內嵌或連結) 都具有與其相關聯的類型，該類型取決於建立該項目的應用程式。 例如，Microsoft Paintbrush 項目是一種項目的類型，而 Microsoft Excel 項目則是另一種類型。 不過，某些應用程式可以建立一種以上的項目類型。 例如，Microsoft Excel 可以建立工作表項目、圖表項目和巨集表項目。 每一個項目可以唯一識別由系統使用的類別識別項或**CLSID**。  
  
## <a name="see-also"></a>另請參閱  
 [OLE 背景](../mfc/ole-background.md)   
 [OLE 背景： 容器和伺服器](../mfc/ole-background-containers-and-servers.md)   
 [容器： 用戶端項目](../mfc/containers-client-items.md)   
 [伺服器：伺服器項目](../mfc/servers-server-items.md)

