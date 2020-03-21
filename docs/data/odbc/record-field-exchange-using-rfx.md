---
title: 資料錄欄位交換：RFX 的使用
ms.date: 11/04/2016
helpviewer_keywords:
- RFX (ODBC), implementing
ms.assetid: ada8f043-37e6-4d41-9db3-92c997a61957
ms.openlocfilehash: 70197d2a9130388e86bb94f0d670360bb35febeb
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075872"
---
# <a name="record-field-exchange-using-rfx"></a>資料錄欄位交換：RFX 的使用

本主題說明使用 RFX 與架構的關係。

> [!NOTE]
>  本主題適用于衍生自[CRecordset](../../mfc/reference/crecordset-class.md)的類別，其中尚未執行大量資料列提取。 如果您使用大量資料列擷取，就會實作大量記錄欄位交換 (大量 RFX)。 大量 RFX 與 RFX 類似。 若要瞭解差異，請參閱[記錄集：大量提取記錄（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

下列主題包含相關資訊：

- [記錄欄位交換：使用嚮導程式碼](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md)導入了 RFX 的主要元件，並說明 MFC 應用程式精靈和**加入類別**（如[新增 mfc ODBC 取用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)）撰寫以支援 rfx 的程式碼，以及您可能想要修改嚮導程式碼的方式。

- [記錄欄位交換：使用 RFX 函數](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)說明如何在您的 `DoFieldExchange` 覆寫中寫入 RFX 函數的呼叫。

下表顯示您的角色與架構為您提供的功能。

### <a name="using-rfx-you-and-the-framework"></a>使用 RFX：您和架構

|您|架構|
|---------|-------------------|
|使用 wizard 宣告您的記錄集類別。 指定欄位資料成員的名稱和資料類型。|Wizard 會衍生 `CRecordset` 類別，並為您撰寫[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)覆寫，包括每個欄位資料成員的 RFX 函式呼叫。|
|選擇性以手動方式將任何必要的參數資料成員新增至類別。 針對每個參數資料成員，手動將 RFX 函數呼叫加入 `DoFieldExchange`，為參數群組新增[CFieldExchange：： SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)的呼叫，並在[m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)中指定參數的總數。 請參閱[記錄集：參數化記錄集（ODBC）](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。||
|選擇性手動將其他資料行系結至欄位資料成員。 手動遞增[m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)。 請參閱[記錄集：動態地系結資料行（ODBC）](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。||
|建立記錄集類別的物件。 使用物件之前，請先設定其參數資料成員的值（如果有的話）。|為了提高效率，架構會使用 ODBC 來 prebinds 參數。 當您傳遞參數值時，架構會將它們傳遞至資料來源。 除非排序和/或篩選字串已變更，否則只會傳送查詢的參數值。|
|使用[CRecordset：： open](../../mfc/reference/crecordset-class.md#open)開啟記錄集物件。|執行記錄集的查詢、將資料行系結至記錄集的欄位資料成員，並呼叫 `DoFieldExchange`，以便在第一個選取的記錄和記錄集的欄位資料成員之間交換資料。|
|使用[CRecordset：： Move](../../mfc/reference/crecordset-class.md#move)或功能表或工具列命令，在記錄集中進行滾動。|呼叫 `DoFieldExchange`，將資料從新的目前記錄傳送到欄位資料成員。|
|新增、更新和刪除記錄。|呼叫 `DoFieldExchange` 以將資料傳送至資料來源。|

## <a name="see-also"></a>另請參閱

[資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[資料錄欄位交換：RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[資料錄集：取得 SUM 和其他彙總結果 (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange 類別](../../mfc/reference/cfieldexchange-class.md)<br/>
[宏、全域函式和全域變數](../../mfc/reference/mfc-macros-and-globals.md)
