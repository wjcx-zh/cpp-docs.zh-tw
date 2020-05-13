---
title: SQL
ms.date: 05/09/2019
helpviewer_keywords:
- database classes [C++], SQL statements
- SQL [C++]
- SQL [C++], ODBC
- ODBC [C++], SQL implementation
ms.assetid: e3923bc4-b317-4e0b-afd8-3cd403eb0faf
ms.openlocfilehash: e5ab824f850b6050e11c10734dd709330af416b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376434"
---
# <a name="sql"></a>SQL

SQL (結構化查詢語言) 使一種與關聯式資料庫進行通訊的方式，可讓您定義、查詢、修改及控制資料。 使用 SQL 語法時，您可以建構根據所指定準則來擷取記錄的陳述式。

> [!NOTE]
> 此資訊適用於 MFC ODBC 類別。 如果您使用的是 MFC DAO 類別，請參閱 DAO　說明中的「Microsoft 資料庫引擎 SQL 與 ANSI SQL 之比較」主題。

SQL 陳述式會以 **CREATE** 或 **SELECT**之類的關鍵字指令動詞作為開頭。 SQL 是一種功能非常強大的語言；一個陳述式即可影響整個資料表。

SQL 有許多版本，每個版本都是以特定的 DBMS 作為開發概念。 MFC 資料庫類別會辨識一組與 X/Open 和 SQL 存取群組通用應用程式環境 (CAE) SQL 草擬規格 (1991) 對應的 SQL 陳述式。 如需有關這些陳述式語法的資訊，請參閱 MSDN Library CD 上 *ODBC SDK ＜程式設計人員參考＞* ** 中的＜附錄 C＞。

本主題將說明：

- [ODBC 與 SQL 之間的關聯性](#_core_open_database_connectivity_.28.odbc.29)。

- [資料庫類別使用的最常見 SQL 關鍵字](#_core_the_database_classes)。

- [資料庫類別如何使用 SQL](#_core_how_the_database_classes_use_sql)。

## <a name="open-database-connectivity-odbc"></a><a name="_core_open_database_connectivity_.28.odbc.29"></a>開放資料庫連線 (ODBC)

這些資料庫類別是以 ODBC 實作的，它會在呼叫層級介面使用 SQL，而不是在程式碼中內嵌 SQL 命令。 ODBC 會使用 SQL 透過 ODBC 驅動程式與[資料來源](../../data/odbc/data-source-odbc.md)進行通訊。 這些驅動程式會解譯 SQL 並視需要轉譯它，以搭配特定資料格式 (例如 Microsoft Access) 使用。 如需有關 ODBC 如何使用 SQL 的詳細資訊，請參閱 MSDN Library CD 上的 [ODBC](../../data/odbc/odbc-basics.md) 和 ODBC ＜程式設計人員參考＞**。

## <a name="database-classes"></a><a name="_core_the_database_classes"></a> 資料庫類別

> [!NOTE]
> Visual Studio 2019 和更新版本中未提供「MFC ODBC 消費者」精靈。 您仍然可以手動建立消費者。

資料庫類別的設計目的是要讓您操作和更新現有[資料來源](../../data/odbc/data-source-odbc.md)中的資料。 [MFC 應用程式精靈](../../mfc/reference/database-support-mfc-application-wizard.md)、[MFC ODBC 消費者精靈](../../mfc/reference/adding-an-mfc-odbc-consumer.md) (透過 [新增類別]**** 來存取) 及資料庫類別會為您建構大部分 SQL 陳述式。

資料庫類別會使用 SQL 中稱為「資料操作語言」(DML) 的部分。 這些命令可讓您使用資料來源的全部或部分、新增新的記錄、編輯記錄，以及刪除記錄。 下表列出最常見的 SQL 關鍵字，以及資料庫類別使用它們的方式。

### <a name="some-common-sql-keywords"></a>一些常見的 SQL 關鍵字

|SQL 關鍵字|精靈和資料庫類別對其使用方式|
|-----------------|---------------------------------------------|
|**選擇**|識別資料來源中要使用的資料表和資料行。|
|**哪裡**|套用可縮小選取範圍的篩選。|
|**排序依據**|在資料錄集套用排序次序。|
|**插入**|將新記錄新增至資料錄集。|
|**刪除**|從資料錄集刪除記錄。|
|**更新**|修改記錄的欄位。|

此外，資料庫類別會辨識 ODBC **CALL** 陳述式，這可供您用來呼叫某些資料來源上的預先定義查詢 (或預存程序)。 ODBC 資料庫驅動程式會解譯這些陳述式，並替代成適合每個 DBMS 的命令。

> [!NOTE]
> 並非所有 DBMS 都支援 **CALL** 陳述式。

如果類別無法辨識 `CRecordset::Open` 中使用者提供的陳述式，系統就會將其解譯為資料表名稱。

有關框架如何構造 SQL 語句的說明,請參閱[記錄集:記錄集如何選擇記錄 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)和[SQL:自訂記錄集的 SQL 語句 (ODBC)。](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)

SQL 資料庫使用的資料類型與 C 和 C++ 中使用的資料類型類似。 有關這些相似性的討論,請參閱[SQL:SQL 和 C++資料類型 (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)。

您可以在 MSDN Library CD 上 *ODBC SDK＜程式設計人員參考＞* ** 中，找到 SQL 的相關詳細資訊，包括支援的 SQL 陳述式清單、資料類型、SQL 核心文法，以及建議的 SQL 相關出版品讀物清單。

## <a name="how-the-database-classes-use-sql"></a><a name="_core_how_the_database_classes_use_sql"></a> 資料庫類別如何使用 SQL

您從資料庫類別衍生的資料錄集會使用 ODBC 來與資料來源進行通訊，而 ODBC 則會藉由傳送 SQL 陳述式，從資料來源擷取記錄。 本主題說明資料庫類別與 SQL 之間的關聯性。

資料錄集會將 SQL 陳述式片段組建成 `CString` 來建構 SQL 陳述式。 此字串會建構成 **SELECT** 陳述式，以傳回一組記錄。

當資料錄集呼叫 ODBC 以將 SQL 陳述式傳送給資料來源時，「ODBC 驅動程式管理員」會將陳述式傳遞給 ODBC 驅動程式，驅動程式則會將其傳遞給基礎 DBMS。 DBMS 會傳回記錄的結果集，而 ODBC 驅動程式則會將記錄傳回給應用程式。 資料庫類別可讓您的程式存取衍生自 `CRecordset` 之型別安全 C++ 類別中的結果集。

下列主題提供有關資料庫類別如何使用 SQL 的詳細資訊：

- [SQL:自訂記錄集的 SQL 語句 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)

- [SQL：SQL 和 C++ 資料類型 (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)

- [SQL：製作直接的 SQL 呼叫 (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)

## <a name="see-also"></a>另請參閱

[開放資料庫連線 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[ODBC 基礎知識](../../data/odbc/odbc-basics.md)
