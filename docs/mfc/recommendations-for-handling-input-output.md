---
title: 處理輸入 / 輸出的建議
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [MFC], about I/O
- file-based I/O options
- I/O [MFC]
- I/O [MFC], options
- I/O [MFC], file-based options
ms.assetid: d664b175-3b4a-40c3-b14b-39de6b12e419
ms.openlocfilehash: 760c213c3af7f9c75374f04e3dfc6b9499eade5c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261962"
---
# <a name="recommendations-for-handling-inputoutput"></a>處理輸入/輸出的建議

您是否使用檔案為基礎的 I/O 是否取決於您如何回應下列決策樹中的問題：

**在您的應用程式中的主要資料存放在磁碟檔案中**

- 是的主要資料會位於磁碟檔案：

     **應用程式整份檔案讀入記憶體上開啟檔案，並將整個檔案寫回至磁碟上儲存檔案嗎**

   - [是]:這是預設 MFC 文件的情況。 使用`CDocument`序列化。

   - 否：這通常是以交易方式更新檔案的大小寫。 您更新每個交易為基礎的檔案，而不需`CDocument`序列化。

- 否，主要的資料不位於磁碟檔案中：

     **資料位在 ODBC 資料來源**

   - 是，資料會位於 ODBC 資料來源：

         Use MFC's database support. The standard MFC implementation for this case includes a `CDatabase` object, as discussed in the article [MFC: Using Database Classes with Documents and Views](../data/mfc-using-database-classes-with-documents-and-views.md). The application might also read and write an auxiliary file — the purpose of the application wizard "both a database view and file support" option. In this case, you'd use serialization for the auxiliary file.

   - 否，資料不會位於 ODBC 資料來源。

         Examples of this case: the data resides in a non-ODBC DBMS; the data is read via some other mechanism, such as OLE or DDE.

         In such cases, you won't use serialization, and your application won't have Open and Save menu items. You might still want to use a `CDocument` as a home base, just as an MFC ODBC application uses the document to store `CRecordset` objects. But you won't use the framework's default File Open/Save document serialization.

若要支援開啟、 儲存，並將儲存為命令，在 [檔案] 功能表上，此架構會提供文件序列化。 序列化讀取和寫入資料，包括物件衍生自類別`CObject`，到永久儲存體，通常是磁碟檔案。 序列化很容易使用，並提供許多您的需求，但可能很適合用在許多資料存取應用程式。 資料存取應用程式通常會更新每個交易為基礎的資料。 他們也會更新受交易而不是讀取和寫入整個資料檔案一次的記錄。

如需序列化的資訊，請參閱[序列化](../mfc/serialization-in-mfc.md)。

## <a name="see-also"></a>另請參閱

[序列化：序列化與資料庫輸入/輸出](../mfc/serialization-serialization-vs-database-input-output.md)
