---
title: "資料錄集： 資料錄集選取資料錄的方式 (ODBC) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- recordsets, selecting records
- record selection, ODBC recordsets
- SQL statements, recordset
- records, selecting
- recordsets, constructing SQL statements
- ODBC recordsets, selecting records
ms.assetid: 343a6a91-aa4c-4ef7-b21f-2f2bfd0d3787
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8664c5732c0cdf1042b6af338ea388ab29ab7863
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-how-recordsets-select-records-odbc"></a>資料錄集：資料錄集選取資料錄的方式 (ODBC)
本主題適用於 MFC ODBC 類別。  
  
 本主題說明：  
  
-   [您的角色和您的選項中選取資料錄](#_core_your_options_in_selecting_records)。  
  
-   [資料錄集如何建構其 SQL 陳述式及選取記錄](#_core_how_a_recordset_constructs_its_sql_statement)。  
  
-   [您可以執行來自訂作業選取](#_core_customizing_the_selection)。  
  
 資料錄集選取資料來源的 ODBC 驅動程式透過傳送到驅動程式的 SQL 陳述式的記錄。 傳送 SQL 取決於您如何設計及開啟資料錄集類別。  
  
##  <a name="_core_your_options_in_selecting_records"></a>您的選項中選取資料錄  
 下表顯示您的選項中選取資料錄。  
  
### <a name="how-and-when-you-can-affect-a-recordset"></a>如何及何時可能會影響資料錄集  
  
|當您|您可以|  
|--------------|-------------|  
|宣告您的資料錄集類別與**加入類別**精靈|指定要從選取的資料表。<br /><br /> 指定要包含哪些資料行。<br /><br /> 請參閱[加入 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)。|  
|完成您的資料錄集類別的實作|覆寫成員函式時，例如`OnSetOptions`（進階） 設定應用程式特定選項，或變更預設值。 如果您想要參數化資料錄集，請指定參數資料成員。|  
|建構資料錄集物件 (之前先呼叫**開啟**)|指定搜尋條件 （可能是複合），以用於**其中**篩選資料錄的子句。 請參閱[資料錄集： 篩選資料錄 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)。<br /><br /> 指定排序次序用於**ORDER BY**子句來排序記錄。 請參閱[資料錄集： 排序資料錄 (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)。<br /><br /> 指定參數值的任何參數加入至類別。 請參閱[資料錄集： 參數化資料錄集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。|  

|執行資料錄集的查詢，藉由呼叫**開啟**|指定自訂的 SQL 字串來取代精靈所設定的預設 SQL 字串。 請參閱[crecordset:: Open](../../mfc/reference/crecordset-class.md#open)中*類別程式庫參考*和[SQL： 自訂資料錄集的 SQL 陳述式 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。 |  

|呼叫**Requery**重新查詢資料來源上的最新值資料錄集 |指定新的參數、 篩選或排序。 請參閱[資料錄集： 重新查詢資料錄集 (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)。 |  
  
##  <a name="_core_how_a_recordset_constructs_its_sql_statement"></a>資料錄集如何建構其 SQL 陳述式  
 當您呼叫資料錄集物件的[開啟](../../mfc/reference/crecordset-class.md#open)成員函式，**開啟**建構 SQL 陳述式使用部分或全部的下列元素：  
  
-   **LpszSQL**參數傳遞至**開啟**。 如果沒有**NULL**，此參數會指定自訂 SQL 字串的一部分。 將字串剖析架構。 如果字串是 SQL**選取**陳述式或 ODBC**呼叫**陳述式中，架構會做為資料錄集的 SQL 陳述式中使用的字串。 如果字串開頭不是 「 選取 」 或 「 {呼叫 」，架構會使用所提供來建構 SQL **FROM**子句。  
  
-   所傳回的字串[GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql)。 根據預設，這是您在精靈中，資料錄集為指定之資料表的名稱，但您可以變更函式的傳回。 這個架構會呼叫`GetDefaultSQL`— 如果字串開頭不是 「 選取 」 或 「 {呼叫 」，則會假設為資料表名稱，用來建構 SQL 字串。  
  

-   欄位資料成員的資料錄集，也就是繫結至特定的資料行的資料表。 架構會將記錄的資料行繫結至這些成員，使用它們做為緩衝區的位址。 架構決定資料表資料行，從相互關聯的欄位資料成員[RFX](../../data/odbc/record-field-exchange-using-rfx.md)或 Bulk RFX 函式呼叫中的資料錄集[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)或[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)成員函式。  
  
-   [篩選](../../data/odbc/recordset-filtering-records-odbc.md)資料錄集，如果有的話，包含在[m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter)資料成員。 架構會使用這個字串建構 SQL**其中**子句。  
  
-   [排序](../../data/odbc/recordset-sorting-records-odbc.md)排序資料錄集，如果任何項目，包含在[m_strSort](../../mfc/reference/crecordset-class.md#m_strsort)資料成員。 架構會使用這個字串建構 SQL **ORDER BY**子句。  

  
    > [!TIP]
    >  若要使用 SQL **GROUP BY**子句 (而且可能**HAVING**子句)，將子句附加至您的篩選字串的結尾。  
  
-   任何值[參數資料成員](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)您指定的類別。 只在您呼叫之前，設定參數值**開啟**或**Requery**。 架構會將繫結的參數值"？"的 SQL 字串中的預留位置。 在編譯時期，您可以指定字串的預留位置。 在執行階段，架構會填滿，根據您傳遞的參數值的詳細資料。  
  
 **開啟**建構 SQL**選取**陳述式，從這些因素。 請參閱[自訂選取](#_core_customizing_the_selection)如需架構如何使用這些因素的詳細資訊。  
  
 之後建構陳述式，**開啟**傳送 SQL ODBC 驅動程式管理員 （及 ODBC 資料指標程式庫是否在記憶體中），這將它傳送給 ODBC 驅動程式的特定 DBMS。 驅動程式與資料來源上的選取項目執行 DBMS 通訊，而且擷取第一個資料錄。 架構會將資料錄載入資料錄集的欄位資料成員。  
  
 您可以使用這些技術的組合，以開啟[資料表](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)和來建構查詢是根據[聯結](../../data/odbc/recordset-performing-a-join-odbc.md)多個資料表。 與其他自訂，您可以呼叫[預先定義的查詢](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)（預存程序），選取資料表資料行不知道在設計階段和[繫結](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)資料錄集欄位，或是您可以執行大部分其他資料存取工作。 您無法藉由自訂資料錄集來完成的工作仍可藉由[呼叫 ODBC API 函式](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)或直接執行 SQL 陳述式與[cdatabase:: Executesql](../../mfc/reference/cdatabase-class.md#executesql)。  
  
##  <a name="_core_customizing_the_selection"></a>自訂選取  
 除了提供篩選、 排序順序或參數，您可以採取下列動作來自訂資料錄集的選取項目：  
  
-   將自訂的 SQL 字串中傳遞**lpszSQL**當您呼叫[開啟](../../mfc/reference/crecordset-class.md#open)資料錄集。 您要傳入的任何項目**lpsqSQL**優先於什麼[GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql)成員函式傳回。  
  
     如需詳細資訊，請參閱[SQL： 自訂資料錄集的 SQL 陳述式 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)，用來描述類型的 SQL 陳述式 （或部分陳述式） 中，您可以傳遞給**開啟**和架構使用它們。  
  
    > [!NOTE]
    >  如果您傳遞了自訂字串開頭不是 「 選取 」 或 「 {呼叫 」，MFC 會假設它包含的資料表名稱。 這也適用於下一個項目。  
  
-   Alter 精靈撰寫您的資料錄集中的字串`GetDefaultSQL`成員函式。 編輯變更它所傳回的函式的程式碼。 根據預設，精靈會撰寫`GetDefaultSQL`函式會傳回單一資料表名稱。  
  
     您可以擁有`GetDefaultSQL`傳回任何項目，您可以傳入**lpszSQL**參數**開啟**。 如果您不傳遞自訂的 SQL 字串中**lpszSQL**，架構會使用字串，`GetDefaultSQL`傳回。 最少`GetDefaultSQL`必須傳回單一資料表名稱。 但您可以將它傳回多個資料表名稱，完整**選取**陳述式，ODBC**呼叫**陳述式中，依此類推。 如需您可以傳遞給**lpszSQL** — 或具有`GetDefaultSQL`傳回，請參閱[SQL： 自訂資料錄集的 SQL 陳述式 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。  
  
     如果您正在執行的兩個或多個資料表聯結，請重寫`GetDefaultSQL`自訂的 SQL 中使用的資料表清單**FROM**子句。 如需詳細資訊，請參閱[資料錄集： 執行聯結 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)。  
  

-   以手動方式將額外的欄位資料成員，也許是根據您取得結構描述資訊的資料來源在執行階段繫結。 您將欄位資料成員加入至資料錄集類別[RFX](../../data/odbc/record-field-exchange-using-rfx.md) Bulk RFX 函式呼叫他們或[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)或[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)成員函式，並類別建構函式中的資料成員初始設定。 如需詳細資訊，請參閱[資料錄集： 動態地繫結資料行 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。  
  
-   覆寫資料錄集成員函式，例如`OnSetOptions`、 設定應用程式特定選項或覆寫預設值。  
  
 如果您想要根據複雜的 SQL 陳述式中的資料錄集時，您需要使用這些自訂技術的組合。 例如，也許您想要使用 SQL 子句和關鍵字不直接支援的資料錄集，或可能是您要加入多個資料表。  
  
## <a name="see-also"></a>請參閱  
 [資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [資料錄集： 資料錄集更新資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)   
 [ODBC 基本概念](../../data/odbc/odbc-basics.md)   
 [SQL](../../data/odbc/sql.md)   
 [資料錄集：鎖定資料錄 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)