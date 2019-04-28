---
title: SQL:SQL 和C++資料類型 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], SQL vs. C++
- SQL data types [C++]
- SQL [C++], vs. C++ data types
ms.assetid: 066e0070-d4da-435c-9c4b-f7cab3352c86
ms.openlocfilehash: 3efa36342b7d16968113acd818a7a1386e4cefcc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62329879"
---
# <a name="sql-sql-and-c-data-types-odbc"></a>SQL:SQL 和C++資料類型 (ODBC)

> [!NOTE]
>  這項資訊適用於 MFC ODBC 類別。 如果您使用 MFC DAO 類別時，請參閱 「 比較 Microsoft Jet 資料庫引擎 SQL 和 ANSI SQL"DAO [說明] 中的主題。

下表對應至的 ANSI SQL 資料類型C++資料類型。 這可增強的附錄 D 中提供的 C 語言資訊*ODBC SDK* *程式設計人員參考*MSDN Library CD 上。 精靈會管理為您的大部分資料類型對應。 如果您不使用精靈，您可以使用對應的資訊可協助您以手動方式撰寫欄位交換程式碼。

### <a name="ansi-sql-data-types-mapped-to-c-data-types"></a>ANSI SQL 資料類型對應至C++資料類型

|ANSI SQL 資料類型|C++ 資料型別|
|------------------------|---------------------|
|**CHAR**|`CString`|
|**DECIMAL**|`CString` 1|
|**SMALLINT**|**int**|
|**REAL**|**float**|
|**INTEGER**|**long**|
|**FLOAT**|**double**|
|**DOUBLE**|**double**|
|**NUMERIC**|`CString` 1|
|**VARCHAR**|`CString`|
|**LONGVARCHAR**|`CLongBinary`, `CString` 2|
|**BIT**|**BOOL**|
|**TINYINT**|**BYTE**|
|**BIGINT**|`CString` 1|
|**二進位**|`CByteArray`|
|**VARBINARY**|`CByteArray`|
|**LONGVARBINARY**|`CLongBinary`, `CByteArray` 3|
|**DATE**|`CTime`、 `CString`|
|**TIME**|`CTime`、 `CString`|
|**TIMESTAMP**|`CTime`、 `CString`|

1. ANSI**十進位**並**數值**對應至`CString`因為**SQL_C_CHAR**是預設 ODBC 傳輸類型。

2. 當對應至的預設值來截斷超過 255 個字元的字元資料`CString`。 您可以藉由明確將擴充截斷長度*nMaxLength*引數`RFX_Text`。

3. 當對應至的預設值來截斷超過 255 個字元的二進位資料`CByteArray`。 您可以藉由明確將擴充截斷長度*nMaxLength*引數`RFX_Binary`。

如果您不會使用 ODBC 資料指標程式庫，您可能會遇到問題，在嘗試更新兩個或更多使用 Microsoft SQL Server ODBC 驅動程式和 MFC ODBC 資料庫類別的長時間的可變長度欄位。 ODBC 型別**SQL_LONGVARCHAR**並**SQL_LONGVARBINARY**、 對應至文字和映像 SQL Server 型別。 A`CDBException`如果您更新兩個或多個長時間的可變長度欄位相同的呼叫會擲回`CRecordset::Update`。 因此，不會更新同時使用多長的資料行`CRecordset::Update`。 您可以使用 ODBC API，同時更新多長的資料行`SQLPutData`。 您也可以使用 ODBC 資料指標程式庫，但這不建議用於驅動程式，如 SQL Server 驅動程式支援資料指標，而不需要資料指標程式庫。

如果您使用 MFC ODBC 資料庫類別和 Microsoft SQL Server ODBC 驅動程式，使用 ODBC 資料指標程式庫**ASSERT**可能會發生連同`CDBException`如果呼叫`CRecordset::Update`在呼叫`CRecordset::Requery`。 請改為呼叫`CRecordset::Close`並`CRecordset::Open`而非`CRecordset::Requery`。 另一個解決方案是不使用 ODBC 資料指標程式庫，因為 SQL Server 和 SQL Server ODBC 驅動程式提供原生支援資料指標的原生並不需要 ODBC 資料指標程式庫。

## <a name="see-also"></a>另請參閱

[SQL](../../data/odbc/sql.md)<br/>
[SQL：製作直接的 SQL 呼叫 (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)