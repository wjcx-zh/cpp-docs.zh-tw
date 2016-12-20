---
title: "資料錄集：資料錄集選取資料錄的方式 (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ODBC 資料錄集, 選取資料錄"
  - "資料錄選取, ODBC 資料錄集"
  - "資料錄, 選取"
  - "資料錄集, 建構 SQL 陳述式"
  - "資料錄集, 選取資料錄"
  - "SQL 陳述式, 資料錄集"
ms.assetid: 343a6a91-aa4c-4ef7-b21f-2f2bfd0d3787
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 資料錄集：資料錄集選取資料錄的方式 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件適用於 MFC ODBC 類別。  
  
 這個主題說明：  
  
-   [您在選取資料錄時的角色和選項](#_core_your_options_in_selecting_records)。  
  
-   [資料錄集建構其 SQL 陳述式和選取資料錄的方式](#_core_how_a_recordset_constructs_its_sql_statement)。  
  
-   [自訂選取的方式](#_core_customizing_the_selection)。  
  
 資料錄集藉由將 SQL 陳述式送至 ODBC 驅動程式，透過驅動程式選取資料來源中的資料錄。  送出的 SQL 將根據您設計和開啟資料錄集類別的方式，而有所不同。  
  
##  <a name="_core_your_options_in_selecting_records"></a> 選取資料錄時的選項  
 下表說明您在選取資料錄時的選項。  
  
### 您如何及何時可影響資料錄集  
  
|當您|您可以|  
|--------|---------|  
|使用 \[加入類別\] 精靈來宣告您的資料錄集類別|指定進行選取的資料表。<br /><br /> 指定要包括哪些資料行。<br /><br /> 請參閱[加入 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)。|  
|完成您的資料錄集類別實作|覆寫例如 `OnSetOptions` \(進階的\) 等成員函式來設定特定應用程式選項或變更為預設值。  若您想要一個參數型的資料錄集，則指定參數資料成員。|  
|建構資料錄集物件 \(在您呼叫 **Open** 之前\)|在 **WHERE** 子句內指定一個搜尋條件 \(可能是複合的\)，以便用來篩選資料錄。  請參閱[資料錄集：篩選資料錄 \(ODBC\)](../../data/odbc/recordset-filtering-records-odbc.md)。<br /><br /> 在 **ORDER BY** 子句內指定一個排序順序，以便排序資料錄。  請參閱[資料錄集：排序資料錄 \(ODBC\)](../../data/odbc/recordset-sorting-records-odbc.md)。<br /><br /> 為任何您加到類別中的參數指定參數值。  請參閱[資料錄集：參數化資料錄集 \(ODBC\)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。|  
|呼叫 **Open** 來執行資料錄集的查詢|指定自訂的 SQL 字串來取代精靈所設定的預設 SQL 字串。  請參閱《類別庫參考》內的 [CRecordset::Open](../Topic/CRecordset::Open.md) 和 [SQL：自訂資料錄集的 SQL 陳述式 \(ODBC\)](../../data/odbc/sql-customizing-your-recordset’s-sql-statement-odbc.md)。|  
|呼叫 **Requery**，使用資料來源上的最新值來重新查詢資料錄集|指定新的參數、篩選條件或排序。  請參閱[資料錄集：重新查詢資料錄集 \(ODBC\)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)。|  
  
##  <a name="_core_how_a_recordset_constructs_its_sql_statement"></a> 資料錄集建構其 SQL 陳述式的方式  
 當您呼叫資料錄集物件的 [Open](../Topic/CRecordset::Open.md) 成員函式時，**Open** 會使用下列某些或所有因素來建構 SQL 陳述式：  
  
-   傳遞至 **Open** 的 **lpszSQL** 參數。  若不是 **NULL**，此參數便會指定自訂的 SQL 字串或字串的一部分。  架構會剖析此字串。  若該字串是一個 SQL **SELECT** 陳述式或一個 ODBC **CALL** 陳述式，架構會使用該字串做為資料錄集的 SQL 陳述式。  若該字串不是以 "SELECT" 或 "{CALL" 開頭，架構會使用所提供的項目來建構 SQL **FROM** 子句。  
  
-   [GetDefaultSQL](../Topic/CRecordset::GetDefaultSQL.md) 傳回的字串。  預設情形下，這會是您在精靈中指定給資料錄集的資料表名稱，但您可變更此函式傳回的字串。  架構會呼叫 `GetDefaultSQL`，如果該字串不是以 "SELECT" 或 "{CALL" 開頭，它會假設該字串為用來建構 SQL 字串的資料表名稱。  
  
-   資料錄集的欄位資料成員，此成員是用來繫結資料表內特定的資料行。  架構會將資料錄資料行繫結至這些成員的位置，把它們當做緩衝區使用。  架構會從資料錄集的 [DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md) 或 [DoBulkFieldExchange](../Topic/CRecordset::DoBulkFieldExchange.md) 成員函式內的 [RFX](../../data/odbc/record-field-exchange-using-rfx.md) 或 Bulk RFX 函式呼叫，來決定欄位資料成員與資料表資料行間的相互關聯。  
  
-   資料錄集的[篩選條件](../../data/odbc/recordset-filtering-records-odbc.md) \(如果有的話\) 會包含在 [m\_strFilter](../Topic/CRecordset::m_strFilter.md) 資料成員內。  架構會使用此字串來建構 SQL **WHERE** 子句。  
  
-   資料錄集的[排序](../../data/odbc/recordset-sorting-records-odbc.md)順序 \(如果有的話\) 會包含在 [m\_strSort](../Topic/CRecordset::m_strSort.md) 資料成員內。  架構會使用此字串來建構 SQL **ORDER BY** 子句。  
  
    > [!TIP]
    >  若要使用 SQL **GROUP BY** 子句 \(可能是 **HAVING** 子句\)，請將該子句附加至您的篩選字串結尾。  
  
-   您為該類別所指定的任何[參數資料成員](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)值。  您只能在呼叫 **Open** 或 **Requery** 前設定參數值。  架構會將參數值繫結至 SQL 字串內的 "?" 替代符號。  您可以在編譯時間中，使用替代符號來指定該字串。  在執行階段時，架構會根據您傳入的參數值來填入詳細資訊。  
  
 **Open** 會從這些因素來建構 SQL **SELECT** 陳述式。  如需架構如何使用這些因素的詳細資訊，請參閱[自訂選取](#_core_customizing_the_selection)。  
  
 在建構陳述式後，**Open** 會將此 SQL 傳送至 ODBC 驅動程式管理員 \(如果 ODBC 資料指標程式庫還在記憶體中的話\)，它會將 SQL 傳給特定 DBMS 的 ODBC 驅動程式。  驅動程式會與 DBMS 溝通，完成資料來源上的選取，並擷取第一筆資料錄。  架構會將資料錄載入資料錄集的欄位資料成員中。  
  
 您可使用這些技術的組合來開啟[資料表](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)，並根據多個資料表的[聯結](../../data/odbc/recordset-performing-a-join-odbc.md)來建構查詢。  有了其他的自訂項目，您可以呼叫[預先定義查詢](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md) \(預存程序\)、選取設計階段時未知的資料表資料行，以及將它們[繫結](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)至資料錄集欄位，或執行大多數其他的資料存取工作。  您不能自訂資料錄集來完成的工作仍可藉由[呼叫 ODBC API 函式](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)，或直接使用 [CDatabase::ExecuteSQL](../Topic/CDatabase::ExecuteSQL.md) 執行 SQL 陳述式來完成。  
  
##  <a name="_core_customizing_the_selection"></a> 自訂選取  
 您除了可以提供篩選條件、排序順序或參數外，還可採取下列動作來自訂您的資料錄集選取：  
  
-   當為資料錄集呼叫 [Open](../Topic/CRecordset::Open.md) 時，請在 **lpszSQL** 內傳遞自訂的 SQL 字串。  您在 **lpsqSQL** 內傳遞的任何字串都會比 [GetDefaultSQL](../Topic/CRecordset::GetDefaultSQL.md) 成員函式所傳回的還要優先。  
  
     如需詳細資訊，請參閱 [SQL：自訂資料錄集的 SQL 陳述式 \(ODBC\)](../../data/odbc/sql-customizing-your-recordset’s-sql-statement-odbc.md)，會說明您可以傳遞至 **Open** 的 SQL 陳述式類型 \(或部分陳述式\)，以及架構能使用這些類型所做的事。  
  
    > [!NOTE]
    >  若您所傳入的自訂字串不是以 "SELECT" 或 "{CALL" 開頭，MFC 會假設字串包含有資料表名稱。  這也適用於下一個項目符號項目。  
  
-   改變精靈在資料錄集的 `GetDefaultSQL` 成員函式中編寫的字串。  編輯函式的程式碼以變更傳回的字串。  預設地，精靈會編寫一個傳回單一資料表名稱的 `GetDefaultSQL` 函式。  
  
     您可讓 `GetDefaultSQL` 傳回任何您傳給 **Open** 的 **lpszSQL** 參數。  如果沒有在 **lpszSQL** 內傳遞自訂的 SQL 字串，架構會使用 `GetDefaultSQL` 傳回的字串。  `GetDefaultSQL` 至少必須傳回單一資料表名稱。  但您可讓它傳回多個資料表名稱、一個完整的 **SELECT** 陳述式、一個 ODBC **CALL** 陳述式等等。  如需可以傳遞什麼內容至 **lpszSQL** 或可以讓 `GetDefaultSQL` 傳回什麼內容的清單，請參閱 [SQL：自訂資料錄集的 SQL 陳述式 \(ODBC\)](../../data/odbc/sql-customizing-your-recordset’s-sql-statement-odbc.md)。  
  
     若您正在執行兩個或多個資料表的聯結，請改寫 `GetDefaultSQL` 以自訂用於 SQL **FROM** 子句的資料表清單。  如需詳細資訊，請參閱[資料錄集：執行聯結 \(ODBC\)](../../data/odbc/recordset-performing-a-join-odbc.md)。  
  
-   手動繫結附加的欄位資料成員，也許是根據您在執行階段所取得的資料來源結構描述資料進行繫結。  您加入欄位資料成員至資料錄集類別、在 [DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md) 或 [DoBulkFieldExchange](../Topic/CRecordset::DoBulkFieldExchange.md) 成員函式內加入 [RFX](../../data/odbc/record-field-exchange-using-rfx.md) 或 Bulk RFX 函式呼叫，以及類別建構函式 \(Constructor\) 內資料成員的初始化。  如需詳細資訊，請參閱[資料錄集：動態地繫結資料行 \(ODBC\)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。  
  
-   覆寫例如 `OnSetOptions` 的資料錄集成員函式，以設定特定應用程式選項或覆寫預設值。  
  
 如果您想要根據複雜的 SQL 陳述式來建構資料錄集，會需要使用這些自訂技術的某些組合。  例如，也許您想要使用資料錄集無法直接支援的 SQL 子句和關鍵字，或是正在聯結多個資料表。  
  
## 請參閱  
 [資料錄集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [資料錄集：資料錄集更新資料錄的方式 \(ODBC\)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)   
 [ODBC 的基本概念](../../data/odbc/odbc-basics.md)   
 [SQL](../../data/odbc/sql.md)   
 [資料錄集：鎖定資料錄 \(ODBC\)](../../data/odbc/recordset-locking-records-odbc.md)