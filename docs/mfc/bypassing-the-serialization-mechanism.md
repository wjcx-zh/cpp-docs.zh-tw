---
title: "略過序列化機制 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "封存物件 [C++]"
  - "封存 [C++]"
  - "封存 [C++], 序列化"
  - "略過序列化"
  - "序列化 [C++], 略過"
  - "序列化 [C++], 覆寫"
  - "序列化 [C++], 架構的角色"
ms.assetid: 48d4a279-b51c-4ba5-81cd-ed043312b582
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 略過序列化機制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如您所見，架構提供了預設的方式從檔案讀取和寫入資料。  序列化可以封存物件符合需要的大許多應用程式。  這類應用程式完全讀取檔案至記憶體，讓使用者更新檔案寫入磁碟，然後再將更新的版本。  
  
 不過，某些應用程式非常不同的方式處理資料，因此，在這些應用程式會藉由封存不是適當的。  範例包含資料庫程式，編輯大型檔案中只有部分的程式，僅寫入文件資料的程式，和撰寫共用資料檔案。  
  
 在這些情況下，您可以用不同的方式覆寫 [序列化](../Topic/CObject::Serialize.md) 函式透過 [C 檔案](../mfc/reference/cfile-class.md) 物件斡旋檔案動作而不是 [CArchive](../mfc/reference/carchive-class.md) 物件。  
  
 您可以使用 **Open**， **ReadWriteClose**，，，， `Seek` 類別會開啟檔案的 `CFile` 的成員函式，移動檔案指標 \(搜尋\) 移至檔案中的特定點，此時讀取一個資料錄 \(指定的位元組數\)，讓使用者更新資料錄，然後再搜尋到相同的點和寫入該記錄至檔案。  架構會開啟檔案，因此，您可以使用類別 `CArchive` 的 `GetFile` 成員函式取得指標到 `CFile` 物件。  對於較複雜而有彈性，可以覆寫類別 `CWinApp`的 [OnOpenDocument](../Topic/CDocument::OnOpenDocument.md) 和 [OnSaveDocument](../Topic/CDocument::OnSaveDocument.md) 成員函式。  如需詳細資訊，請參閱 *MFC 參考* 中的 [CFile](../mfc/reference/cfile-class.md) 類別  
  
 在這個案例中，您的 `Serialize` 覆寫不執行任何動作，，除非，例如，要將其讀取和寫入檔案標頭保持最新，在文件關閉時。  
  
## 請參閱  
 [使用文件](../mfc/using-documents.md)