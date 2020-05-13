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
ms.openlocfilehash: 043ba019c6b5ad79db2cedb6314c9e65f14b14b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376939"
---
# <a name="serializing-data-to-and-from-files"></a>將資料序列化至檔案以及從檔案序列化資料

持久性的基本思想是,對象應該能夠將其當前狀態(由其成員變數的值指示)寫入持久存儲。 稍後,可以通過讀取或"反序列化"從持久存儲讀取物件的狀態來重新創建物件。 此處的關鍵點是物件本身負責讀取和寫入其自己的狀態。 因此,要使類持久化,它必須實現基本的序列化操作。

該框架提供了一個預設實現,用於將文件儲存到磁碟檔,以回應「檔案」選單上的「儲存和儲存為」命令,以及從磁碟檔載入文件以回應 Open 命令。 只需很少工作,即可實現文檔在檔中寫入和讀取其數據的能力。 您必須執行的主要操作是重寫文件類中的[序列化](../mfc/reference/cobject-class.md#serialize)成員函數。

MFC 應用程式精靈在其為您創建的文檔類中`CDocument`放置 成員`Serialize`函數的骨骼覆蓋。 實現應用程式的成員變數後,可以使用將數據發送到連接到檔的「存檔物件」的代碼填充`Serialize`重寫。 [CArchive](../mfc/reference/carchive-class.md)對象類似於C++ iostream 庫中的**cin**和**cout**輸入/輸出物件。 但是,`CArchive`寫入和讀取二進位格式,而不是格式化文本。

## <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [序列化](../mfc/serialization-in-mfc.md)

- [文件在序列化中的作用](#_core_the_document.92.s_role_in_serialization)

- [資料在序列化中的作用](#_core_the_data.92.s_role_in_serialization)

- [繞過序列化機制](../mfc/bypassing-the-serialization-mechanism.md)

## <a name="the-documents-role-in-serialization"></a><a name="_core_the_document.92.s_role_in_serialization"></a>文件在序列化中的作用

框架自動回應檔功能表的「打開」、「儲存」和「儲存為」命令,如果文`Serialize`檔的成員函數已實現,則調用該函數。 例如,ID_FILE_OPEN命令調用應用程式物件中的處理程式函數。 在此過程中,使用者看到並回應「檔案打開」對話框,框架獲取使用者選擇的檔名。 框架建立`CArchive`物件,用於將資料載入到文件中並將存檔傳遞到`Serialize`。 框架已打開該檔。 文`Serialize`檔成員函數中的代碼通過存檔讀取數據,根據需要重建數據物件。 有關序列化的詳細資訊,請參閱文章[序列化](../mfc/serialization-in-mfc.md)。

## <a name="the-datas-role-in-serialization"></a><a name="_core_the_data.92.s_role_in_serialization"></a>資料在序列化中的作用

通常,類類型數據應該能夠序列化自身。 也就是說,當您將對象傳遞到存檔時,該物件應知道如何將自己寫入存檔以及如何從存檔中讀取自身。 MFC 支援以這種方式使類序列化。 如果設計一個類來定義數據類型,並且打算序列化該類型的數據,則設計序列化。

## <a name="see-also"></a>另請參閱

[使用文件](../mfc/using-documents.md)
