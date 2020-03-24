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
ms.openlocfilehash: e1ba9f29ebf2cb3b1f94620e815882c850bbc7cc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213053"
---
# <a name="record-field-exchange-rfx"></a>資料錄欄位交換 (RFX)

MFC ODBC 資料庫類別會自動在資料來源與[記錄集](../../data/odbc/recordset-odbc.md)物件之間移動資料。 當您從[CRecordset](../../mfc/reference/crecordset-class.md)衍生類別，但不使用大量資料列提取時，資料會由記錄欄位交換（RFX）機制來傳送。

> [!NOTE]
>  如果您已在衍生的 `CRecordset` 類別中執行大量資料列提取，此架構會使用大量記錄欄位交換（Bulk RFX）機制來傳送資料。 如需詳細資訊，請參閱[記錄集：大量提取記錄（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

RFX 類似于對話資料交換（DDX）。 在資料來源與記錄集的欄位資料成員之間移動資料時，需要對記錄集的[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)函式進行多次呼叫，並在架構和[ODBC](../../data/odbc/odbc-basics.md)之間進行相當的互動。 RFX 機制是型別安全的，可為您節省呼叫 ODBC 函數的工作，例如 `::SQLBindCol`。 如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

RFX 對您而言大多是透明的。 如果您使用 [MFC 應用程式精靈] 或 [**加入類別**] 來宣告記錄集類別（如[加入 Mfc ODBC 取用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)中所述），則會自動內建 RFX。 您的記錄集類別必須衍生自架構所提供的基底類別 `CRecordset`。 MFC 應用程式精靈可讓您建立初始記錄集類別。 [**新增類別**] 可讓您在需要時新增其他記錄集類別。 如需詳細資訊和範例，請參閱[加入 MFC ODBC 取用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)。

當您想要執行下列三種情況時，您必須手動新增少量 RFX 程式碼：

- 使用參數化查詢。 如需詳細資訊，請參閱[記錄集：參數化記錄集（ODBC）](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。

- 執行聯結（針對兩個或多個資料表中的資料行使用一個記錄集）。 如需詳細資訊，請參閱[記錄集：執行聯結（ODBC）](../../data/odbc/recordset-performing-a-join-odbc.md)。

- 動態地系結資料行。 這不如參數化一般。 如需詳細資訊，請參閱[記錄集：動態地系結資料行（ODBC）](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。

如果您需要更深入的 RFX 瞭解，請參閱[記錄欄位交換： RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

下列主題說明使用記錄集物件的詳細資料：

- [資料錄欄位交換：RFX 的使用](../../data/odbc/record-field-exchange-using-rfx.md)

- [資料錄欄位交換：RFX 函式的使用](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)

- [資料錄欄位交換：RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)

## <a name="see-also"></a>另請參閱

[開放式資料庫連接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[MFC 應用程式精靈、資料庫支援](../../mfc/reference/database-support-mfc-application-wizard.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)
