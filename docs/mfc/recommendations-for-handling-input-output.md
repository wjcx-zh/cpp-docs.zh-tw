---
title: 處理輸入輸出的建議
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [MFC], about I/O
- file-based I/O options
- I/O [MFC]
- I/O [MFC], options
- I/O [MFC], file-based options
ms.assetid: d664b175-3b4a-40c3-b14b-39de6b12e419
ms.openlocfilehash: 956a92fd1761f61081afa2eb9c6cb35fe72b46d6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446906"
---
# <a name="recommendations-for-handling-inputoutput"></a>處理輸入/輸出的建議

您是否使用以檔案為基礎的 i/o，取決於您如何回應下列決策樹中的問題：

**應用程式中的主要資料是否位於磁片檔案中**

- 是，主要資料位於磁片檔案中：

     **應用程式是否會在檔案開啟時將整個檔案讀取到記憶體中，並在檔案儲存時將整個檔案寫回磁片**

   - 是：這是預設的 MFC 檔案例。 使用 `CDocument` 序列化。

   - 否：這通常是以交易為基礎的檔案更新的情況。 您會以每一交易為基礎更新檔案，而不需要 `CDocument` 序列化。

- 否，主要資料不會位於磁片檔案中：

     **資料位於 ODBC 資料來源中**

   - 是，資料位於 ODBC 資料來源中：

      使用 MFC 的資料庫支援。 此案例的標準 MFC 執行包含 `CDatabase` 物件，如[MFC：使用具有檔和視圖的資料庫類別](../data/mfc-using-database-classes-with-documents-and-views.md)一文所述。 應用程式可能也會讀取和寫入輔助檔案，而應用程式精靈的目的是 [資料庫檢視和檔案支援] 選項。 在此情況下，您會針對輔助檔案使用序列化。

   - 否，資料不位於 ODBC 資料來源中。

      此案例的範例：資料位於非 ODBC DBMS;資料是透過一些其他機制（例如 OLE 或 DDE）來讀取。

      在這種情況下，您不會使用序列化，而且您的應用程式將不會有開啟和儲存功能表項目。 您可能還是想要使用 `CDocument` 做為 home base，就像 MFC ODBC 應用程式使用檔來儲存 `CRecordset` 物件一樣。 但您不會使用架構的預設檔案開啟/儲存檔序列化。

為了支援 [檔案] 功能表上的 [開啟]、[儲存] 和 [另存新檔] 命令，架構提供了檔序列化。 序列化會讀取和寫入資料，包括從類別 `CObject`衍生的物件到永久儲存體，通常是磁片檔案。 序列化很容易使用，並提供許多您的需求，但可能不適用於許多資料存取應用程式。 資料存取應用程式通常會以每筆交易為基礎來更新資料。 它們會更新受交易影響的記錄，而不是一次讀取及寫入整個資料檔案。

如需序列化的詳細資訊，請參閱[序列化](../mfc/serialization-in-mfc.md)。

## <a name="see-also"></a>另請參閱

[序列化：序列化和資料庫輸入/輸出比較](../mfc/serialization-serialization-vs-database-input-output.md)
