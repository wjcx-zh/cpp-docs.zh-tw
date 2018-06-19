---
title: 資料錄欄位交換 (RFX) |Microsoft 文件
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
ms.openlocfilehash: 8b214cf05115056efc96c4a078dedd4b7f9a3a1a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33091650"
---
# <a name="record-field-exchange-rfx"></a>資料錄欄位交換 (RFX)
MFC ODBC 資料庫類別自動化資料來源之間移動資料和[資料錄集](../../data/odbc/recordset-odbc.md)物件。 當您衍生自[CRecordset](../../mfc/reference/crecordset-class.md) ，請勿使用大量資料列擷取的資料傳輸的資料錄欄位交換 (RFX) 機制。  
  
> [!NOTE]
>  如果您已實作大量資料列擷取中衍生`CRecordset`類別，架構會使用大量資料錄欄位交換 (Bulk RFX) 機制來傳輸資料。 如需詳細資訊，請參閱[資料錄集： 擷取記錄中大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 對話方塊資料交換 (DDX) 與相似 RFX。 資料來源與資料錄集的欄位資料成員之間移動資料需要多次呼叫資料錄集的[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)函式，並需要相當大的架構之間的互動和[ODBC](../../data/odbc/odbc-basics.md). RFX 機制是類型安全，並將您儲存的工作，例如呼叫 ODBC 函數的 **:: SQLBindCol**。 如需有關 DDX 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
 RFX 大部分是您可以看見。 如果您宣告您的資料錄集類別與 MFC 應用程式精靈或**加入類別**(中所述[加入 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md))，自動 RFX 建立它們。 資料錄集類別必須衍生自基底類別`CRecordset`架構所提供。 MFC 應用程式精靈可讓您建立的初始資料錄集類別。 **將類別加入**可讓您加入其他資料錄集類別，您需要的時候。 如需詳細資訊和範例，請參閱[加入 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)。  
  
 當您想要必須以手動方式在三個情況下，加入少量 RFX 程式碼：  
  
-   使用參數化的查詢。 如需詳細資訊，請參閱[資料錄集： 參數化資料錄集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。  
  
-   執行聯結 （兩個或多個資料表的資料行使用一個資料錄集）。 如需詳細資訊，請參閱[資料錄集： 執行聯結 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)。  
  
-   動態繫結資料行。 這是較不常見，比參數化。 如需詳細資訊，請參閱[資料錄集： 動態地繫結資料行 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。  
  
 如果您需要更進階的了解 RFX，請參閱[資料錄欄位交換： RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 下列主題說明使用資料錄集物件的詳細資料：  
  
-   [資料錄欄位交換：RFX 的使用](../../data/odbc/record-field-exchange-using-rfx.md)  
  
-   [資料錄欄位交換：RFX 函式的使用](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)  
  
-   [資料錄欄位交換：RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)  
  
## <a name="see-also"></a>另請參閱  
 [開放式資料庫連接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)   
 [資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [MFC 應用程式精靈、 資料庫支援](../../mfc/reference/database-support-mfc-application-wizard.md)   
 [CRecordset 類別](../../mfc/reference/crecordset-class.md)