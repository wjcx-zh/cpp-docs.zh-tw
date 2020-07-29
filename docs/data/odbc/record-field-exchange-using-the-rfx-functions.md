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
ms.openlocfilehash: 4d621fbe2207114dd51845b819d309802a009690
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216527"
---
# <a name="record-field-exchange-using-the-rfx-functions"></a>資料錄欄位交換：RFX 函式的使用

本主題說明如何使用組成覆寫主體的 RFX 函式呼叫 `DoFieldExchange` 。

> [!NOTE]
> 本主題適用于衍生自[CRecordset](../../mfc/reference/crecordset-class.md)的類別，其中尚未執行大量資料列提取。 如果您使用大量資料列擷取，就會實作大量記錄欄位交換 (大量 RFX)。 大量 RFX 與 RFX 類似。 若要瞭解差異，請參閱[記錄集：大量提取記錄（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

RFX 全域函式會在記錄集的資料來源和欄位資料成員上的資料行之間交換資料。 您在記錄集的[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)成員函式中撰寫 RFX 函式呼叫。 本主題會簡短地描述函式，並顯示可使用 RFX 函數的資料類型。 [技術提示 43](../../mfc/tn043-rfx-routines.md)說明如何為其他資料類型撰寫您自己的 RFX 函數。

## <a name="rfx-function-syntax"></a><a name="_core_rfx_function_syntax"></a>RFX 函數語法

每個 RFX 函數都接受三個參數（而有些則採用選擇性的第四個或第五個參數）：

- [CFieldExchange](../../mfc/reference/cfieldexchange-class.md)物件的指標。 您只要沿著 `pFX` 傳遞給的指標傳遞 `DoFieldExchange` 。

- 資料行出現在資料來源上的名稱。

- 記錄集類別中對應的欄位資料成員或參數資料成員的名稱。

- 選擇性在某些函式中，要傳送之字串或陣列的最大長度。 這預設為255個位元組，但您可能會想要加以變更。 大小上限是根據物件的大小上限 `CString` （ **INT_MAX** （2147483647）位元組），但您可能會在該大小之前遇到驅動程式限制。

- 選擇性在 `RFX_Text` 函數中，您有時會使用第五個參數來指定資料行的資料類型。

如需詳細資訊，請參閱*類別庫參考*中[宏和全域](../../mfc/reference/mfc-macros-and-globals.md)的 RFX 函式。 如需您可能會特別使用參數的範例，請參閱[記錄集：取得總和和其他匯總結果（ODBC）](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)。

## <a name="rfx-data-types"></a><a name="_core_rfx_data_types"></a>RFX 資料類型

類別庫會提供 RFX 函式，以便在資料來源與您的記錄集之間傳輸許多不同的資料類型。 下列清單摘要說明依資料類型的 RFX 函數。 在您必須撰寫自己的 RFX 函式呼叫的情況下，請從這些函數中依資料類型選取。

|函式|資料類型|
|--------------|---------------|
|`RFX_Bool`|**型**|
|`RFX_Byte`|**節**|
|`RFX_Binary`|`CByteArray`|
|`RFX_Double`|**`double`**|
|`RFX_Single`|**`float`**|
|`RFX_Int`|**`int`**|
|`RFX_Long`|**`long`**|
|`RFX_LongBinary`|`CLongBinary`|
|`RFX_Text`|`CString`|
|`RFX_Date`|`CTime`|

如需詳細資訊，請參閱*類別庫參考*中[宏和全域](../../mfc/reference/mfc-macros-and-globals.md)底下的 RFX 函數檔。 如需 c + + 資料類型如何對應至 SQL 資料類型的詳細資訊，請參閱對應至 Sql 中的 c + + 資料類型的資料表 ANSI SQL 資料類型[（ODBC）](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)。

## <a name="see-also"></a>另請參閱

[記錄欄位交換（RFX）](../../data/odbc/record-field-exchange-rfx.md)<br/>
[記錄欄位交換： RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[記錄集：參數化記錄集（ODBC）](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[記錄集：動態地系結資料行（ODBC）](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange 類別](../../mfc/reference/cfieldexchange-class.md)
