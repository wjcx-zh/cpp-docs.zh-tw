---
title: "序列化：序列化物件 | Microsoft Docs"
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
  - "物件 [C++], 序列化"
  - "序列化 [C++], 物件"
  - "序列化物件 [C++]"
ms.assetid: 1db772b1-ad55-4fcf-b133-126cca082510
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 序列化：序列化物件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

文件 [序列化: 將 Serializable 類別](../mfc/serialization-making-a-serializable-class.md) 示範如何使類別可序列化。  一旦您有可序列化類別，您可以在檔案序列化該類別物件透過 [CArchive](../mfc/reference/carchive-class.md) 物件。  本文說明:  
  
-   [什麼是 CArchive 物件](../mfc/what-is-a-carchive-object.md)  
  
-   [建立 CArchive 物件的兩種方式](../mfc/two-ways-to-create-a-carchive-object.md)  
  
-   [如何使用 CArchive \<\< 和 \>\> 運算子](../mfc/using-the-carchive-output-and-input-operators.md)。  
  
-   [透過封存儲存及載入 CObjects](../mfc/storing-and-loading-cobjects-via-an-archive.md)  
  
 您可以讓架構建置可序列化資料的封存或明確建立 `CArchive` 物件。  您可以將資料儲存在檔案中使用的 \<\< 序列化 `CArchive` 物件和 \>\> 運算子之間，或在其他情況下，藉由呼叫 `CObject` 衍生類別的 `Serialize` 函式。  
  
## 請參閱  
 [序列化](../mfc/serialization-in-mfc.md)