---
title: SQL：SQL 和 C++ 資料類型 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], SQL vs. C++
- SQL data types [C++]
- SQL [C++], vs. C++ data types
ms.assetid: 066e0070-d4da-435c-9c4b-f7cab3352c86
ms.openlocfilehash: cffe44b832ac1eb28d368072b8f0e92ea9f57feb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374471"
---
# <a name="sql-sql-and-c-data-types-odbc"></a>SQL：SQL 和 C++ 資料類型 (ODBC)

> [!NOTE]
> 此資訊適用於 MFC ODBC 類別。 如果您正在使用 MFC DAO 類,請參閱 DAO 説明中的主題「微軟噴氣資料庫引擎 SQL 和 ANSI SQL 的比較」。。

下表將 ANSI SQL 資料類型映射到 C++數據類型。 這增強了*ODBC SDK 程式師*在 MSDN 庫 CD 上的參考附錄 D 中給出*的*C 語言資訊。 嚮導為您管理大多數數據類型映射。 如果不使用嚮導,則可以使用映射資訊來説明手動編寫欄位交換代碼。

### <a name="ansi-sql-data-types-mapped-to-c-data-types"></a>映射到C++資料類型的 ANSI SQL 資料類型

|ANSI SQL 資料類型|C++ 資料型別|
|------------------------|---------------------|
|**字元**|`CString`|
|**十進位**|`CString`1|
|**小林特**|**int**|
|**真正**|**浮動**|
|**整數**|**長**|
|**浮動**|**double**|
|**雙**|**double**|
|**公尺**|`CString`1|
|**瓦爾查爾**|`CString`|
|**朗瓦爾查爾**|`CLongBinary`, `CString` 2|
|**位元**|**Bool**|
|**TINYINT**|**位元組**|
|**比金特**|`CString`1|
|**二 進制**|`CByteArray`|
|**瓦爾里進位**|`CByteArray`|
|**LONGVARBINARY**|`CLongBinary`, `CByteArray` 3|
|**日期**|`CTime`, `CString`|
|**時間**|`CTime`, `CString`|
|**時間 戳**|`CTime`, `CString`|

1. ANSI **DECIMAL**和**數位**映`CString`射, 因為**SQL_C_CHAR**是預設的 ODBC 傳輸類型。

2. 默認情況下,在映射到 時,超過 255 個字元的字元`CString`數據將被截斷。 可以通過顯示式設定*nMaxLength 參數*來延長`RFX_Text`截斷長度 。

3. 默認情況下,在映射到 時,超過 255 個字元的二`CByteArray`進位數據將被截斷。 可以通過顯示式設定*nMaxLength 參數*來延長`RFX_Binary`截斷長度 。

如果不使用 ODBC 遊標庫,則在嘗試使用 Microsoft SQL Server ODBC 驅動程式和 MFC ODBC 資料庫類更新兩個或多個長變數長度欄位時可能會遇到問題。 ODBC 類型 **,SQL_LONGVARCHAR**和**SQL_LONGVARBINARY,** 映射到文字和圖像 SQL 伺服器類型。 如果`CDBException`在同一呼叫 上更新兩個或多個長度的可變長度欄位`CRecordset::Update`, 則引發 。 因此,不要與`CRecordset::Update`同時更新多個長列。 您可以更新多個長列與 ODBC API `SQLPutData`。 也可以使用 ODBC 遊標庫,但不建議支援游標的驅動程式(如 SQL Server 驅動程式)使用,並且不需要游標庫。

如果將 ODBC 游標庫與 MFC ODBC 資料庫類和 Microsoft SQL Server`CDBException`ODBC 驅動`CRecordset::Update`程式一起`CRecordset::Requery`使用,則可能會與調用 後調用 時一起出現**ASSERT。** 相反,呼叫`CRecordset::Close``CRecordset::Open``CRecordset::Requery`而不是 。 另一個解決方案是不使用 ODBC 游標庫,因為 SQL Server 和 SQL Server ODBC 驅動程式為游標本機提供本機支援,並且不需要 ODBC 游標庫。

## <a name="see-also"></a>另請參閱

[SQL](../../data/odbc/sql.md)<br/>
[SQL：製作直接的 SQL 呼叫 (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
