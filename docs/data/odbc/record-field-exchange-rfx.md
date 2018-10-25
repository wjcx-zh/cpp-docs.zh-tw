---
title: 資料錄欄位交換 (RFX) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- RFX (ODBC) [C++]
- data [MFC], moving between sources and recordsets
- database classes [C++], RFX
- data [MFC]
- ODBC [C++], RFX
ms.assetid: f5ddfbf0-2901-48d7-9848-4fb84de3c7ee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ede5ce16aa7255bd6f62afc1b397d802003e6621
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080999"
---
# <a name="record-field-exchange-rfx"></a>資料錄欄位交換 (RFX)

MFC ODBC 資料庫類別自動化的資料來源之間移動資料和[資料錄集](../../data/odbc/recordset-odbc.md)物件。 當您衍生的類別[CRecordset](../../mfc/reference/crecordset-class.md)和不使用大量資料列擷取、 資料傳輸的資料錄欄位交換 (RFX) 機制。

> [!NOTE]
>  如果您已實作在衍生的大量資料列擷取`CRecordset`類別，架構會使用大量資料錄欄位交換 (Bulk RFX) 機制來傳輸資料。 如需詳細資訊，請參閱 <<c0> [ 資料錄集： 擷取記錄中大量資料庫連接 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

RFX 是類似於對話方塊資料交換 (DDX)。 資料來源與資料錄集的欄位資料成員之間移動資料需要資料錄集的多次呼叫[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)函式，並具有相當大的互動，framework 間和[ODBC](../../data/odbc/odbc-basics.md). RFX 機制是類型安全，並且將您的工作，例如呼叫 ODBC 函數的`::SQLBindCol`。 如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

RFX 大部分是透明的。 如果您宣告您的資料錄集類別，使用 [MFC 應用程式精靈] 或**加入類別**(如中所述[加入 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md))，自動 RFX 建置它們。 您的資料錄集類別必須衍生自的基底類別`CRecordset`framework 所提供。 MFC 應用程式精靈可讓您建立的初始資料錄集類別。 **將類別加入**可讓您新增其他資料錄集類別，您需要的時候。 如需詳細資訊和範例，請參閱 <<c0> [ 加入 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)。

您必須手動將少量的 RFX 程式碼新增在三個情況下，當您想要：

- 使用參數化的查詢。 如需詳細資訊，請參閱 <<c0> [ 資料錄集： 參數化資料錄集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。

- 執行聯結 （使用兩個或多個資料表的資料行的一個資料錄集）。 如需詳細資訊，請參閱 <<c0> [ 資料錄集： 執行聯結 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)。

- 動態繫結資料行。 這是參數化比較不常見。 如需詳細資訊，請參閱 <<c0> [ 資料錄集： 動態地繫結資料行 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。

如果您需要 RFX 更進一步了解，請參閱[資料錄欄位交換： RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

下列主題說明使用資料錄集物件的詳細資料：

- [資料錄欄位交換：RFX 的使用](../../data/odbc/record-field-exchange-using-rfx.md)

- [資料錄欄位交換：RFX 函式的使用](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)

- [資料錄欄位交換：RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)

## <a name="see-also"></a>另請參閱

[開放式資料庫連接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[MFC 應用程式精靈、資料庫支援](../../mfc/reference/database-support-mfc-application-wizard.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)