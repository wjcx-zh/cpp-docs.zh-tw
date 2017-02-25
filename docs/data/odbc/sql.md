---
title: "SQL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "資料庫類別 [C++], SQL 陳述式"
  - "ODBC [C++], SQL 實作"
  - "SQL [C++]"
  - "SQL [C++], ODBC"
ms.assetid: e3923bc4-b317-4e0b-afd8-3cd403eb0faf
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# SQL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

SQL \(結構化查詢語言\) 是一種與可讓您定義的關聯式資料庫進行通訊，查詢，並修改控制項資料。  使用 SQL 語法，您可根據指定的準則來建構取出資料錄的陳述式。  
  
> [!NOTE]
>  本資訊適用於 MFC ODBC 類別。  如果正使用 MFC DAO 類別，請參閱《DAO 說明》中的＜比較 Microsoft Jet Database Engine SQL 與 ANSI SQL＞主題。  
  
 SQL 陳述式會以關鍵字動詞為開頭，例如 **CREATE** 或 **SELECT**。  SQL 是一種非常強大的語言；單一陳述式可影響一整個資料表。  
  
 市面上存在許多 SQL 版本，每一個開發時都針對特定的 DBMS。  MFC 資料庫類別會辨認與 X\/Open 和 SQL Access Group Common Applications Environment \(CAE\) SQL 草擬規格 \(1991\) 一致的 SQL 陳述式集。  如需這些陳述式語法的詳細資訊，請參閱 MSDN Library 光碟片中《ODBC SDK 程式設計人員參考》的附錄 C。  
  
 這個主題說明：  
  
-   [ODBC 和 SQL 之間的關聯性](#_core_open_database_connectivity_.28.odbc.29)  
  
-   [資料庫類別使用的通用 SQL 關鍵字](#_core_the_database_classes)  
  
-   [資料庫類別使用 SQL 的方式](#_core_how_the_database_classes_use_sql)  
  
##  <a name="_core_open_database_connectivity_.28.odbc.29"></a> 開放式資料庫連接 \(ODBC\)  
 資料庫類別使用 ODBC 來實作，它以呼叫層級介面來使用 SQL，而非在程式碼內嵌入 SQL 命令。  ODBC 透過 ODBC 的驅動程式使用 SQL 和[資料來源](../../data/odbc/data-source-odbc.md)溝通。  必要時這些驅動程式會解譯 SQL，並進行轉譯，以便使用如 Microsoft Access 等特定資料庫格式。  如需 ODBC 如何使用 SQL 的詳細資訊，請參閱 [ODBC](../../data/odbc/odbc-basics.md) 和 MSDN Library 光碟片中的《ODBC SDK 程式設計人員參考》。  
  
##  <a name="_core_the_database_classes"></a> 資料庫類別  
 資料庫類別是設計來讓您處理和更新在現有[資料來源](../../data/odbc/data-source-odbc.md)內的資料。  [MFC 應用程式精靈](../../mfc/reference/database-support-mfc-application-wizard.md)、[MFC ODBC 消費者精靈](../../mfc/reference/adding-an-mfc-odbc-consumer.md) \(透過 Add Class 存取\) 和資料庫類別，會為您建構大部分的 SQL 陳述式。  
  
 資料庫類別使用一部分被稱為資料操作語言 \(DML\) 的 SQL。  這些命令讓您得以使用所有的或部分的資料來源、加入新的資料錄、編輯資料錄和刪除資料錄。  下表列出大多數通用的 SQL 關鍵字和資料庫類別使用它們的方法。  
  
### 一些通用的 SQL 關鍵字  
  
|SQL 關鍵字|精靈和資料庫類別使用目的|  
|-------------|------------------|  
|**SELECT**|用以識別要使用資料來源內的哪些資料表和資料行|  
|**WHERE**|用以套用縮小選擇的篩選條件|  
|**ORDER BY**|用以套用資料錄集的排序次序|  
|**INSERT**|用以將新的資料錄加入資料錄集|  
|**DELETE**|用以刪除資料錄集的資料錄|  
|**UPDATE**|用以修改資料錄的欄位|  
  
 另外，資料庫類別會辨認 ODBC **CALL** 陳述式，這些陳述式可供您用來呼叫某些資料來源上的預先定義查詢 \(或預存程序\)。  ODBC 資料庫驅動程式會解譯這些陳述式，並取代適用於每個 DBMS 的命令。  
  
> [!NOTE]
>  並非所有的 DBMS 都支援 **CALL** 陳述式。  
  
 若類別不能在 `CRecordset::Open` 內辨認使用者提供的陳述式，則會將其解譯成資料表名稱。  
  
 如需架構如何建構 SQL 陳述式的說明，請參閱[資料錄集：資料錄集選取資料錄的方式 \(ODBC\)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) 和 [SQL：自訂資料錄集的 SQL 陳述式 \(ODBC\)](../../data/odbc/sql-customizing-your-recordset’s-sql-statement-odbc.md)。  
  
 SQL 資料庫使用類似於 C 和 C\+\+ 所用的資料型別。  如需這些相似之處的討論，請參閱 [SQL：SQL 和 C\+\+ 資料型別 \(ODBC\)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)。  
  
 您可在 MSDN Library 光碟片中的《ODBC SDK 程式設計人員參考》中找到 SQL 的詳細資訊，包括所支援的 SQL 陳述式清單、資料型別、SQL 核心文法和 SQL 的建議發行物閱讀清單。  
  
##  <a name="_core_how_the_database_classes_use_sql"></a> 資料庫類別使用 SQL 的方式  
 您從資料庫類別取得的資料錄集是使用 ODBC 與資料來源進行溝通，而 ODBC 是藉由傳送 SQL 陳述式從資料來源擷取資料錄。  這個主題會說明資料庫類別和 SQL 之間的關聯性。  
  
 資料錄集藉由將 SQL 陳述式片段建構於 `CString` 中，以建構 SQL 陳述式。  此字串會建構成傳回資料錄集的 **SELECT** 陳述式。  
  
 當資料錄集呼叫 ODBC 傳送 SQL 陳述式至資料來源時，ODBC 驅動程式管理員會將陳述式傳遞至 ODBC 驅動程式，驅動程式再將陳述式傳送至基礎 DBMS。  DBMS 傳回資料錄的結果集，而 ODBC 驅動程式可將資料錄傳回至應用程式。  資料庫類別讓您的程式可以存取衍生自 `CRecordset` 的型別安全 C\+\+ 類別中的結果集。  
  
 下列主題提供資料庫類別如何使用 SQL 的詳細資訊：  
  
-   [SQL：自訂資料錄集的 SQL 陳述式 \(ODBC\)](../../data/odbc/sql-customizing-your-recordset’s-sql-statement-odbc.md)  
  
-   [SQL：SQL 和 C\+\+ 資料型別 \(ODBC\)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)  
  
-   [SQL：製作直接的 SQL 呼叫 \(ODBC\)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)  
  
## 請參閱  
 [開放式資料庫連接 \(ODBC\)](../../data/odbc/open-database-connectivity-odbc.md)   
 [ODBC 的基本概念](../../data/odbc/odbc-basics.md)