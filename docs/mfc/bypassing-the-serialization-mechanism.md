---
title: "略過序列化機制 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- archive objects [MFC]
- bypassing serialization
- archives [MFC], serialization
- serialization [MFC], bypassing
- archives [MFC]
- serialization [MFC], role of framework
- serialization [MFC], overriding
ms.assetid: 48d4a279-b51c-4ba5-81cd-ed043312b582
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 510e6ed244fb8920c55c4b3ffedcbd0801c3e202
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="bypassing-the-serialization-mechanism"></a>略過序列化機制
如您所見，架構提供了預設的方式從檔案讀取和寫入資料。 將封存物件序列化符合許許多多應用程式的需求。 這類應用程式會將檔案完全讀入記憶體，讓使用者更新檔案，然後再將更新的版本寫入磁碟。  
  
 不過，部分應用程式是以非常不同的方式處理資料，而對這些應用程式將封存序列化就不適當。 範例包含資料庫程式、僅編輯大型檔案的一部分的程式、僅寫入純文字檔的程式以及共用資料檔的程式。  
  
 在這些情況下，您可以覆寫[序列化](../mfc/reference/cobject-class.md#serialize)函式，以不同方式來斡旋檔案動作透過[CFile](../mfc/reference/cfile-class.md)物件而非[CArchive](../mfc/reference/carchive-class.md)物件。  
  
 您可以使用**開啟**，**讀取**，**寫入**，**關閉**，和`Seek`類別成員函式`CFile`開啟檔案檔案指標移到 （搜尋） 的特定點在檔案中，此時讀取記錄 （指定的位元組數），讓使用者更新記錄，再搜尋一次相同的點和記錄備份檔案的寫入。 架構會為您開啟檔案，所以您可以使用類別 `GetFile` 的 `CArchive` 成員函式取得 `CFile` 物件的指標。 用於更精密且更有彈性，您可以覆寫[OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument)和[OnSaveDocument](../mfc/reference/cdocument-class.md#onsavedocument)類別成員函式`CWinApp`。 如需詳細資訊，請參閱類別[CFile](../mfc/reference/cfile-class.md)中*MFC 參考*。  
  
 在此案例中，您的 `Serialize` 覆寫不會執行任何動作，除非例如您在文件關閉時要其讀取和寫入檔案標頭以使其保持最新。  
  
## <a name="see-also"></a>請參閱  
 [使用文件](../mfc/using-documents.md)

