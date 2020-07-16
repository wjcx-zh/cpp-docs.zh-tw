---
title: SQL：SQL 和 C++ 資料類型 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], SQL vs. C++
- SQL data types [C++]
- SQL [C++], vs. C++ data types
ms.assetid: 066e0070-d4da-435c-9c4b-f7cab3352c86
ms.openlocfilehash: 70796db02f8ff3fcfd67694fb596722664e8f904
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404251"
---
# <a name="sql-sql-and-c-data-types-odbc"></a>SQL：SQL 和 C++ 資料類型 (ODBC)

> [!NOTE]
> 此資訊適用於 MFC ODBC 類別。 如果您要使用 MFC DAO 類別，請參閱 DAO 說明中的 < Microsoft Jet 資料庫引擎 SQL 和 ANSI SQL 的比較主題。

下表將 ANSI SQL 資料類型對應至 c + + 資料類型。 這會增強 ODBC 程式設計[人員參考](/sql/odbc/reference/odbc-programmer-s-reference)檔之附錄 D 中提供的 C 語言資訊。 此嚮導會為您管理大部分的資料類型對應。 如果您不使用 wizard，可以使用對應資訊來協助您手動撰寫欄位交換程式碼。

### <a name="ansi-sql-data-types-mapped-to-c-data-types"></a>對應至 c + + 資料類型的 ANSI SQL 資料類型

|ANSI SQL 資料類型|C++ 資料型別|
|------------------------|---------------------|
|**CHAR**|`CString`|
|**十**|`CString`sha-1|
|**SMALLINT**|**int**|
|**即時**|**float**|
|**介於**|**前提**|
|**FLOAT**|**double**|
|**兩**|**double**|
|**數值**|`CString`sha-1|
|**VARCHAR**|`CString`|
|**LONGVARCHAR**|`CLongBinary`， `CString` 2|
|**一些**|**型**|
|**TINYINT**|**節**|
|**BIGINT**|`CString`sha-1|
|**二**|`CByteArray`|
|**VARBINARY**|`CByteArray`|
|**LONGVARBINARY**|`CLongBinary`， `CByteArray` 3|
|**日期**|`CTime`, `CString`|
|**階段**|`CTime`, `CString`|
|**timestamp**|`CTime`, `CString`|

1. ANSI**十進位**和**數值**對應， `CString` 因為**SQL_C_CHAR**是預設的 ODBC 傳送類型。

2. 當對應到時，預設會截斷超過255個字元的字元資料 `CString` 。 您可以藉由明確地設定的*nMaxLength*引數，來擴充截斷長度 `RFX_Text` 。

3. 當對應到時，預設會截斷超過255個字元的二進位資料 `CByteArray` 。 您可以藉由明確地設定的*nMaxLength*引數，來擴充截斷長度 `RFX_Binary` 。

如果您不是使用 ODBC 資料指標程式庫，當您嘗試使用 Microsoft SQL Server ODBC 驅動程式和 MFC ODBC 資料庫類別來更新兩個或多個長度可變的欄位時，可能會遇到問題。 ODBC 類型， **SQL_LONGVARCHAR**和**SQL_LONGVARBINARY**對應至文字和影像 SQL Server 類型。 `CDBException`如果您在相同的呼叫上更新兩個或多個 long 可變長度的欄位，則會擲回 `CRecordset::Update` 。 因此，請勿使用同時更新多個長資料行 `CRecordset::Update` 。 您可以使用 ODBC API 同時更新多個長資料行 `SQLPutData` 。 您也可以使用 ODBC 資料指標程式庫，但這不建議用於支援資料指標的驅動程式（例如 SQL Server 驅動程式），而且不需要資料指標程式庫。

如果您搭配 MFC ODBC 資料庫類別和 Microsoft SQL Server ODBC 驅動程式來使用 ODBC 資料指標程式庫，則在呼叫之後，如果呼叫，**則可能會發生與的**判斷提示 `CDBException` `CRecordset::Update` `CRecordset::Requery` 。 相反地，請呼叫 `CRecordset::Close` ， `CRecordset::Open` 而不是 `CRecordset::Requery` 。 另一個解決方法是不要使用 ODBC 資料指標程式庫，因為 SQL Server 和 SQL Server ODBC 驅動程式會提供原生的資料指標支援，而不需要 ODBC 資料指標程式庫。

## <a name="see-also"></a>另請參閱

[SQL](../../data/odbc/sql.md)<br/>
[SQL：進行直接的 SQL 呼叫（ODBC）](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
