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
ms.openlocfilehash: c365120a385c440f09f0ee4c0a2fc52afb55834f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371728"
---
# <a name="recommendations-for-handling-inputoutput"></a>處理輸入/輸出的建議

是否使用基於檔案的 I/O 取決於您如何回答以下決策樹中的問題:

**應用程式中的主要資料是否駐在磁碟檔案中**

- 是的,主資料駐留在磁碟檔中:

   **應用程式在檔案打開時將整個檔讀入記憶體,並將整個檔寫回檔儲存上的磁碟嗎?**

  - 是:這是預設的 MFC 文檔案例。 使用`CDocument`序列化。

  - 否:通常情況下是基於事務的檔更新。 基於每個事務更新檔,不需要`CDocument`序列化。

- 否,主資料不駐留在磁碟檔中:

   **資料是否駐留在 ODBC 資料來源中**

  - 是的,資料駐留在 ODBC 資料來源中:

      使用 MFC 的資料庫支援。 此案例的標準 MFC 實現`CDatabase`包括一個物件,如 MFC 一文中所述[:使用包含文件和檢視的資料庫類](../data/mfc-using-database-classes-with-documents-and-views.md)。 應用程式還可以讀取和寫入輔助檔案 - 應用程式精靈"資料庫檢視和檔支援"選項的目的。 在這種情況下,您將對輔助檔使用序列化。

  - 否,數據不駐留在 ODBC 數據源中。

      這種情況的示例:數據駐留在非 ODBC DBMS 中;數據通過其他機制(如 OLE 或 DDE)讀取。

      在這種情況下,您不會使用序列化,並且應用程式將沒有"打開"和"保存"選單項。 您可能仍要使用`CDocument`作為 主資料庫,就像 MFC ODBC`CRecordset`應用程式使用文件儲存 物件一樣。 但是,您不會使用框架的預設檔案打開/儲存文檔序列化。

為了在「檔」功能表上支援「打開」、「儲存」和「保存為」命令,框架提供文檔序列化。 序列化將資料(包括從類`CObject`派生的物件)讀取和寫入永久存儲,通常是磁碟檔。 序列化易於使用,可滿足您的許多需求,但在許多數據訪問應用程式中可能不合適。 數據訪問應用程式通常根據每個事務更新數據。 它們更新受事務影響的記錄,而不是一次讀取和寫入整個數據檔。

有關序列化的資訊,請參閱[序列化](../mfc/serialization-in-mfc.md)。

## <a name="see-also"></a>另請參閱

[序列化：序列化和資料庫輸入/輸出比較](../mfc/serialization-serialization-vs-database-input-output.md)
