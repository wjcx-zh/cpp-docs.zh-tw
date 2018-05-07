---
title: 從檔案序列化資料 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- documents [MFC], serialization
- documents [MFC], saving
- saving documents
- deserialization [MFC]
- serialization [MFC], role of document
- serialization [MFC], role of data
- data [MFC]
- data [MFC], serializing
- document data [MFC]
ms.assetid: b42a0c68-4bc4-4012-9938-5433a26d2c24
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ec6bfbe647045a334af9fe95cd6d1ab40625a51f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="serializing-data-to-and-from-files"></a>將資料序列化至檔案以及從檔案序列化資料
持續性的基本概念是物件應該要能夠寫入目前的狀態，由其成員變數，永續性儲存體的值。 稍後，您可以重新讀取，或 「 還原序列化時，「 物件的狀態從永續性儲存體建立物件。 此處的重點是物件本身位負責讀取及撰寫自己的狀態。 因此，對於持續性類別，就必須實作基本的序列化作業。  
  
 架構提供的預設實作，將文件儲存至磁碟儲存回應檔案與另存新檔命令檔案 功能表上，從 開啟 命令的回應中的磁碟檔案載入文件。 使用非常少量的工作，您可以實作寫入和讀取其資料，以及從檔案的文件的能力。 您必須執行的主要項目是覆寫[序列化](../mfc/reference/cobject-class.md#serialize)文件類別中的成員函式。  
  
 MFC 應用程式精靈會將架構的覆寫的**CDocument**成員函式`Serialize`中為您建立的文件類別。 您已實作應用程式的成員變數之後，您可以填寫您`Serialize`覆寫以傳送資料至 「 封存物件 」 連接到檔案的程式碼。 A [CArchive](../mfc/reference/carchive-class.md)物件是類似於`cin`和`cout`輸入/輸出來自 c + + iostream 程式庫物件。 不過，`CArchive`寫入和讀取二進位格式，未格式化的文字。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [序列化](../mfc/serialization-in-mfc.md)  
  
-   [在序列化中的文件的角色](#_core_the_document.92.s_role_in_serialization)  
  
-   [在序列化中資料的角色](#_core_the_data.92.s_role_in_serialization)  
  
-   [略過序列化機制](../mfc/bypassing-the-serialization-mechanism.md)  
  
##  <a name="_core_the_document.92.s_role_in_serialization"></a> 在序列化中的文件的角色  
 架構會自動回應 [檔案] 功能表開啟儲存，並將儲存為命令藉由呼叫文件的`Serialize`如果實作的成員函式。 `ID_FILE_OPEN`命令，例如，呼叫處理常式函式中的應用程式物件。 在此過程中，使用者將看見且回應檔案開啟對話方塊，架構取得使用者選擇的檔案名稱。 架構會建立`CArchive`物件設定的資料載入文件，並傳遞要封存`Serialize`。 架構已經開啟了檔案。 您的文件中的程式碼`Serialize`成員函式會讀取透過封存，視需要重新建構資料物件中的資料。 如需序列化的詳細資訊，請參閱文章[序列化](../mfc/serialization-in-mfc.md)。  
  
##  <a name="_core_the_data.92.s_role_in_serialization"></a> 在序列化中資料的角色  
 一般情況下，類別型別資料應該能夠序列化它本身。 也就是當您將物件傳遞至封存時，物件應該要知道如何將本身寫入封存以及如何從封存讀取本身。 MFC 提供讓類別以這種方式可序列化的支援。 如果您設計的類別來定義資料類型，而且您想要序列化該類型的資料，設計進行序列化。  
  
## <a name="see-also"></a>另請參閱  
 [使用文件](../mfc/using-documents.md)

