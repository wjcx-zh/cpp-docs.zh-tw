---
title: 資料錄集：資料錄集選取資料錄的方式 (ODBC)
ms.date: 05/09/2019
helpviewer_keywords:
- recordsets, selecting records
- record selection, ODBC recordsets
- SQL statements, recordset
- records, selecting
- recordsets, constructing SQL statements
- ODBC recordsets, selecting records
ms.assetid: 343a6a91-aa4c-4ef7-b21f-2f2bfd0d3787
ms.openlocfilehash: 252d17fc56c13415f1068d6b16ed8b1ee663b5f1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212884"
---
# <a name="recordset-how-recordsets-select-records-odbc"></a>資料錄集：資料錄集選取資料錄的方式 (ODBC)

> [!NOTE]
> Visual Studio 2019 及更新版本中未提供 MFC ODBC 消費者精靈。 您仍然可以手動建立消費者。

本主題適用於 MFC ODBC 類別。

本主題將說明：

- [您在選取資料錄上的角色和選項](#_core_your_options_in_selecting_records)。

- [資料錄集如何建構其 SQL 陳述式並選取資料錄](#_core_how_a_recordset_constructs_its_sql_statement)。

- [您可以如何自訂選取項目](#_core_customizing_the_selection)。

資料錄集會將 SQL 陳述式傳送至 ODBC 驅動程式，來透過該驅動程式從資料來源選取資料錄。 所傳送的 SQL 會取決於您設計及開啟資料錄集類別的方式。

##  <a name="your-options-in-selecting-records"></a><a name="_core_your_options_in_selecting_records"></a> 您在選取資料錄上的選項

下表會顯示您在選取資料錄上的選項。

### <a name="how-and-when-you-can-affect-a-recordset"></a>您可以影響到資料錄集的方式和時機

|當您|您可以|
|--------------|-------------|
|使用 [新增類別] 精靈來宣告您的資料錄集類別|指定要從中選取的資料表。<br /><br /> 指定要包含的資料行。<br /><br /> 請參閱[加入 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)。|
|完成資料錄集類別實作|覆寫如 `OnSetOptions` (進階) 等的成員函式來設定應用程式特定選項，或是變更預設值。 如果您想要參數化的資料錄集，請指定參數資料成員。|
|建構資料錄集物件 (在您呼叫 `Open` 之前)|在篩選資料錄的 **WHERE** 子句中，指定要使用的搜尋條件 (可能是複合)。 請參閱[記錄集：篩選記錄（ODBC）](../../data/odbc/recordset-filtering-records-odbc.md)。<br /><br /> 在排序資料錄的 **ORDER BY** 子句中指定要使用的排列順序。 請參閱記錄[集：排序記錄（ODBC）](../../data/odbc/recordset-sorting-records-odbc.md)。<br /><br /> 針對您加入至類別中的任何參數指定參數值。 請參閱[記錄集：參數化記錄集（ODBC）](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。|

|呼叫 `Open` 來執行資料錄集的查詢|指定自訂的 SQL 字串來取代由精靈設定的預設 SQL 字串。 請參閱*類別庫參考*和[SQL：自訂記錄集的 SQL 語句（ODBC）](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)中的[CRecordset：： Open](../../mfc/reference/crecordset-class.md#open) 。 |

|呼叫 `Requery` 來搭配資料來源上的最新值重新查詢資料錄集|指定新的參數、篩選或排序。 請參閱[記錄集：重新查詢記錄集（ODBC）](../../data/odbc/recordset-requerying-a-recordset-odbc.md)。 |

##  <a name="how-a-recordset-constructs-its-sql-statement"></a><a name="_core_how_a_recordset_constructs_its_sql_statement"></a> 資料錄集如何建構其 SQL 陳述式

當您呼叫資料錄集物件的 [Open](../../mfc/reference/crecordset-class.md#open) 成員函式時，`Open` 會使用下列部分或全部材料來建構 SQL 陳述式：

- *lpszSQL* 參數會被傳遞至 `Open`。 若非 NULL，此參數便會指定自訂的 SQL 字串或部分字串。 架構會剖析該字串。 如果該字串是 SQL **SELECT** 陳述式或 ODBC **CALL** 陳述式，架構便會將該字串作為資料錄集的 SQL 陳述式使用。 如果字串不是以 "SELECT" 或 "{CALL" 開始，架構便會使用提供來建造 SQL **FROM** 子句的項目。

- 由 [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql)所傳回的字串。 根據預設，這是您在精靈中為資料錄集所指定的資料表名稱，但您可以變更函式會傳回的內容。 架構會呼叫 `GetDefaultSQL`。如果字串不是以 "SELECT" 或 "{CALL" 開始，系統會將它假設為資料表名稱，且其會被用來建構 SQL 字串。

- 資料錄集的欄位資料成員，其會被繫結至資料表的特定資料行。 架構會將資料錄資料行繫結至這些成員的位址，並使用它們作為緩衝區。 架構會從資料錄集的 [DoFieldExchange](../../data/odbc/record-field-exchange-using-rfx.md) 或 [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) 成員函式中的 [RFX](../../mfc/reference/crecordset-class.md#dofieldexchange) 或大量 RFX 函式呼叫，來判斷欄位資料成員和資料表資料行之間的關聯性。

- 資料錄集的[篩選](../../data/odbc/recordset-filtering-records-odbc.md) (若有的話)，包含在 [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) 資料成員中。 架構會使用此字串來建構 SQL **WHERE** 子句。

- 資料錄集的[排序](../../data/odbc/recordset-sorting-records-odbc.md)順序 (若有的話)，包含在 [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) 資料成員中。 架構會使用此字串來建構 SQL **ORDER BY** 子句。

   > [!TIP]
   > 若要使用 SQL **GROUP BY** 子句 (以及可能的 **HAVING** 子句)，請將子句附加至您篩選字串的結尾。

- 您針對類別指定之任何[參數資料成員](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)的值。 您會在呼叫 `Open` 或 `Requery` 之前設定參數值。 架構會將參數值繫結至 SQL 字串中的 "?" 預留位置。 在編譯時間時，您會搭配預留位置指定字串。 在執行階段時，架構會根據您所傳遞的參數值填入詳細資料。

`Open` 會根據這些材料建構 SQL **SELECT** 陳述式。 請參閱[自訂選取項目](#_core_customizing_the_selection)以取得架構使用材料之方式的詳細資料。

在建構陳述式之後，`Open` 會將 SQL 傳送至 ODBC 驅動程式管理員 (以及 ODBC 資料指標程式庫，如果其位於記憶體中的話)，其會針對特定的 DBMS 將它傳送至 ODBC 驅動程式。 驅動程式會與 DBMS 通訊，以在資料來源上執行選取並擷取第一個資料錄。 架構會將資料錄載入資料錄集的欄位資料成員內。

您可以結合使用這些技術來開啟[資料表](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)，以及根據[聯結](../../data/odbc/recordset-performing-a-join-odbc.md)多個資料表來建構查詢。 透過額外的自訂，您可以呼叫[預先定義的查詢](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md) (預存程序)，選取在設計期間未知的資料表資料行，然後將它們[繫結](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)至資料錄集欄位，或是您可以執行大部分其他資料存取工作。 您無法透過自訂資料錄集來達成的工作，仍然可以透過[呼叫 ODBC API 函式](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)或搭配 [CDatabase::ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql) 直接執行 SQL 陳述式來達成。

##  <a name="customizing-the-selection"></a><a name="_core_customizing_the_selection"></a> 自訂選取項目

除了提供篩選、排列順序或參數之外，您可以採取下列動作來自定資料錄集的選取項目：

- 當您呼叫資料錄集的 *Open* 時，在 [lpszSQL](../../mfc/reference/crecordset-class.md#open) 中傳遞自訂 SQL 字串。 您在 *lpsqSQL* 中所傳遞的項目，都會優先於 [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) 成員函式所傳回的項目。

   如需詳細資訊，請參閱[sql：自訂記錄集的 Sql 語句（ODBC）](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)，其中描述您可以傳遞給 `Open` 的 sql 語句類型（或部分語句），以及架構對它們執行的動作。

    > [!NOTE]
    >  如果您傳遞的自訂字串不是以 "SELECT" 或 "{CALL" 開始，MFC 會假設它包含資料表名稱。 這也會套用至下一個分項項目。

- 修改精靈寫入至您資料錄集 `GetDefaultSQL` 成員函式的字串。 編輯函式的程式碼來變更其所傳回的內容。 根據預設，精靈會寫入 `GetDefaultSQL` 函式，其會傳回單一資料表名稱。

   您可以讓 `GetDefaultSQL` 將您可以在 *lpszSQL* 參數中傳遞的任何項目傳回至 `Open`。 如果您沒有在 *lpszSQL* 中傳遞自訂 SQL 字串，架構便會使用 `GetDefaultSQL` 傳回的字串。 `GetDefaultSQL` 至少必須傳回單一資料表名稱。 但您可以讓它傳回多個資料表名稱、完整的 **SELECT** 陳述式、ODBC **CALL** 陳述式等。 如需您可以傳遞給*lpszSQL*的內容清單，或傳回 `GetDefaultSQL`，請參閱[SQL：自訂記錄集的 SQL 語句（ODBC）](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。

   如果您正在執行兩個或多個資料表的聯結，請重新撰寫 `GetDefaultSQL` 以自訂用於 SQL **FROM** 子句中的資料表清單。 如需詳細資訊，請參閱[記錄集：執行聯結（ODBC）](../../data/odbc/recordset-performing-a-join-odbc.md)。

- 手動繫結額外的欄位資料成員，也許是根據您在執行階段期間取得之資料來源結構描述的相關資訊。 您會將欄位資料成員加入至資料錄集類別，[RFX](../../data/odbc/record-field-exchange-using-rfx.md) 或大量 RFX 函式呼叫它們至 [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) 或 [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) 成員函式，以及在類別建構函式中初始化資料成員。 如需詳細資訊，請參閱[記錄集：動態地系結資料行（ODBC）](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。

- 覆寫如 `OnSetOptions` 等的資料錄集成員函式，來設定應用程式特定選項或是覆寫預設值。

如果您想要使資料錄集以複雜的 SQL 陳述式為基礎，便需要搭配使用這些自訂技術。 例如，假設您想要使用資料錄集不直接支援的 SQL 子句和關鍵字，或是正在聯結多個資料表。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：資料錄集更新資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[ODBC 基本概念](../../data/odbc/odbc-basics.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[資料錄集：鎖定資料錄 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
