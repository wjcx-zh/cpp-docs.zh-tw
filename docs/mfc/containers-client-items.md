---
title: 容器： 用戶端項目 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE containers [MFC], client items
- client items and OLE containers
ms.assetid: 231528b5-0744-4f83-8897-083bf55ed087
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 14979f1c5f11e9a229c408e33e7c17d8776a54a5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="containers-client-items"></a>容器：用戶端項目
本文說明哪些用戶端項目以及應用程式應該從哪些類別衍生其用戶端項目。  
  
 用戶端項目是屬於 OLE 容器應用程式的文件中所包含或參考的另一個應用程式的資料項目。 其資料包含在文件中的用戶端項目乃為內嵌；會連結至其資料是儲存在容器文件所參考的其他位置的項目。  
  
 OLE 應用程式中的文件類別衍生自類別[COleDocument](../mfc/reference/coledocument-class.md)而不是從**CDocument**。 `COleDocument`類別繼承自**CDocument**使用 MFC 應用程式為基礎的文件/檢視架構必要的所有功能。 `COleDocument` 也會定義將文件當做 `CDocItem` 物件集合的介面。 會提供數個 `COleDocument` 成員函式，用於加入、擷取和刪除該集合的項目。  
  
 每個容器應用程式應該從 `COleClientItem` 至少衍生一個類別。 這個類別的物件表示在這個 OLE 文件中內嵌或連結的項目。 除非從文件中刪除，否則這些物件會一直存在於包含這些物件的文件中。  
  
 `CDocItem` 是基底類別`COleClientItem`和`COleServerItem`。 分別從這兩個衍生的類別物件會做為 OLE 項目以及用戶端和伺服器應用程式之間的媒介。 每次新的 OLE 項目加入至文件，MFC 架構就會將用戶端應用程式的 `COleClientItem` 衍生類別的新物件，加入到 `CDocItem` 物件的文件集合中。  
  
## <a name="see-also"></a>另請參閱  
 [容器](../mfc/containers.md)   
 [容器： 複合檔案](../mfc/containers-compound-files.md)   
 [容器： 使用者介面問題](../mfc/containers-user-interface-issues.md)   
 [容器： 進階的功能](../mfc/containers-advanced-features.md)   
 [COleClientItem 類別](../mfc/reference/coleclientitem-class.md)   
 [COleServerItem 類別](../mfc/reference/coleserveritem-class.md)
