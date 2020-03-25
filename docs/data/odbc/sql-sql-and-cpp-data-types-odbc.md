---
title: SQL：SQL 和 C++ 資料類型 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], SQL vs. C++
- SQL data types [C++]
- SQL [C++], vs. C++ data types
ms.assetid: 066e0070-d4da-435c-9c4b-f7cab3352c86
ms.openlocfilehash: 1c1ce908b5c8d345906d49adc79e322225ed49f5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212611"
---
# <a name="sql-sql-and-c-data-types-odbc"></a>SQL：SQL 和 C++ 資料類型 (ODBC)

> [!NOTE]
>  此資訊適用於 MFC ODBC 類別。 如果您要使用 MFC DAO 類別，請參閱 DAO 說明中的 < Microsoft Jet 資料庫引擎 SQL 和 ANSI SQL 的比較主題。

下表將 ANSI SQL 資料類型對應至C++資料類型。 這會增強 MSDN Library CD 上的*ODBC SDK*程式設計*人員參考*附錄 D 所提供的 C 語言資訊。 此嚮導會為您管理大部分的資料類型對應。 如果您不使用 wizard，可以使用對應資訊來協助您手動撰寫欄位交換程式碼。

### <a name="ansi-sql-data-types-mapped-to-c-data-types"></a>對應至資料類型的C++ ANSI SQL 資料類型

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
|**LONGVARCHAR**|`CLongBinary`，`CString` 2|
|**BIT**|**BOOL**|
|**TINYINT**|**BYTE**|
|**BIGINT**|`CString` 1|
|**二**|`CByteArray`|
|**VARBINARY**|`CByteArray`|
|**LONGVARBINARY**|`CLongBinary`，`CByteArray` 3|
|**DATE**|`CTime`, `CString`|
|**TIME**|`CTime`, `CString`|
|**TIMESTAMP**|`CTime`, `CString`|

1. 要 `CString` 的 ANSI**十進位**和**數值**對應，因為**SQL_C_CHAR**是預設的 ODBC 傳輸類型。

2. 當對應至 `CString`時，預設會截斷超過255個字元的字元資料。 您可以藉由明確地設定 `RFX_Text`的*nMaxLength*引數，來擴充截斷長度。

3. 當對應至 `CByteArray`時，預設會截斷超過255個字元的二進位資料。 您可以藉由明確地設定 `RFX_Binary`的*nMaxLength*引數，來擴充截斷長度。

如果您不是使用 ODBC 資料指標程式庫，當您嘗試使用 Microsoft SQL Server ODBC 驅動程式和 MFC ODBC 資料庫類別來更新兩個或多個長度可變的欄位時，可能會遇到問題。 ODBC 類型， **SQL_LONGVARCHAR**和**SQL_LONGVARBINARY**對應至文字和影像 SQL Server 類型。 如果您在 `CRecordset::Update`的相同呼叫上更新兩個或多個長可變長度的欄位，則會擲回 `CDBException`。 因此，請勿同時使用 `CRecordset::Update`來更新多個長資料行。 您可以使用 ODBC API `SQLPutData`，同時更新多個長資料行。 您也可以使用 ODBC 資料指標程式庫，但這不建議用於支援資料指標的驅動程式（例如 SQL Server 驅動程式），而且不需要資料指標程式庫。

如果您使用具有 MFC ODBC 資料庫類別和 Microsoft SQL Server ODBC 驅動程式的 ODBC 資料指標程式庫，則在呼叫 `CRecordset::Update` 之後，如果呼叫 `CRecordset::Requery`，**則可能會**發生判斷提示，以及 `CDBException`。 相反地，請呼叫 `CRecordset::Close` 並 `CRecordset::Open`，而不是 `CRecordset::Requery`。 另一個解決方法是不要使用 ODBC 資料指標程式庫，因為 SQL Server 和 SQL Server ODBC 驅動程式會提供原生的資料指標支援，而不需要 ODBC 資料指標程式庫。

## <a name="see-also"></a>另請參閱

[SQL](../../data/odbc/sql.md)<br/>
[SQL：製作直接的 SQL 呼叫 (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
