---
title: 資料錄集： 資料錄集選取資料錄的方式 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- recordsets, selecting records
- record selection, ODBC recordsets
- SQL statements, recordset
- records, selecting
- recordsets, constructing SQL statements
- ODBC recordsets, selecting records
ms.assetid: 343a6a91-aa4c-4ef7-b21f-2f2bfd0d3787
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c8bd84cf7f3dabb837cc7fff345d4ed6c41be44a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051356"
---
# <a name="recordset-how-recordsets-select-records-odbc"></a>資料錄集：資料錄集選取資料錄的方式 (ODBC)

本主題適用於 MFC ODBC 類別。  
  
本主題說明：  
  
- [您的角色和您的選項中選取資料錄](#_core_your_options_in_selecting_records)。  
  
- [資料錄集建構其 SQL 陳述式的方式，並選取記錄](#_core_how_a_recordset_constructs_its_sql_statement)。  
  
- [您可以執行來自訂作業選取](#_core_customizing_the_selection)。  
  
資料錄集傳送給驅動程式的 SQL 陳述式，從資料來源的 ODBC 驅動程式透過選取記錄。 傳送 SQL 取決於您如何設計及開啟資料錄集類別。  
  
##  <a name="_core_your_options_in_selecting_records"></a> 您的選項中選取資料錄  

下表顯示您的選項中選取資料錄。  
  
### <a name="how-and-when-you-can-affect-a-recordset"></a>如何及何時可能會影響資料錄集  
  
|當您|您可以|  
|--------------|-------------|  
|使用您的資料錄集類別的宣告**加入類別**精靈|指定要從選取的資料表。<br /><br /> 指定要包含哪些資料行。<br /><br /> 請參閱[加入 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)。|  
|完成您的資料錄集類別實作|覆寫成員函式時，例如`OnSetOptions`（進階） 來設定應用程式特有的選項，或變更預設值。 如果您想要參數化資料錄集，請指定參數的資料成員。|  
|建構資料錄集物件 (在呼叫之前`Open`)|指定搜尋條件 （可能是複合），以用於**其中**篩選資料錄的子句。 請參閱[資料錄集： 篩選資料錄 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)。<br /><br /> 指定用於排序次序**ORDER BY**子句來排序記錄。 請參閱[資料錄集： 排序資料錄 (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)。<br /><br /> 指定任何參數加入至類別的參數值。 請參閱[資料錄集： 參數化資料錄集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。|  

|執行資料錄集的查詢，藉由呼叫`Open`|指定自訂的 SQL 字串，來取代由精靈所設定的預設 SQL 字串。 請參閱[crecordset:: Open](../../mfc/reference/crecordset-class.md#open)中*類別庫參考*並[SQL： 自訂資料錄集的 SQL 陳述式 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。 |  

|呼叫`Requery`重新查詢資料來源上的最新值的資料錄集 |指定新的參數、 篩選或排序。 請參閱[資料錄集： 重新查詢資料錄集 (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)。 |  
  
##  <a name="_core_how_a_recordset_constructs_its_sql_statement"></a> 資料錄集如何建構它的 SQL 陳述式  

當您呼叫資料錄集物件的[開放](../../mfc/reference/crecordset-class.md#open)成員函式，`Open`建構 SQL 陳述式使用部分或所有下列因素：  
  
- *LpszSQL*參數傳遞至`Open`。 如果不是 NULL，則此參數會指定自訂的 SQL 字串的一部分。 架構會剖析字串。 如果字串為 SQL**選取 **陳述式或 ODBC**呼叫**陳述式，此架構會為資料錄集的 SQL 陳述式中使用的字串。 如果字串開頭不是"SELECT"或"{CALL"，架構會使用什麼提供給建構 SQL **FROM**子句。  
  
- 所傳回的字串[GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql)。 根據預設，這是您在精靈中，資料錄集指定之資料表的名稱，但您可以變更此函數會傳回。 這個架構會呼叫`GetDefaultSQL`— 如果字串開頭不是"SELECT"或"{CALL"，則會假設是資料表的名稱，且用來建構 SQL 字串。  
  

- 欄位資料成員的資料錄集，也就是繫結至特定的資料行的資料表。 架構會將記錄的資料行繫結至這些成員，使用它們作為緩衝區的位址。 架構決定資料表資料行的欄位資料成員的相互關聯[RFX](../../data/odbc/record-field-exchange-using-rfx.md) Bulk RFX 函式呼叫中的資料錄集或[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)或[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)成員函式。  
  
- [篩選條件](../../data/odbc/recordset-filtering-records-odbc.md)資料錄集，如果有的話，包含在[m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter)資料成員。 架構會使用此字串來建構 SQL**其中**子句。  
  
- [排序](../../data/odbc/recordset-sorting-records-odbc.md)排序資料錄集，如果任何項目，包含在[m_strSort](../../mfc/reference/crecordset-class.md#m_strsort)資料成員。 架構會使用此字串來建構 SQL **ORDER BY**子句。  

  
    > [!TIP]
    >  若要使用 SQL **GROUP BY**子句 (而且可能**HAVING**子句)，將子句附加至您的篩選字串的結尾。  
  
- 值的任何[參數的資料成員](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)您指定的類別。 只在您呼叫之前，設定參數值`Open`或`Requery`。 架構會繫結的參數值"？"中的 SQL 字串的預留位置。 在編譯時期，您可以指定字串預留位置。 在執行階段，架構會填滿，根據您傳遞的參數值的詳細資料。  
  
`Open` 建構 SQL**選取**陳述式，從這些要素。 請參閱[自訂選取](#_core_customizing_the_selection)如需架構如何使用這些因素的詳細資訊。  
  
在建構陳述式之後,`Open`傳送 SQL ODBC 驅動程式管理員 （及 ODBC 資料指標程式庫是否在記憶體中），然後傳送至 ODBC 驅動程式針對特定的 DBMS。 驅動程式與資料來源上的選取項目執行 DBMS 進行通訊，並擷取第一筆記錄。 此架構會將記錄載入資料錄集的欄位資料成員。  
  
您可以使用這些技術的組合，以開啟[資料表](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)並建構查詢是根據[聯結](../../data/odbc/recordset-performing-a-join-odbc.md)多個資料表。 您可以使用其他自訂，呼叫[預先定義的查詢](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)（預存程序），選取資料表在設計階段不知道的資料行並[繫結](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)資料錄集欄位，或是您可以執行大部分其他資料存取工作。 您無法完成的自訂資料錄集的工作仍可透過[呼叫 ODBC API 函式](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)或直接執行 SQL 陳述式與[cdatabase:: Executesql](../../mfc/reference/cdatabase-class.md#executesql)。  
  
##  <a name="_core_customizing_the_selection"></a> 自訂選取項目  

除了提供篩選、 排序順序或參數，您可以採取下列動作以自訂資料錄集的選取項目：  
  
- 將自訂的 SQL 字串中傳遞*lpszSQL*當您呼叫[開啟](../../mfc/reference/crecordset-class.md#open)資料錄集。 您所傳遞的任何項目*lpsqSQL*優先於什麼[GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql)成員函式傳回。  
  
     如需詳細資訊，請參閱 < [SQL： 自訂資料錄集的 SQL 陳述式 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)，其中描述類型的 SQL 陳述式 （或部分陳述式） 中，您可以傳遞給`Open`和架構會使用它們。  
  
    > [!NOTE]
    >  如果您傳遞的自訂字串開頭不是"SELECT"或"{CALL"，MFC 會假設它包含資料表名稱。 這也適用於下一個項目符號項目。  
  
- Alter 精靈會將您的資料錄集的字串`GetDefaultSQL`成員函式。 編輯變更它所傳回的函式的程式碼。 根據預設，精靈會將`GetDefaultSQL`函式會傳回單一的資料表名稱。  
  
     您可以擁有`GetDefaultSQL`會傳回任何項目，您可以傳入*lpszSQL*參數來`Open`。 如果您沒有傳遞自訂的 SQL 字串中*lpszSQL*，架構會使用字串的`GetDefaultSQL`傳回。 最少`GetDefaultSQL`必須傳回單一資料表名稱。 但您可以將它傳回多個資料表名稱，完整**選取 **陳述式，ODBC**呼叫**陳述式，依此類推。 如需您可以傳遞給*lpszSQL* — 或有`GetDefaultSQL`傳回，請參閱[SQL： 自訂資料錄集的 SQL 陳述式 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。  
  
     如果您正在執行的兩個或多個資料表聯結，請重寫`GetDefaultSQL`來自訂在 SQL 中使用的資料表清單**FROM**子句。 如需詳細資訊，請參閱 <<c0> [ 資料錄集： 執行聯結 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)。  
  

- 手動將額外的欄位資料成員，也許是根據您取得的相關資訊的結構描述資料來源在執行階段繫結。 資料錄集類別中加入欄位資料成員[RFX](../../data/odbc/record-field-exchange-using-rfx.md)或 Bulk RFX 函式會呼叫這些[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)或是[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)成員函式，和類別建構函式中的資料成員初始設定。 如需詳細資訊，請參閱 <<c0> [ 資料錄集： 動態地繫結資料行 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。  
  
- 覆寫資料錄集成員函式，例如`OnSetOptions`、 設定應用程式特定選項或覆寫預設值。  
  
如果您想要根據複雜的 SQL 陳述式中的資料錄集，您需要使用這些自訂技術的一些組合。 例如，也許您想要使用 SQL 子句時，關鍵字不直接支援的資料錄集，或可能是您要聯結多個資料表。  
  
## <a name="see-also"></a>另請參閱  

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：資料錄集更新資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[ODBC 基本概念](../../data/odbc/odbc-basics.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[資料錄集：鎖定資料錄 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)