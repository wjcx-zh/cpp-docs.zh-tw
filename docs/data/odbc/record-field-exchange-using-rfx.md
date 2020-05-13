---
title: 資料錄欄位交換：RFX 的使用
ms.date: 11/04/2016
helpviewer_keywords:
- RFX (ODBC), implementing
ms.assetid: ada8f043-37e6-4d41-9db3-92c997a61957
ms.openlocfilehash: dc0cdcee758f4842b0738068a8a11c4e2e404155
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367150"
---
# <a name="record-field-exchange-using-rfx"></a>資料錄欄位交換：RFX 的使用

本主題介紹您如何處理使用 RFX 與框架的作用。

> [!NOTE]
> 本主題適用於從[CRecordset](../../mfc/reference/crecordset-class.md)派生的類,其中尚未實現批量行提取。 如果您使用大量資料列擷取，就會實作大量記錄欄位交換 (大量 RFX)。 大量 RFX 與 RFX 類似。 要瞭解差異,請參閱[記錄集:批量提取記錄 (ODBC)。](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

以下主題包含相關資訊:

- [記錄欄位交換:使用嚮導代碼](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md)引入了 RFX 的主要元件,並解釋了 MFC 應用程式精靈和**添加類**(如[添加 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)中所述)為支援 RFX 而編寫的代碼,以及如何修改向導代碼。

- [記錄欄位交換:使用 RFX 函數](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)可以解釋在重寫中寫入對 RFX 函數的`DoFieldExchange`調用。

下表顯示了您相對於框架為您做什麼的角色。

### <a name="using-rfx-you-and-the-framework"></a>使用 RFX:您和框架

|您|架構|
|---------|-------------------|
|使用嚮導聲明記錄集類。 指定欄位資料成員的名稱和資料類型。|嚮導派生一個`CRecordset`類,並為您編寫[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)重寫,包括針對每個欄位數據成員的 RFX 函數調用。|
|( 選擇性的 )手動將任何所需的參數數據成員添加到類中。 手動`DoFieldExchange`為每個參數數據成員添加 RFX 函數調用,向[CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)添加參數組調用,並在[m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)中指定參數的總數。 請參閱[記錄集:參數化記錄集 (ODBC)。](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)||
|( 選擇性的 )手動將其他列綁定到欄位數據成員。 手動增加[m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)。 請參閱[記錄集:動態綁定數據列 (ODBC)。](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)||
|構造記錄集類的物件。 在使用 物件之前,設置其參數數據成員的值(如果有)。|為了提高效率,框架使用 ODBC 預綁定參數。 傳遞參數值時,框架會將它們傳遞給數據源。 除非排序和/或篩選器字串已更改,否則僅發送參數值進行重新查詢。|
|使用[CRecordset::打開](../../mfc/reference/crecordset-class.md#open)記錄集物件。|執行記錄集的查詢,將列綁定到記錄集的欄位數據成員,並調用`DoFieldExchange`在第一個選定的記錄和記錄集的欄位數據成員之間交換數據。|
|使用[CRecordset:move](../../mfc/reference/crecordset-class.md#move)或功能表或工具列命令在記錄集中滾動。|調用`DoFieldExchange`將數據從新的當前記錄傳輸到欄位數據成員。|
|添加、更新和刪除記錄。|將數據`DoFieldExchange`傳輸到數據源的調用。|

## <a name="see-also"></a>另請參閱

[記錄現場交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[資料錄欄位交換：RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[資料錄集：取得 SUM 和其他彙總結果 (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange 類別](../../mfc/reference/cfieldexchange-class.md)<br/>
[巨集、全域函式和全域變數](../../mfc/reference/mfc-macros-and-globals.md)
