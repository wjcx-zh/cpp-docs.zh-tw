---
title: 動態集
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, dynasets
- ODBC cursor library [ODBC], dynasets
- keyset-driven cursors in dynasets
- cursors [ODBC], keyset-driven cursors in dynasets
- cursor library [ODBC], dynaset availability
- recordsets [C++], dynasets
- dynasets
ms.assetid: 2867e6be-208e-4fe7-8bbe-b8697cb1045c
ms.openlocfilehash: ed7098600126005978c8b017e7db378fca4c1a68
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213235"
---
# <a name="dynaset"></a>動態集

本主題描述動態集並討論其[可用性](#_core_availability_of_dynasets)。

> [!NOTE]
>  本主題適用于 MFC ODBC 類別，包括[CRecordset](../../mfc/reference/crecordset-class.md)。 如需 DAO 類別中之動態程式的相關資訊，請參閱[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。 您可以使用 DAO 開啟動態集型別記錄集。

動態集是具有動態屬性的記錄集。 在其存留期間，動態集模式（通常稱為「動態集」）中的 recordset 物件會以下列方式與資料來源保持同步。 在多使用者環境中，其他使用者可能會編輯或刪除您的動態集內的記錄，或將記錄新增至您的動態集所代表的資料表。 應用程式在記錄集中加入或刪除的記錄會反映在您的動態集中。 其他使用者加入至資料表的記錄將不會反映在您的動態集內，直到您藉由呼叫其 `Requery` 成員函式重建動態集為止。 當其他使用者刪除記錄時，MFC 程式碼會略過記錄集內的刪除。 當您流覽至受影響的記錄時，其他使用者編輯現有記錄的變更就會反映在您的動態集中。

同樣地，您對動態集內的記錄所做的編輯，會反映在其他使用者所使用的動態集內。 您新增的記錄在重新查詢其動態集之前，不會反映在其他使用者的動態集中。 您刪除的記錄會在其他使用者的記錄集中標示為「已刪除」。 如果您有多個連接到相同的資料庫（多個 `CDatabase` 物件），則與這些連接相關聯的記錄集與其他使用者的記錄集具有相同的狀態。

當資料必須是動態的（例如，在航空公司保留系統中）時，動態集最有價值。

> [!NOTE]
> 若要使用動態集，您必須擁有支援動態集之資料來源的 ODBC 驅動程式，而且必須不載入 ODBC 資料指標程式庫。 如需詳細資訊，請參閱[動態集的可用性](#_core_availability_of_dynasets)。

若要指定記錄集為動態集，請將 `CRecordset::dynaset` 當做第一個參數傳遞至記錄集物件的 `Open` 成員函式。

> [!NOTE]
> 對於可更新的動態集，您的 ODBC 驅動程式必須支援定點更新語句或 `::SQLSetPos` ODBC API 函式。 如果兩者都受到支援，MFC 會使用 `::SQLSetPos` 以提高效率。

##  <a name="availability-of-dynasets"></a><a name="_core_availability_of_dynasets"></a>動態集的可用性

如果符合下列需求，MFC 資料庫類別就支援動態集：

- ODBC 資料指標程式庫 DLL 不得用於此資料來源。

   如果使用資料指標程式庫，它會針對動態集支援所需的基礎 ODBC 驅動程式，遮罩其一些功能。 如果您想要使用動態集（而且您的 ODBC 驅動程式具有動態集所需的功能，如本節其餘部分所述），您可以在建立 `CDatabase` 物件時，讓 MFC 不載入資料指標程式庫。 如需詳細資訊，請參閱[ODBC](../../data/odbc/odbc-basics.md)和 class `CDatabase`的[microsoft.office.interop.visio.documents.open](../../mfc/reference/cdatabase-class.md#openex)或[Open](../../mfc/reference/cdatabase-class.md#open)成員函式。

   在 ODBC 術語中，動態集和快照稱為「資料指標」。 資料指標是一種機制，用來追蹤其在記錄集中的位置。

- 適用于資料來源的 ODBC 驅動程式必須支援索引鍵集驅動資料指標。

   索引鍵集驅動資料指標會藉由取得並儲存一組索引鍵，來管理資料表中的資料。 當使用者滾動至特定記錄時，會使用這些金鑰來取得資料表中的目前資料。 若要判斷您的驅動程式是否提供這種支援，請使用*SQL_SCROLL_OPTIONS*參數來呼叫 `::SQLGetInfo` ODBC API 函式。

   如果您嘗試開啟沒有索引鍵集支援的動態集，您會取得 `CDBException`，其中包含傳回碼值 AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED。

- 適用于資料來源的 ODBC 驅動程式必須支援延伸提取。

   延伸提取是一種能夠回溯的功能，並可在 SQL 查詢的結果記錄上向前復原。 若要判斷您的驅動程式是否支援此功能，請使用*SQL_API_SQLEXTENDEDFETCH*參數呼叫 `::SQLGetFunctions` ODBC API 函式。

如果您想要可更新的動態集（或快照集），您的 ODBC 驅動程式也必須支援 `::SQLSetPos` ODBC API 函式或定點更新。 `::SQLSetPos` 函數可讓 MFC 更新資料來源，而不需要傳送 SQL 語句。 如果這項支援可供使用，MFC 會在喜好設定中使用它，以使用 SQL 來進行更新。 若要判斷您的驅動程式是否支援 `::SQLSetPos`，請使用*SQL_POS_OPERATIONS*參數呼叫 `::SQLGetInfo`。

定點更新使用 SQL 語法（其為**目前的**\<cursorname > 的格式），以識別資料來源上資料表中的特定資料列。 若要判斷您的驅動程式是否支援定點更新，請使用*SQL_POSITIONED_STATEMENTS*參數來呼叫 `::SQLGetInfo`。

一般來說，MFC 動態集（但不是順向記錄集）需要具有層級 2 API 一致性的 ODBC 驅動程式。 如果資料來源的驅動程式符合層級 1 API 集，您仍然可以同時使用可更新和唯讀的快照集和順向記錄集，而不是動態集。 不過，如果支援擴充提取和索引鍵集驅動資料指標，層級1驅動程式可以支援動態集。 如需 ODBC 一致性層級的詳細資訊，請參閱[odbc](../../data/odbc/odbc-basics.md)。

> [!NOTE]
> 如果您想要同時使用快照集和動態連結程式庫，您必須將它們以兩個不同的 `CDatabase` 物件（兩個不同的連接）做為基礎。

不同于快照集（使用 ODBC 資料指標程式庫所維護的中繼儲存體），在您滾動到資料來源後，動態程式會直接從該資料來源提取記錄。 這會讓動態集所選取的記錄與資料來源同步處理。

如需此版本 Visual C++ 隨附之 ODBC 驅動程式的清單，以及取得其他驅動程式的相關資訊，請參閱 [ODBC 驅動程式清單](../../data/odbc/odbc-driver-list.md)。

## <a name="see-also"></a>另請參閱

[開放式資料庫連接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
