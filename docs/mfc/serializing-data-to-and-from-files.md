---
title: "將資料序列化至檔案以及從檔案序列化資料 | Microsoft Docs"
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
  - "資料 [MFC]"
  - "資料 [MFC], 序列化"
  - "還原序列化 [C++]"
  - "文件資料 [C++]"
  - "文件 [C++], 儲存"
  - "文件 [C++], 序列化"
  - "儲存文件"
  - "序列化 [C++], 資料的角色"
  - "序列化 [C++], 文件的角色"
ms.assetid: b42a0c68-4bc4-4012-9938-5433a26d2c24
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 將資料序列化至檔案以及從檔案序列化資料
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

繼續基本概念是物件應該可以將其目前狀態，表示由其成員變數的值，為持續性儲存體。  之後，物件可以讀取或「將重新建立，而從持續性儲存體的物件狀態。  這裡的主要是物件讀取和寫入其狀態來執行。  因此，才能成為的類別可以保存的，它必須實作基本的序列化作業。  
  
 架構提供預設實作會將文件寫入磁碟檔案以回應儲存和儲存，命令在檔案功能表以及從磁碟檔案的文件以回應開啟命令。  很少工作，您可以實作資料的能力將檔案寫入和讀取資料。  您必須進行的重要事件是覆寫您的文件類別的 [序列化](../Topic/CObject::Serialize.md) 成員函式。  
  
 MFC 應用程式精靈在文件類別將會為您建立 **CDocument**`Serialize` 成員函式的基本架構覆寫。  在您實作應用程式的成員變數之後，您可以將資料傳送至「封存物件已經連接到檔案的程式碼填入您的 `Serialize` 覆寫。  [CArchive](../mfc/reference/carchive-class.md) 物件類似於 C\+\+ iostream 程式庫的 `cin` 和 `cout` 輸入\/輸出物件。  不過， `CArchive` 寫入和讀取二進位格式，而不是。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [序列化](../mfc/serialization-in-mfc.md)  
  
-   [在還原序列化的文件的作用](#_core_the_document.92.s_role_in_serialization)  
  
-   [在序列化資料的作用](#_core_the_data.92.s_role_in_serialization)  
  
-   [略過序列化機制](../mfc/bypassing-the-serialization-mechanism.md)  
  
##  <a name="_core_the_document.92.s_role_in_serialization"></a> 在還原序列化的文件的作用  
 架構會自動回應檔案功能表上的開啟，儲存和儲存命令時，會呼叫文件的 `Serialize` 成員函式它是否實作。  `ID_FILE_OPEN` 命令，例如，在應用程式物件的處理函式。  在這個過程中，使用者會看到並回應檔案開啟對話方塊，而這個框架取得使用者選取的檔名。  架構建立載入資料的 `CArchive` 物件設定為文件並將封存至 `Serialize`。  架構已開啟檔案。  在文件的 `Serialize` 成員函式的程式碼會將項目寫入資料，重建資料物件視需要。  如需序列化的詳細資訊，請參閱本文件的 [序列化](../mfc/serialization-in-mfc.md)。  
  
##  <a name="_core_the_data.92.s_role_in_serialization"></a> 在序列化資料的作用  
 一般而言，類別型別的資料應該可以序列化。  也就是說，當您將傳遞至封存物件時，物件應該會如何將自己封存寫入和讀取自己從封存。  MFC 提供這類使類別支援序列化。  當您設計一個類別定義資料型別，而您想要序列化該型別資料，請為序列化設計。  
  
## 請參閱  
 [使用文件](../mfc/using-documents.md)