---
title: 資料錄集：建立和關閉資料錄集 (ODBC)
ms.date: 05/09/2019
helpviewer_keywords:
- ODBC recordsets, creating
- recordsets, creating
- recordsets, opening
- recordsets, closing
- ODBC recordsets, closing
- ODBC recordsets, opening
ms.assetid: 8d2aac23-4396-4ce2-8c60-5ecf1b360d3d
ms.openlocfilehash: 1ff6f3050ff8ca0be746b91216300632323dcd85
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216514"
---
# <a name="recordset-creating-and-closing-recordsets-odbc"></a>資料錄集：建立和關閉資料錄集 (ODBC)

> [!NOTE]
> Visual Studio 2019 和更新版本中未提供「MFC ODBC 消費者」精靈。 您仍然可以手動建立消費者。

本主題適用於 MFC ODBC 類別。

若要使用資料錄集，請建構資料錄集物件，然後呼叫其 `Open` 成員函式來執行資料錄集的查詢並選取記錄。 當您使用完資料錄集時，請關閉並終結物件。

本主題將說明：

- [何時及如何建立資料錄集](#_core_creating_recordsets_at_run_time)。

- [何時及如何將資料錄集的行為參數化、篩選、排序或鎖定來限定此行為](#_core_setting_recordset_options)。

- [何時及如何關閉資料錄集物件](#_core_closing_a_recordset)。

## <a name="creating-recordsets-at-run-time"></a><a name="_core_creating_recordsets_at_run_time"></a> 在執行階段建立資料錄集

您通常需先撰寫應用程式特定資料錄集類別，才能在程式中建立資料錄集物件。 如需有關此初步步驟的詳細資訊，請參閱[新增 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)。

當您需要從資料來源選取記錄時，請開啟動態集或快照集物件。 要建立的物件類型取決於您需要在應用程式中使用資料來做什麼，以及取決於您的 ODBC 驅動程式所支援的項目。 如需詳細資訊，請參閱[動態集](../../data/odbc/dynaset.md)和[快照集](../../data/odbc/snapshot.md)。

#### <a name="to-open-a-recordset"></a>開啟資料錄集

1. 建構您 `CRecordset` 衍生類別的物件。

   您可以在堆積上或在函式的堆疊框架上建構物件。

1. 視需要修改預設資料錄集行為。 如需可用的選項，請參閱[設定資料錄集選項](#_core_setting_recordset_options)。

1. 呼叫物件的 [Open](../../mfc/reference/crecordset-class.md#open) 成員函式。

在建構函式中，傳遞 `CDatabase` 物件的指標，或傳遞 NULL 以使用架構會依據 [GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect) 成員函式所傳回之連接字串來建構並開啟的暫時資料庫物件。 `CDatabase` 物件可能已經連線至資料來源。

`Open` 呼叫會使用 SQL 從資料來源中選取記錄。 所選取的第一個記錄 (如果有的話) 是目前的記錄。 此記錄的欄位值會儲存在資料錄集物件的欄位資料成員中。 如果已選取任何資料，`IsBOF` 和 `IsEOF` 成員函式都會傳回 0。

在您的 [Open](../../mfc/reference/crecordset-class.md#open) 呼叫中，您可以：

- 指定資料錄集是動態集還是快照集。 資料錄集預設會以快照集的形式開啟。 或者，您可以指定一個順向資料錄集，這會只允許一次向前捲動一個記錄。

   資料錄集預設會使用儲存在 `CRecordset` 資料成員 `m_nDefaultType` 中的預設類型。 精靈會撰寫程式碼將 `m_nDefaultType` 初始化成您在精靈中選擇的資料錄集類型。 您可以不接受此預設值，而是替代成另一個資料錄集類型。

- 指定一個字串來取代資料錄集所建構的預設 SQL **SELECT** 陳述式。

- 指定資料錄集是唯讀還是僅附加。 資料錄集預設會允許完整更新，但您可以將其限制成僅限新增新的記錄，也可以不允許所有更新。

下列範例示範如何開啟 `CStudentSet` 類別 (應用程式特定類別) 的唯讀快照集物件：

```cpp
// Construct the snapshot object
CStudentSet rsStudent( NULL );
// Set options if desired, then open the recordset
if(!rsStudent.Open(CRecordset::snapshot, NULL, CRecordset::readOnly))
    return FALSE;
// Use the snapshot to operate on its records...
```

在您呼叫 `Open` 之後，請使用成員函式和物件的資料成員來與記錄搭配運作。 在某些情況下，您可能會想要重新查詢或重新整理資料錄集，以包含已在資料來源上發生的變更。 如需詳細資訊，請參閱[記錄集：重新查詢記錄集（ODBC）](../../data/odbc/recordset-requerying-a-recordset-odbc.md)。

> [!TIP]
> 您在開發期間使用的連接字串可能與最終使用者所需的連接字串不同。 如需有關在此方面一般化應用程式的構想，請參閱[資料來源：管理連接（ODBC）](../../data/odbc/data-source-managing-connections-odbc.md)。

## <a name="setting-recordset-options"></a><a name="_core_setting_recordset_options"></a> 設定資料錄集選項

在您建構資料錄集物件之後但在呼叫 `Open` 以選取記錄之前，您可能會想要設定一些選項來控制資料錄集的行為。 針對所有資料錄集，您可以：

- 指定[篩選](../../data/odbc/recordset-filtering-records-odbc.md)來限制記錄選取範圍。

- 指定記錄的[排序](../../data/odbc/recordset-sorting-records-odbc.md)次序。

- 指定[參數](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)，以便使用在執行階段取得或計算出的資訊來選取記錄。

如果條件成立，您也可以設定下列選項：

- 如果資料錄集可更新且支援鎖定選項，請指定用於更新的[鎖定](../../data/odbc/recordset-locking-records-odbc.md)方法。

> [!NOTE]
> 若要影響記錄選取範圍，您必須在呼叫 `Open` 成員函式之前先設定這些選項。

## <a name="closing-a-recordset"></a><a name="_core_closing_a_recordset"></a> 關閉資料錄集

使用完資料錄集時，您必須處置它並將其記憶體解除配置。

#### <a name="to-close-a-recordset"></a>關閉資料錄集

1. 呼叫其 [Close](../../mfc/reference/crecordset-class.md#close) 成員函式。

1. 終結資料錄集物件。

   如果您是在函式的堆疊框架上宣告它，當物件超出範圍時，系統會自動將它終結。 否則，請使用 **`delete`** 運算子。

`Close` 會釋放資料錄集的 `HSTMT` 控制代碼。 它不會終結 C++ 物件。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：捲動 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)<br/>
[記錄集：加入、更新和刪除記錄（ODBC）](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)
