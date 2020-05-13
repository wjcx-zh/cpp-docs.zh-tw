---
title: 資料錄欄位交換 (RFX)
ms.date: 11/04/2016
helpviewer_keywords:
- RFX (ODBC) [C++]
- data [MFC], moving between sources and recordsets
- database classes [C++], RFX
- data [MFC]
- ODBC [C++], RFX
ms.assetid: f5ddfbf0-2901-48d7-9848-4fb84de3c7ee
ms.openlocfilehash: 6f965b90e1e0bbcfd3ad04bb5b40644d61050b2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367154"
---
# <a name="record-field-exchange-rfx"></a>資料錄欄位交換 (RFX)

MFC ODBC 資料庫類自動在數據源和[記錄集](../../data/odbc/recordset-odbc.md)對象之間移動數據。 當您從[CRecordset](../../mfc/reference/crecordset-class.md)派生類並且不使用批量行提取時,數據由記錄欄位交換 (RFX) 機制傳輸。

> [!NOTE]
> 如果在派生`CRecordset`類中實現了批量行提取,則框架將使用批量記錄欄位交換 (Bulk RFX) 機制來傳輸數據。 有關詳細資訊,請參閱[記錄集:批量提取記錄 (ODBC)。](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

RFX 類似於對話數據交換 (DDX)。 在資料源和記錄集的現場資料成員之間移動數據需要多次調用記錄集的[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)函數,並且框架和[ODBC](../../data/odbc/odbc-basics.md)之間存在相當大的交互。 RFX 機制是類型安全的,併為您節省調用 ODBC 函`::SQLBindCol`數(如 )的工作。 如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

RFX 對您大部分是透明的。 如果使用 MFC 應用程式精靈或**添加類**聲明記錄集類(如[添加 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)中所述),則 RFX 會自動內置到它們中。 記錄集類別必須派生自框架提供的基數`CRecordset`。 MFC 應用程式精靈允許您創建初始記錄集類。 **添加類**允許您根據需要添加其他記錄集類。 有關詳細資訊和範例,請參閱添加[MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)。

在三種情況下,您必須手動添加少量 RFX 代碼,此時需要:

- 使用參數化查詢。 有關詳細資訊,請參閱[記錄集:參數化記錄集 (ODBC)。](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

- 執行聯接(對兩個或多個表中的列使用一個記錄集)。 有關詳細資訊,請參閱[記錄集:執行聯接 (ODBC)。](../../data/odbc/recordset-performing-a-join-odbc.md)

- 動態綁定數據列。 這比參數化更不常見。 有關詳細資訊,請參閱[記錄集:動態綁定數據列 (ODBC)。](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)

如果您需要更高級地瞭解 RFX,請參閱[記錄欄位交換:RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

以下主題解釋使用記錄集物件的詳細資訊:

- [資料錄欄位交換：RFX 的使用](../../data/odbc/record-field-exchange-using-rfx.md)

- [資料錄欄位交換：RFX 函式的使用](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)

- [資料錄欄位交換：RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)

## <a name="see-also"></a>另請參閱

[開放資料庫連線 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[MFC 應用程式精靈、資料庫支援](../../mfc/reference/database-support-mfc-application-wizard.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)
