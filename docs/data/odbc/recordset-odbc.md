---
title: 資料錄集 (ODBC) |Microsoft 文件
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
ms.openlocfilehash: 0c59de3c5db2e1ec658a09279cb42e2833a4109e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33092479"
---
# <a name="recordset-odbc"></a>資料錄集 (ODBC)
本主題適用於 MFC ODBC 類別。  
  
 A [CRecordset](../../mfc/reference/crecordset-class.md)物件都代表一組選取自資料來源的記錄。 記錄可以來自：  
  
-   資料表中。  
  
-   查詢。  
  
-   預存程序存取的一或多個資料表。  
  
 以資料表為基礎的資料錄集的範例是 「 所有客戶 」 存取 Customer 資料表。 查詢的範例是 「 所有發票 Joe Smith。 」 資料錄集 （有時稱為預先定義的查詢） 的預存程序為基礎的範例是 「 繳帳戶，全部 」 叫用後端資料庫中的預存程序。 兩個或多個從相同的資料來源的資料表，但不是從不同的資料來源的資料表，可以加入資料錄集。  
  
> [!NOTE]
>  衍生的精靈資料錄集類別的相關資訊，請參閱[加入 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)和[MFC 應用程式精靈、 資料庫支援](../../mfc/reference/database-support-mfc-application-wizard.md)。  
  
> [!NOTE]
>  有些 ODBC 驅動程式支援資料庫的檢視。 這方面的檢視是最初建立 SQL 查詢`CREATE VIEW`陳述式。 這些精靈目前不支援檢視，但可以自行撰寫程式碼這項支援。  
  
##  <a name="_core_recordset_capabilities"></a> 資料錄集的功能  
 資料錄集的所有物件都共用的下列功能：  
  
-   如果資料來源不是唯讀的您可以指定資料錄集是[可更新](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)，[可附加](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)，或唯讀狀態。 如果可以更新資料錄集，您可以選擇開放式或封閉式[鎖定](../../data/odbc/recordset-locking-records-odbc.md)方法，提供驅動程式提供適當的鎖定支援。 如果資料來源是唯讀，則資料錄集將處於唯讀模式。  
  
-   您可以呼叫成員函式來[捲動](../../data/odbc/recordset-scrolling-odbc.md)透過選取的記錄。  
  
-   您可以[篩選](../../data/odbc/recordset-filtering-records-odbc.md)以限制哪些記錄會選取從可用的記錄。  
  
-   您可以[排序](../../data/odbc/recordset-sorting-records-odbc.md)的記錄，以遞增或遞減順序，根據一個或多個資料行。  
  
-   您可以[參數化](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)來限定資料錄集選取範圍，在執行階段資料錄集。  
  
##  <a name="_core_snapshots_and_dynasets"></a> 快照集和動態集  
 有兩種主要資料錄集：[快照](../../data/odbc/snapshot.md)和[dynaset](../../data/odbc/dynaset.md)。 類別都受到`CRecordset`。 每個共用共同的特性的所有資料錄集，但每個也在自己特製化的方式延伸的通用功能。 快照集提供資料的靜態檢視，而且可用於報表和其他您想在其中的資料檢視，存在於特定的時間。 當您想要看到資料錄集中而不必重新查詢，或重新整理資料錄集的其他使用者所做的更新，動態集很有用。 快照集和動態集可以是可更新或唯讀狀態。 若要反映資料錄加入或刪除由其他使用者呼叫[CRecordset::Requery](../../mfc/reference/crecordset-class.md#requery)。  
  
 `CRecordset` 也可讓兩個其他類型的資料錄集： 動態資料錄集和順向資料錄集。 動態資料錄集是類似於動態集;不過，動態資料錄集反映加入或刪除而不會呼叫任何記錄`CRecordset::Requery`。 基於這個理由，動態資料錄集有關處理時間的 dbms，一般而言成本較高，而且許多 ODBC 驅動程式不支援它們。 相反地，順向資料錄集提供的不需要更新或向後捲動資料錄集的資料存取最有效率的方法。 例如，您可能使用順向資料錄集將資料從一個資料來源到另一個，您只需要以正向方向資料中移動。 若要使用的順向資料錄集，您必須執行下列兩個動作：  
  
-   傳遞選項**CRecordset::forwardOnly**為`nOpenType`參數[開啟](../../mfc/reference/crecordset-class.md#open)成員函式。  
  
-   指定**CRecordset::readOnly**中`dwOptions`參數**開啟**。  
  
    > [!NOTE]
    >  動態集支援的 ODBC 驅動程式需求的詳細資訊，請參閱[ODBC](../../data/odbc/odbc-basics.md)。 包含在這個版本的 Visual c + + 中的 ODBC 驅動程式清單以及取得其他驅動程式的相關資訊，請參閱[ODBC 驅動程式清單](../../data/odbc/odbc-driver-list.md)。  
  
##  <a name="_core_your_recordsets"></a> 您的資料錄集  
 對於每個相異的資料表、 檢視表或您想要存取的預存程序，您通常定義類別，衍生自`CRecordset`。 （例外狀況是資料庫的連結，其中一個資料錄集代表資料行從兩個或多個資料表）。當您衍生的資料錄集類別時，您啟用資料錄欄位交換 (RFX) 機制或大量資料錄欄位交換 (Bulk RFX) 機制，類似於對話方塊資料交換 (DDX) 機制。 RFX 和 Bulk RFX 簡化從資料來源的資料傳輸至資料錄集;RFX 此外從資料錄集，資料傳輸的資料來源。 如需詳細資訊，請參閱[資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)和[資料錄集： 擷取記錄中大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 資料錄集物件可讓您存取所有選取的記錄。 您可以捲動使用多個選取的記錄`CRecordset`成員函式，例如`MoveNext`和`MovePrev`。 同時，資料錄集物件，代表其中一個選取的資料錄，目前的記錄。 您可以藉由宣告類別成員變數對應到資料行的資料表或從資料庫查詢產生的記錄資料錄集來檢查目前資料錄的欄位。 資料錄集的資料成員的相關資訊，請參閱[資料錄集： 架構 (ODBC)](../../data/odbc/recordset-architecture-odbc.md)。  
  
 下列主題說明使用資料錄集物件的詳細資料。 主題會列出功能分類和自然瀏覽順序容許循序讀取。  
  
### <a name="topics-about-the-mechanics-of-opening-reading-and-closing-recordsets"></a>開啟、 讀取和關閉資料錄集的機制的相關主題  
  
-   [資料錄集：架構 (ODBC)](../../data/odbc/recordset-architecture-odbc.md)  
  
-   [資料錄集：宣告資料表的類別 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)  
  
-   [資料錄集：建立和關閉資料錄集 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)  
  
-   [資料錄集：捲動 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)  
  
-   [資料錄集：書籤和絕對位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)  
  
-   [資料錄集：篩選資料錄 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)  
  
-   [資料錄集：排序資料錄 (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)  
  
-   [資料錄集：參數化資料錄集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)  
  
### <a name="topics-about-the-mechanics-of-modifying-recordsets"></a>修改資料錄集機制的相關主題  
  
-   [資料錄集：新增、更新和刪除資料錄 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)  
  
-   [資料錄集：鎖定資料錄 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)  
  
-   [資料錄集：重新查詢資料錄集 (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)  
  
### <a name="topics-about-somewhat-more-advanced-techniques"></a>進階技術的主題  
  
-   [資料錄集：執行聯結 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)  
  
-   [資料錄集：宣告預先定義查詢的類別 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)  
  
-   [資料錄集：動態地繫結資料行 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)  
  
-   [資料錄集：擷取大量資料錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)  
  
-   [資料錄集：使用大型的資料項目 (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)  
  
-   [資料錄集：取得 SUM 和其他彙總結果 (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)  
  
### <a name="topics-about-how-recordsets-work"></a>資料錄集的運作方式的相關主題  
  
-   [資料錄集：資料錄集選取資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)  
  
-   [資料錄集：資料錄集更新資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)  
  
## <a name="see-also"></a>另請參閱  
 [開放式資料庫連接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)   
 [MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [異動 (ODBC)](../../data/odbc/transaction-odbc.md)