---
title: 資料錄欄位交換：RFX 函式的使用
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC [C++], data types
- data types [C++], ODBC record field exchange
- RFX (ODBC) [C++], function syntax and parameters
- DoFieldExchange method, and RFX functions
- ODBC [C++], RFX
- RFX (ODBC) [C++], data types
- function calls, RFX functions
ms.assetid: c594300b-5a29-4119-a68b-e7ca32def696
ms.openlocfilehash: f1afded360cfeff564f1f3d8bb9b294aa33cb733
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367136"
---
# <a name="record-field-exchange-using-the-rfx-functions"></a>資料錄欄位交換：RFX 函式的使用

本主題介紹如何使用構成`DoFieldExchange`重寫正文的 RFX 函數調用。

> [!NOTE]
> 本主題適用於從[CRecordset](../../mfc/reference/crecordset-class.md)派生的類,其中尚未實現批量行提取。 如果您使用大量資料列擷取，就會實作大量記錄欄位交換 (大量 RFX)。 大量 RFX 與 RFX 類似。 要瞭解差異,請參閱[記錄集:批量提取記錄 (ODBC)。](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

RFX 全域函數在數據源列和記錄集中的欄位數據成員之間交換數據。 在記錄集的[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)成員函數中寫入 RFX 函數調用。 本主題簡要介紹這些函數,並顯示 RFX 函數可用的數據類型。 [技術說明 43](../../mfc/tn043-rfx-routines.md)介紹了如何為其他數據類型編寫自己的 RFX 函數。

## <a name="rfx-function-syntax"></a><a name="_core_rfx_function_syntax"></a>RFX 函數語法

每個 RFX 函數需要三個參數(有些參數採用可選的第四個或第五個參數):

- 指向[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)物件的指標。 您只需傳遞傳遞給`pFX``DoFieldExchange`的指標即可。

- 列的名稱,因為它顯示在數據源上。

- 記錄集類中相應欄位數據成員或參數數據成員的名稱。

- ( 選擇性的 )在某些函數中,要傳輸的字串或數位的最大長度。 這預設值為 255 位元組,但您可能希望更改它。 最大大小基於`CString`物件的最大大小 **(INT_MAX** (2,147,483,647) 位元組,但在該大小之前可能會遇到驅動程式限制。

- ( 選擇性的 )在函數`RFX_Text`中,有時使用第五個參數來指定列的數據類型。

有關詳細資訊,請參閱*類庫參考*中的[宏和全域](../../mfc/reference/mfc-macros-and-globals.md)下的 RFX 函數。 有關何時可以特殊使用參數的範例,請參閱[記錄集:獲取 SUM 和其他聚合結果 (ODBC)。](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)

## <a name="rfx-data-types"></a><a name="_core_rfx_data_types"></a>RFX 資料類型

類庫提供 RFX 函數,用於在數據源和記錄集之間傳輸許多不同的數據類型。 下面的清單按數據類型匯總了 RFX 函數。 在必須編寫自己的 RFX 函數調用的情況下,請按數據類型從這些函數中選擇。

|函式|資料類型|
|--------------|---------------|
|`RFX_Bool`|**Bool**|
|`RFX_Byte`|**位元組**|
|`RFX_Binary`|`CByteArray`|
|`RFX_Double`|**double**|
|`RFX_Single`|**浮動**|
|`RFX_Int`|**int**|
|`RFX_Long`|**長**|
|`RFX_LongBinary`|`CLongBinary`|
|`RFX_Text`|`CString`|
|`RFX_Date`|`CTime`|

有關詳細資訊,請參閱*類庫參考*中的[宏和全域](../../mfc/reference/mfc-macros-and-globals.md)下的 RFX 函數文檔。 有關C++資料類型如何映射到 SQL 資料類型的資訊,請參閱映射到 SQL 中C++資料類型的表 ANSI SQL 資料類型[:SQL 和C++資料類型 (ODBC)。](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)

## <a name="see-also"></a>另請參閱

[記錄現場交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[資料錄欄位交換：RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[資料錄集：參數化資料錄集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[資料錄集：動態地繫結資料行 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange 類別](../../mfc/reference/cfieldexchange-class.md)
