---
title: SQL
ms.date: 11/04/2016
helpviewer_keywords:
- database classes [C++], SQL statements
- SQL [C++]
- SQL [C++], ODBC
- ODBC [C++], SQL implementation
ms.assetid: e3923bc4-b317-4e0b-afd8-3cd403eb0faf
ms.openlocfilehash: 8f93d97530068695359273b523e7d2ae46de01cb
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037853"
---
# <a name="sql"></a>SQL

SQL （結構式查詢語言） 是用來與關聯式資料庫，可讓您定義、 查詢、 修改和控制的資料。 您可以使用 SQL 語法，來建構陳述式，它會擷取記錄，根據您指定的準則。

> [!NOTE]
>  這項資訊適用於 MFC ODBC 類別。 如果您使用 MFC DAO 類別時，請參閱主題比較 Microsoft Jet 資料庫引擎 SQL 和 DAO [說明] 中的 ANSI SQL。

SQL 陳述式開頭關鍵字動詞命令這類**CREATE**或是**選取**。 SQL 是非常強大的語言;單一陳述式可能會影響整個資料表。

許多版本的 SQL 存在，每個開發特定 DBMS 記住。 MFC 資料庫類別識別一組對應至 X / Open 的 SQL 陳述式和 SQL 存取群組通用應用程式的環境 (CAE) SQL 草稿規格 (1991)。 這些陳述式之語法的詳細資訊，請參閱中的 < 附錄 C *ODBC SDK* *程式設計人員參考*MSDN Library CD 上。

本主題說明：

- [ODBC 和 SQL 之間的關聯性](#_core_open_database_connectivity_.28.odbc.29)。

- [資料庫類別使用的最常見的 SQL 關鍵字](#_core_the_database_classes)。

- [資料庫類別如何使用 SQL](#_core_how_the_database_classes_use_sql)。

##  <a name="_core_open_database_connectivity_.28.odbc.29"></a> 開放式資料庫連接 (ODBC)

資料庫類別會實作使用 ODBC 時，它會使用呼叫層級介面，而不是在程式碼中嵌入 SQL 命令中的 SQL。 ODBC 用來與通訊的 SQL[資料來源](../../data/odbc/data-source-odbc.md)透過 ODBC 驅動程式。 這些驅動程式解譯 SQL，並轉譯，如有必要，與特定資料庫格式，例如 Microsoft Access 搭配使用。 如需 ODBC SQL 的使用方式的詳細資訊，請參閱[ODBC](../../data/odbc/odbc-basics.md)和 ODBC SDK*程式設計人員參考*MSDN Library CD 上。

##  <a name="_core_the_database_classes"></a> 資料庫類別

資料庫類別設計來讓您處理和更新資料中的現有[資料來源](../../data/odbc/data-source-odbc.md)。 [MFC 應用程式精靈](../../mfc/reference/database-support-mfc-application-wizard.md)，則[MFC ODBC 消費者精靈](../../mfc/reference/adding-an-mfc-odbc-consumer.md)(經由**加入類別**)，和資料庫類別為您建構大部分的 SQL 陳述式。

資料庫類別使用 SQL 資料操作語言 (DML) 的已知的部分。 這些命令可讓您使用全部或部分資料來源、 新增新的記錄、 編輯記錄，以及刪除記錄。 下表列出最常見的 SQL 關鍵字和資料庫類別使用它們的方法。

### <a name="some-common-sql-keywords"></a>一些常見的 SQL 關鍵字

|SQL 關鍵字|精靈和資料庫類別使用它|
|-----------------|---------------------------------------------|
|**SELECT**|若要識別哪些資料表和資料來源中的資料行所要使用。|
|**WHERE**|若要套用篩選，以縮小選取範圍。|
|**ORDER BY**|若要套用的排序次序在資料錄集。|
|**INSERT**|若要新增至資料錄集的記錄。|
|**DELETE**|若要刪除資料錄集的記錄。|
|**UPDATE**|若要修改記錄的欄位。|

此外，資料庫類別會辨認 ODBC**呼叫**陳述式，您可以使用某些資料來源上呼叫預先定義的查詢 （或預存程序）。 ODBC 資料庫驅動程式會解譯這些陳述式，並換成適用於每個 DBMS 命令。

> [!NOTE]
>  並非所有的 Dbms 支援**呼叫**陳述式。

如果類別無法辨識的使用者提供陳述式`CRecordset::Open`，它會解譯為資料表名稱。

如需此架構如何建構 SQL 陳述式的說明，請參閱[資料錄集：資料錄集選取資料錄 (ODBC) 的方式](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)和[SQL:自訂資料錄集的 SQL 陳述式 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。

SQL database 會使用類似 C 中所使用的資料型別和C++。 如需這些相似之處的討論，請參閱[SQL:SQL 和C++資料類型 (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)。

您可以找到 SQL，包括一份支援的 SQL 陳述式、 資料類型、 SQL 核心文法，以及建議的發行集，SQL，關於讀取清單中的詳細資訊*ODBC SDK* *程式設計人員參考* MSDN Library CD 上。

##  <a name="_core_how_the_database_classes_use_sql"></a> 資料庫類別如何使用 SQL

您從資料庫類別衍生的資料錄集使用 ODBC 來與資料來源、 通訊和 ODBC 資料來源擷取記錄傳送 SQL 陳述式。 本主題說明資料庫類別與 SQL 之間的關聯性。

資料錄集建構 SQL 陳述式，藉由建置成 SQL 陳述式的項目`CString`。 字串會建構為**選取**陳述式，它會傳回一組記錄。

當資料錄集呼叫 ODBC SQL 陳述式傳送到資料來源時，ODBC 驅動程式管理員會將陳述式傳遞至 ODBC 驅動程式和驅動程式將它傳送至基礎 DBMS。 DBMS 傳回結果集的記錄，以和 ODBC 驅動程式傳回給應用程式的記錄。 資料庫類別可讓您存取的結果集類型安全的程式C++類別衍生自`CRecordset`。

下列主題提供有關資料庫類別如何使用 SQL 的詳細資訊：

- [SQL:自訂資料錄集的 SQL 陳述式 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)

- [SQL:SQL 和C++資料類型 (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)

- [SQL:製作直接的 SQL 呼叫 (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)

## <a name="see-also"></a>另請參閱

[開放式資料庫連接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[ODBC 基本概念](../../data/odbc/odbc-basics.md)