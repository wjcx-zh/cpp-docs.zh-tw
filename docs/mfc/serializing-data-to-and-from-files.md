---
title: 將資料序列化至檔案以及從檔案序列化資料
ms.date: 11/04/2016
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
ms.openlocfilehash: af3cde9445ae4b128e7e54a5f154db01b2eecd3b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279259"
---
# <a name="serializing-data-to-and-from-files"></a>將資料序列化至檔案以及從檔案序列化資料

持續性的基本概念是物件應該能夠撰寫其目前的狀態，由其成員變數，永續性儲存體的值。 稍後，您可以重新讀取，或 「 還原序列化 」 物件的狀態，從永續性儲存體建立物件。 此處的重點是物件本身會負責讀取和寫入自己的狀態。 因此，對於持續性的類別，就必須實作基本的序列化作業。

「 架構 」 提供的預設實作，將文件儲存至磁碟檔案，以回應儲存和另存新檔命令在 [檔案] 功能表上以及從 [開啟] 命令的回應中的磁碟檔案載入文件。 很少的功夫，您可以實作寫入和讀取其資料與檔案的文件的能力。 您必須執行的重點是覆寫[Serialize](../mfc/reference/cobject-class.md#serialize)文件類別中的成員函式。

MFC 應用程式精靈會的骨架的覆寫`CDocument`成員函式`Serialize`它會為您建立的文件類別中。 在實作您的應用程式成員變數之後，您可以填寫您`Serialize`覆寫以將資料傳送至 「 封存物件 」 連接到檔案的程式碼。 A [CArchive](../mfc/reference/carchive-class.md)物件是類似**cin**並**cout**輸入/輸出來自 c + + iostream 程式庫的物件。 不過，`CArchive`寫入和讀取二進位格式，而不是格式化文字。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [序列化](../mfc/serialization-in-mfc.md)

- [在序列化中的文件的角色](#_core_the_document.92.s_role_in_serialization)

- [在序列化中的資料的角色](#_core_the_data.92.s_role_in_serialization)

- [略過序列化機制](../mfc/bypassing-the-serialization-mechanism.md)

##  <a name="_core_the_document.92.s_role_in_serialization"></a> 在序列化中的文件的角色

架構 [檔案] 功能表開啟後的回應會自動儲存和將儲存為命令，藉由呼叫文件的`Serialize`如果實作的成員函式。 ID_FILE_OPEN 命令，例如，呼叫處理常式函式應用程式物件中。 在此過程中，使用者會看到並回應 [開啟舊檔] 對話方塊中，架構會取得使用者選擇的檔案名稱。 此架構會建立`CArchive`物件設定的資料載入文件，並將傳遞至封存`Serialize`。 架構已開啟檔案。 您的文件中的程式碼`Serialize`成員函式會讀取透過封存，並視需要重新建構資料物件中的資料。 如需序列化的詳細資訊，請參閱文章[序列化](../mfc/serialization-in-mfc.md)。

##  <a name="_core_the_data.92.s_role_in_serialization"></a> 在序列化中的資料的角色

一般情況下，類別型別資料應該能夠序列化本身。 也就是當您將物件傳遞至封存時，此物件應該知道，如何將本身寫入封存，以及如何從封存讀取本身。 MFC 提供讓類別以這種方式可序列化的支援。 如果您設計的類別來定義資料類型，而且您想要序列化該類型的資料，來設計進行序列化。

## <a name="see-also"></a>另請參閱

[使用文件](../mfc/using-documents.md)
