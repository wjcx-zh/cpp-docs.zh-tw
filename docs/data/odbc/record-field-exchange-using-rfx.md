---
title: 資料錄欄位交換：使用 RFX
ms.date: 11/04/2016
helpviewer_keywords:
- RFX (ODBC), implementing
ms.assetid: ada8f043-37e6-4d41-9db3-92c997a61957
ms.openlocfilehash: 2a029f653753363e08b3c4f8b9fceab6295924af
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59034111"
---
# <a name="record-field-exchange-using-rfx"></a>資料錄欄位交換：使用 RFX

本主題說明您如何使用 RFX，相對於架構的功能。

> [!NOTE]
>  本主題適用於衍生自類別[CRecordset](../../mfc/reference/crecordset-class.md)的大量資料列中擷取尚未實作。 如果您使用大量資料列擷取，被實作大量資料錄欄位交換 (Bulk RFX)。 大量 RFX 很類似 RFX。 若要了解這些差異，請參閱[資料錄集：擷取大量 (ODBC) 資料錄](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

下列主題包含相關的資訊：

- [資料錄欄位交換：精靈程式碼的使用](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md)介紹 RFX 的主要元件，並說明的程式碼，MFC 應用程式精靈並**加入類別**(如中所述[加入 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) 撰寫若要支援 RFX 和您可能要修改的精靈程式碼的方式。

- [資料錄欄位交換：使用 RFX 函式](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)說明撰寫呼叫 RFX 函式，在您`DoFieldExchange`覆寫。

下表顯示您相對於架構會為您的角色。

### <a name="using-rfx-you-and-the-framework"></a>RFX 的使用：您與架構

|您|架構|
|---------|-------------------|
|宣告您的資料錄集類別的精靈。 指定欄位資料成員的名稱和資料的類型。|精靈衍生`CRecordset`類別和寫入[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)讓您覆寫，請包括 RFX 函式的呼叫，每個欄位資料成員。|
|（選擇性）手動新增至類別的任何所需的參數資料成員。 手動新增的 RFX 函式呼叫`DoFieldExchange`每個參數的資料成員，將呼叫加入[CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)群組的參數，並指定參數的總數[m_nParams](../../mfc/reference/crecordset-class.md#m_nparams). 請參閱[資料錄集：參數化資料錄集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。||
|（選擇性）手動將其他資料行繫結至欄位資料成員。 手動遞增[m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)。 請參閱[資料錄集：動態繫結資料行 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。||
|建構您的資料錄集類別的物件。 之前使用物件，設定其參數的值資料成員，如果有的話。|為了提高效率，架構會 prebinds 參數，使用 ODBC。 當您傳遞參數值時，則架構會將它們傳送到資料來源。 除非變更了排序和/或篩選條件字串變動，會傳送參數值。|
|開啟資料錄集物件，使用[crecordset:: Open](../../mfc/reference/crecordset-class.md#open)。|執行資料錄集的查詢時，將資料行繫結至欄位資料成員的資料錄集，並呼叫`DoFieldExchange`第一個選取的記錄和資料錄集的欄位資料成員之間交換資料。|
|資料錄集的使用中的捲軸[CRecordset::Move](../../mfc/reference/crecordset-class.md#move)或功能表或工具列命令。|呼叫`DoFieldExchange`將資料傳送至的欄位資料成員，從新的目前資料錄。|
|新增、 更新和刪除記錄。|呼叫`DoFieldExchange`將資料傳送至資料來源。|

## <a name="see-also"></a>另請參閱

[資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[資料錄欄位交換：RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[資料錄集：取得 Sum 和其他彙總的結果 (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange 類別](../../mfc/reference/cfieldexchange-class.md)<br/>
[巨集、全域函式和全域變數](../../mfc/reference/mfc-macros-and-globals.md)

