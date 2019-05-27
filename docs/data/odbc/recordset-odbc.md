---
title: 資料錄集 (ODBC)
ms.date: 05/09/2019
helpviewer_keywords:
- recordsets, snapshots
- recordsets, creating
- dynamic recordsets
- forward-only recordsets
- recordsets, dynasets
- ODBC recordsets, CRecordset objects
- ODBC recordsets
- recordsets, about recordsets
- snapshots, ODBC recordsets
- dynasets
ms.assetid: 333337c5-575e-4d26-b5f6-47166ad7874d
ms.openlocfilehash: b043b08e13611b87bbffbe9dfb3255d5520e3359
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707828"
---
# <a name="recordset-odbc"></a>資料錄集 (ODBC)

本主題適用於 MFC ODBC 類別。

[CRecordset](../../mfc/reference/crecordset-class.md) 物件表示選取自資料來源的一組資料錄。 資料錄可以來自：

- 資料表。

- 查詢。

- 存取一或多個資料表的預存程序。

以資料表為基礎的資料錄集的範例是 "all customers"，可存取客戶資料表。 查詢的範例是 "all invoices for Joe Smith"。 以預存程序 (有時稱為預先定義的查詢) 為基礎的資料錄集範例是 "all of the delinquent accounts"，這會叫用後端資料庫中的預存程序。 資料錄集可以聯結來自相同資料來源的兩個或多個資料表，但無法聯結來自不同資料來源的資料表。

> [!NOTE]
>  有些 ODBC 驅動程式支援資料庫的檢視。 這種意義上的檢視是最初使用 SQL `CREATE VIEW` 陳述式建立的查詢。

##  <a name="_core_recordset_capabilities"></a> 資料錄集功能

所有資料錄集物件都共用下列功能：

- 如果資料來源不是唯讀的，您可以指定您的資料錄集是[可更新](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)、[可附加](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)，或是唯讀的。 如果資料錄集是可更新的，您可以選擇封閉式或開放式的[鎖定](../../data/odbc/recordset-locking-records-odbc.md)方法，但前提是，驅動程式會提供適當的鎖定支援。 如果資料來源是唯讀的，資料錄集就會是唯讀的。

- 您可以呼叫成員函式以[捲動](../../data/odbc/recordset-scrolling-odbc.md)選取的資料錄。

- 您可以[篩選](../../data/odbc/recordset-filtering-records-odbc.md)資料錄，以限制可以從可用的資料錄選取哪些資料錄。

- 您可以根據一個或多個資料行，使用遞增或遞減順序[排序](../../data/odbc/recordset-sorting-records-odbc.md)資料錄。

- 您可以將資料錄集[參數化](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)，以限定在執行階段的資料錄集選取範圍。

##  <a name="_core_snapshots_and_dynasets"></a> 快照集和動態集

資料錄集有兩種主要類型：[快照集](../../data/odbc/snapshot.md)和[動態集](../../data/odbc/dynaset.md)。 兩者都受到 `CRecordset` 類別支援。 每種類型都會共用所有資料錄集的通用特性，但每種類型也都會透過自己的特殊方法來擴充通用功能。 快照集提供資料的靜態檢視，而且可用於報表，以及您希望資料檢視存在於特定時間的其他情況。 當您希望在資料錄集中看到其他使用者所做的更新，而不必重新查詢或重新整理資料錄集時，動態集將會很有用。 快照集和動態集可以是可更新的或唯讀的。 若要反映其他使用者新增或刪除的資料錄，請呼叫 [CRecordset::Requery](../../mfc/reference/crecordset-class.md#requery)。

`CRecordset` 也允許其他兩種類型的資料錄集：動態資料錄集和順向資料錄集。 動態資料錄集類似於動態集；不過，動態資料錄集會反映新增或刪除的任何資料錄，而不需呼叫 `CRecordset::Requery`。 因此，動態資料錄集通常會在 DBMS 上耗費大量的處理時間，而且許多 ODBC 驅動程式並不提供支援。 相反地，順向資料錄集會針對不需要更新或向後捲動的資料錄集，提供最有效率的資料存取方法。 例如，您可以使用順向資料錄集，將資料從一個資料來源移轉到另一個資料來源，而且您只需要以順向移動資料即可。 若要使用順向資料錄集，您必須執行下列兩個動作：

- 傳遞選項 `CRecordset::forwardOnly` 作為 [Open](../../mfc/reference/crecordset-class.md#open) 成員函式的 *nOpenType* 參數。

- 在 `Open` 的 *dwOptions* 參數中指定 `CRecordset::readOnly`。

    > [!NOTE]
    >  如需有關動態集支援之 ODBC 驅動程式需求的資訊，請參閱 [ODBC](../../data/odbc/odbc-basics.md)。 如需此版本 Visual C++ 隨附之 ODBC 驅動程式的清單，以及取得其他驅動程式的相關資訊，請參閱 [ODBC 驅動程式清單](../../data/odbc/odbc-driver-list.md)。

##  <a name="_core_your_recordsets"></a> 您的資料錄集

針對每個您想要存取的不同資料表、檢視或預存程序，您通常要定義一個衍生自 `CRecordset` 的類別  (例外狀況是資料庫聯結，其中一個資料錄集代表來自兩個或多個資料表的資料行)。當您衍生資料錄集類別時，會啟用資料錄欄位交換 (RFX) 機制或大量資料錄欄位交換 (大量 RFX) 機制，這類似於對話方塊資料交換 (DDX) 機制。 RFX 和大量 RFX 會將從資料來源傳輸資料到資料錄集的程序簡化；此外，RFX 還會從資料錄集傳輸資料到資料來源。 如需詳細資訊，請參閱[資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md) 和[資料錄集：擷取大量資料錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

資料錄集物件可讓您存取所有選取的資料錄。 您可以使用 `CRecordset` 成員函式 (例如 `MoveNext` 和 `MovePrev`) 捲動多個選取的資料錄，。 同時，一個資料錄集物件只代表其中一個選取的資料錄，也就是目前的資料錄。 您可以宣告對應到資料表資料行，或資料庫查詢所產生之資料錄資料行的資料錄集類別成員變數，藉此檢查目前資料錄的欄位。 如需有關資料錄集資料成員的資訊，請參閱[資料錄集：架構 (ODBC)](../../data/odbc/recordset-architecture-odbc.md)。

下列主題將說明使用資料錄集物件的詳細資料。 這些主題會以功能分類和自然瀏覽順序列出，以允許循序讀取。

### <a name="topics-about-the-mechanics-of-opening-reading-and-closing-recordsets"></a>開啟、讀取和關閉資料錄集機制的相關主題

- [資料錄集：架構 (ODBC)](../../data/odbc/recordset-architecture-odbc.md)

- [資料錄集：宣告資料表的類別 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)

- [資料錄集：建立和關閉資料錄集 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)

- [資料錄集：捲動 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)

- [資料錄集：書籤和絕對位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)

- [資料錄集：篩選資料錄 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)

- [資料錄集：排序資料錄 (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)

- [資料錄集：參數化資料錄集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

### <a name="topics-about-the-mechanics-of-modifying-recordsets"></a>修改資料錄集機制的相關主題

- [資料錄集：新增、更新和刪除資料錄 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)

- [資料錄集：鎖定資料錄 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)

- [資料錄集：重新查詢資料錄集 (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)

### <a name="topics-about-somewhat-more-advanced-techniques"></a>某種程度上更進階技術的相關主題

- [資料錄集：執行聯結 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)

- [資料錄集：宣告預先定義查詢的類別 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)

- [資料錄集：動態地繫結資料行 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)

- [資料錄集：擷取大量資料錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

- [資料錄集：使用大型的資料項目 (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)

- [資料錄集：取得 SUM 和其他彙總結果 (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)

### <a name="topics-about-how-recordsets-work"></a>資料錄集運作方式的相關主題

- [資料錄集：資料錄集選取資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)

- [資料錄集：資料錄集更新資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)

## <a name="see-also"></a>另請參閱

[開放式資料庫連接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[異動 (ODBC)](../../data/odbc/transaction-odbc.md)