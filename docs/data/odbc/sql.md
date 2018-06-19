---
title: SQL |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- database classes [C++], SQL statements
- SQL [C++]
- SQL [C++], ODBC
- ODBC [C++], SQL implementation
ms.assetid: e3923bc4-b317-4e0b-afd8-3cd403eb0faf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: df1563d8bb3d53bb405fbb0d89b2b26cc964bd44
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33093239"
---
# <a name="sql"></a>SQL
SQL （結構化查詢語言） 是定義、 查詢、 修改和控制的資料與關聯式資料庫，可讓進行通訊的方式。 您可以使用 SQL 語法，來建構會擷取記錄，根據您指定的準則的陳述式。  
  
> [!NOTE]
>  這項資訊適用於 MFC ODBC 類別。 如果您使用 MFC DAO 類別時，請參閱本主題比較 Microsoft Jet 資料庫引擎 SQL 及其 DAO [說明] 中的 ANSI SQL。  
  
 SQL 陳述式開頭關鍵字動詞例如**建立**或**選取**。 SQL 是非常強大的語言。在單一陳述式可能會影響整個資料表。  
  
 許多版本的 SQL 存在，請使用特定 DBMS 記住每個開發。 MFC 資料庫類別辨識一組對應到 X / Open 的 SQL 陳述式和 SQL 存取群組通用應用程式的環境 (CAE) SQL 草稿規格 (1991)。 這些陳述式之語法的詳細資訊，請參閱在 < 附錄 C *ODBC SDK* *程式設計人員參考*MSDN Library CD 上。  
  
 本主題說明：  
  
-   [ODBC 與 SQL 之間的關聯性](#_core_open_database_connectivity_.28.odbc.29)。  
  
-   [資料庫類別使用的最常見 SQL 關鍵字](#_core_the_database_classes)。  
  
-   [資料庫類別如何使用 SQL](#_core_how_the_database_classes_use_sql)。  
  
##  <a name="_core_open_database_connectivity_.28.odbc.29"></a> 開放式資料庫連接 (ODBC)  
 資料庫類別會實作使用 ODBC 時，它會使用 SQL 呼叫層級介面，而非程式碼中嵌入 SQL 命令。 ODBC 用來與通訊的 SQL[資料來源](../../data/odbc/data-source-odbc.md)透過 ODBC 驅動程式。 這些驅動程式解譯 SQL，翻譯，如有必要，特定資料庫格式，例如 Microsoft Access 搭配使用。 如需 ODBC SQL 的使用方式的詳細資訊，請參閱[ODBC](../../data/odbc/odbc-basics.md)和 ODBC SDK*程式設計人員參考*MSDN Library CD 上。  
  
##  <a name="_core_the_database_classes"></a> 資料庫類別  
 資料庫類別的設計是可讓您管理和更新中的現有資料[資料來源](../../data/odbc/data-source-odbc.md)。 [MFC 應用程式精靈](../../mfc/reference/database-support-mfc-application-wizard.md)、 [MFC ODBC 消費者精靈](../../mfc/reference/adding-an-mfc-odbc-consumer.md)(透過存取**加入類別**)，和資料庫類別為您建構大部分的 SQL 陳述式。  
  
 資料庫類別使用 SQL 資料操作語言 (DML) 的已知的一部分。 這些命令可讓您使用的全部或部分資料來源、 新增新的記錄、 編輯記錄，以及刪除記錄。 下表列出最常見的 SQL 關鍵字和資料庫類別使用它們的方法。  
  
### <a name="some-common-sql-keywords"></a>某些常見的 SQL 關鍵字  
  
|SQL 關鍵字|精靈和資料庫類別使用|  
|-----------------|---------------------------------------------|  
|**SELECT**|若要識別哪些資料表和資料來源中的資料行的使用。|  
|**WHERE**|若要套用篩選，以縮小選取範圍。|  
|**ORDER BY**|將排序順序套用至資料錄集。|  
|**插入**|若要將新記錄新增至資料錄集。|  
|**刪除**|若要刪除資料錄集的記錄。|  
|**更新**|若要修改記錄的欄位。|  
  
 此外，資料庫類別辨識 ODBC**呼叫**陳述式，您可以使用某些資料來源上呼叫預先定義的查詢 （或預存程序）。 ODBC 資料庫驅動程式會解譯這些陳述式，並換成適用於每個 DBMS 命令。  
  
> [!NOTE]
>  並非所有的 Dbms 支援**呼叫**陳述式。  
  
 如果類別不能辨識中的使用者提供陳述式`CRecordset::Open`，將它解譯為資料表名稱。  
  
 如需架構如何建構 SQL 陳述式的說明，請參閱[資料錄集： 如何資料錄集選取資料錄 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)和[SQL： 自訂資料錄集的 SQL 陳述式 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。  
  
 SQL 資料庫使用資料類型類似於 C 和 c + + 中使用。 如需這些相似之處的討論，請參閱[SQL: SQL 和 c + + 資料類型 (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)。  
  
 您可以找到 SQL，包括支援的 SQL 陳述式、 資料類型、 SQL 核心文法，以及有關 SQL，建議使用發行集的讀取清單的清單中的詳細資訊*ODBC SDK* *程式設計人員參考* MSDN Library CD 上。  
  
##  <a name="_core_how_the_database_classes_use_sql"></a> 資料庫類別如何使用 SQL  
 您從資料庫類別衍生的資料錄集來進行通訊與資料來源，使用 ODBC 和 ODBC 資料來源擷取記錄傳送 SQL 陳述式。 本主題說明資料庫類別與 SQL 之間的關聯性。  
  
 資料錄集來建置的 SQL 陳述式片段建構 SQL 陳述式`CString`。 字串建構為**選取**陳述式會傳回一組記錄。  
  
 當資料錄集呼叫 ODBC SQL 陳述式傳送到資料來源時，ODBC 驅動程式管理員會將陳述式傳遞至 ODBC 驅動程式和驅動程式將它傳送至基礎 DBMS。 DBMS 傳回結果集的記錄，以及 ODBC 驅動程式傳回資料錄應用程式。 資料庫類別可讓您程式的存取權的結果集類型安全的 c + + 類別衍生自`CRecordset`。  
  
 下列主題提供有關資料庫類別如何使用 SQL 的詳細資訊：  
  
-   [SQL： 自訂資料錄集的 SQL 陳述式 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)  
  
-   [SQL：SQL 和 C++ 資料類型 (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)  
  
-   [SQL：製作直接的 SQL 呼叫 (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)  
  
## <a name="see-also"></a>另請參閱  
 [開放式資料庫連接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)   
 [ODBC 基本概念](../../data/odbc/odbc-basics.md)