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
ms.openlocfilehash: 00b995890cf0cced5d06c52c4d702c1c89111dc3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50489956"
---
# <a name="record-field-exchange-using-the-rfx-functions"></a>資料錄欄位交換：RFX 函式的使用

本主題說明如何使用 RFX 函式會呼叫主體所組成您`DoFieldExchange`覆寫。

> [!NOTE]
>  本主題適用於衍生自類別[CRecordset](../../mfc/reference/crecordset-class.md)的大量資料列中擷取尚未實作。 如果您使用大量資料列擷取，被實作大量資料錄欄位交換 (Bulk RFX)。 大量 RFX 很類似 RFX。 若要了解這些差異，請參閱[資料錄集： 擷取記錄中大量資料庫連接 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

RFX 全域函式會交換資料錄集中的資料來源和欄位資料成員上的資料行之間的資料。 您撰寫 RFX 函式會呼叫您的資料錄集中[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)成員函式。 本主題簡要說明的函式，並顯示哪些 RFX 函式可供使用的資料類型。 [技術提示 43](../../mfc/tn043-rfx-routines.md)說明如何撰寫您自己的 RFX 函式的其他資料類型。

##  <a name="_core_rfx_function_syntax"></a> RFX 函式語法

每個 RFX 函式接受三個參數 （和某些會接受選擇性的第四個或第五個參數）：

- 指標[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)物件。 您只會傳遞`pFX`指標傳遞給`DoFieldExchange`。

- 因為它的資料行名稱會出現在資料來源。

- 對應的欄位資料成員或參數的資料錄集類別中的資料成員的名稱。

- （選擇性）在某些函式、 字串或陣列所傳輸的最大長度。 此預設值為 255 個位元組，但您可能想要變更它。 大小上限為基礎的大小上限`CString`物件 — **INT_MAX** (2,147,483,647) 個位元組，但您可能會遇到驅動程式的限制。

- （選擇性）在 `RFX_Text`函式，您有時會使用第五個參數來指定資料行的資料類型。

如需詳細資訊，請參閱 RFX 函式之下[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)中*類別庫參考*。 如需範例時，您可能會進行特殊使用的參數，請參閱[資料錄集： 取得 Sum 和其他彙總結果 (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)。

##  <a name="_core_rfx_data_types"></a> RFX 資料類型

類別庫提供 RFX 函式之間的資料來源和資料錄集傳輸許多不同的資料型別。 下列清單摘要說明 RFX 函式的資料型別。 在您必須在其中撰寫您自己的 RFX 函式呼叫的情況下，選取來自這些函式的資料型別。

|功能|資料類型|
|--------------|---------------|
|`RFX_Bool`|**BOOL**|
|`RFX_Byte`|**BYTE**|
|`RFX_Binary`|`CByteArray`|
|`RFX_Double`|**double**|
|`RFX_Single`|**float**|
|`RFX_Int`|**int**|
|`RFX_Long`|**long**|
|`RFX_LongBinary`|`CLongBinary`|
|`RFX_Text`|`CString`|
|`RFX_Date`|`CTime`|


如需詳細資訊，請參閱下方 RFX 函式文件[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)中*類別庫參考*。 如需 c + + 資料類型如何對應至 SQL 資料類型資訊，請參閱 < ANSI SQL 資料類型對應至 c + + 資料類型的資料表中[SQL: SQL 和 c + + 資料類型 (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)。

## <a name="see-also"></a>另請參閱

[資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[資料錄欄位交換：RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[資料錄集：參數化資料錄集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[資料錄集：動態地繫結資料行 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange 類別](../../mfc/reference/cfieldexchange-class.md)