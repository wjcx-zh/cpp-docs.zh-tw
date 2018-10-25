---
title: 資料錄集 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 221ff85f8e19990f1e804964f3a8be5136957995
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50058319"
---
# <a name="recordset-odbc"></a>資料錄集 (ODBC)

本主題適用於 MFC ODBC 類別。

A [CRecordset](../../mfc/reference/crecordset-class.md)物件都代表一組從資料來源選取的記錄。 記錄可以是：

- 資料表中。

- 這種查詢。

- 預存程序存取的一或多個資料表。

以資料表為基礎的資料錄集的範例是"all customers，"存取客戶資料表。 查詢的範例是"Joe smith 的所有發票。 」 （有時稱為預先定義的查詢） 的預存程序為基礎的資料錄集的範例是 「 繳的帳戶，全部 」 叫用後端資料庫中的預存程序。 資料錄集可以聯結兩個或多個資料表相同的資料來源，但不是從不同的資料來源的資料表。

> [!NOTE]
>  衍生的資料錄集類別，透過精靈的相關資訊，請參閱[加入 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)並[MFC 應用程式精靈、 資料庫支援](../../mfc/reference/database-support-mfc-application-wizard.md)。

> [!NOTE]
>  有些 ODBC 驅動程式支援的資料庫的檢視。 在此檢視是最初建立與 SQL 的查詢`CREATE VIEW`陳述式。 精靈目前不支援檢視，但您可自行編碼此支援。

##  <a name="_core_recordset_capabilities"></a> 資料錄集的功能

資料錄集的所有物件都共用下列功能：

- 如果資料來源不是唯讀的您可以指定您的資料錄集的被[可更新](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)，[可附加](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)，或唯讀狀態。 如果可以更新資料錄集，您可以選擇封閉式或開放式[鎖定](../../data/odbc/recordset-locking-records-odbc.md)方法，可讓您提供的驅動程式提供適當的鎖定支援。 如果唯讀資料來源，資料錄集就會處於唯讀模式。

- 您可以呼叫成員函式[捲](../../data/odbc/recordset-scrolling-odbc.md)透過將選取的記錄。

- 您可以[篩選](../../data/odbc/recordset-filtering-records-odbc.md)限制哪些記錄會選取從可用的記錄。

- 您可以[排序](../../data/odbc/recordset-sorting-records-odbc.md)的記錄，以遞增或遞減順序，根據一個或多個資料行。

- 您可以[參數化](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)限定在執行階段的資料錄集選取資料錄集。

##  <a name="_core_snapshots_and_dynasets"></a> 快照集和動態集

有兩種主要資料錄集：[快照集](../../data/odbc/snapshot.md)並[動態集](../../data/odbc/dynaset.md)。 兩者都支援類別`CRecordset`。 每個共用的通用特性的所有資料錄集，但每個也會在它自己的特殊方法來擴充通用的功能。 快照集提供資料的靜態檢視，並且可用於報表和其他情況下，您想檢視的資料存在於特定的時間。 當您想要顯示在資料錄集而不必重新查詢，或重新整理資料錄集的其他使用者所做的更新時，動態集將會很有用。 快照集和動態集可以是可更新或唯讀狀態。 若要反映資料錄加入或刪除由其他使用者時，呼叫[CRecordset::Requery](../../mfc/reference/crecordset-class.md#requery)。

`CRecordset` 也可讓兩個其他類型的資料錄集： 動態資料錄集和順向的資料錄集。 動態資料錄集是類似於動態集;不過，動態資料錄集反映出任何記錄，新增或刪除而不需呼叫`CRecordset::Requery`。 基於這個理由，動態資料錄集通常會耗上 DBMS 的處理時間，而且許多 ODBC 驅動程式不支援它們。 相反地，順向資料錄集提供最有效率的方法，不需要更新，或向後捲動的資料錄集的資料存取。 比方說，您可能會使用順向資料錄集，將資料從一個資料來源之間，您只需要以正向方向資料中移動。 若要使用的順向資料錄集，您必須執行下列兩個動作：

- 傳遞選項`CRecordset::forwardOnly`作為*nOpenType*參數[開啟](../../mfc/reference/crecordset-class.md#open)成員函式。

- 指定`CRecordset::readOnly`中*dwOptions*參數`Open`。

    > [!NOTE]
    >  動態集支援的 ODBC 驅動程式需求的詳細資訊，請參閱[ODBC](../../data/odbc/odbc-basics.md)。 如需包含在這個版本的 Visual c + + 中的 ODBC 驅動程式的清單，以及取得額外的驅動程式的相關資訊，請參閱[ODBC 驅動程式清單](../../data/odbc/odbc-driver-list.md)。

##  <a name="_core_your_recordsets"></a> 資料錄集

針對每個不同的資料表、 檢視或您想要存取的預存程序，您通常定義類別，衍生自`CRecordset`。 （例外狀況是資料庫聯結，其中一個資料錄集代表資料行從兩個或多個資料表）。當您衍生的資料錄集類別時，會啟用資料錄欄位交換 (RFX) 機制或大量資料錄欄位交換 (Bulk RFX) 機制，類似於對話方塊資料交換 (DDX) 機制。 RFX 和 Bulk RFX 簡化從資料來源的資料傳輸到您的資料錄集;RFX 此外從資料錄集，資料傳輸的資料來源。 如需詳細資訊，請參閱 <<c0> [ 資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)並[資料錄集： 擷取記錄中大量資料庫連接 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

資料錄集物件可讓您存取所有選取的記錄。 您使用多個選取的記錄之間捲動`CRecordset`成員函式，例如`MoveNext`和`MovePrev`。 在此同時，資料錄集物件，表示只有其中一個選取的記錄，目前的記錄。 您可以藉由宣告類別成員變數對應到資料行的資料表或從資料庫查詢產生之記錄的資料錄集來檢查目前資料錄的欄位。 資料錄集的資料成員的相關資訊，請參閱[資料錄集： 架構 (ODBC)](../../data/odbc/recordset-architecture-odbc.md)。

下列主題說明使用資料錄集物件的詳細資料。 主題所述功能分類並允許循序讀取自然瀏覽順序而定。

### <a name="topics-about-the-mechanics-of-opening-reading-and-closing-recordsets"></a>機制的開啟、 讀取和關閉資料錄集的相關主題

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

### <a name="topics-about-somewhat-more-advanced-techniques"></a>某種程度的相關主題更進階的技術

- [資料錄集：執行聯結 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)

- [資料錄集：宣告預先定義查詢的類別 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)

- [資料錄集：動態地繫結資料行 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)

- [資料錄集：擷取大量資料錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

- [資料錄集：使用大型的資料項目 (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)

- [資料錄集：取得 SUM 和其他彙總結果 (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)

### <a name="topics-about-how-recordsets-work"></a>資料錄集的運作方式的相關主題

- [資料錄集：資料錄集選取資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)

- [資料錄集：資料錄集更新資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)

## <a name="see-also"></a>另請參閱

[開放式資料庫連接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[異動 (ODBC)](../../data/odbc/transaction-odbc.md)