---
title: 記錄檢視的資料交換 (MFC 資料存取)
ms.date: 11/19/2018
helpviewer_keywords:
- RFX (record field exchange), data exchange mechanism
- RFX (record field exchange), record views
- record views, data exchange
- DDX (dialog data exchange), record views
- RFX (record field exchange)
ms.assetid: abc52ca7-6997-47a7-98f3-f347f52b1f72
ms.openlocfilehash: f9f460305b55a2313b64effdf4d1dbbfd9823def
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213463"
---
# <a name="data-exchange-for-record-views---mfc-data-access"></a>記錄檢視的資料交換 (MFC 資料存取)

當您使用 [[加入類別](../mfc/reference/adding-an-mfc-odbc-consumer.md)] 將記錄視圖的對話方塊範本資源中的控制項對應至記錄集的欄位時，架構會管理雙向的資料交換，從記錄集到控制項，以及從控制項到記錄集。 使用 DDX 機制意味著您不需要自行撰寫程式碼以來回傳輸資料。

記錄視圖的 DDX 會與適用于類別 `CRecordset` （ODBC）之記錄集的[RFX](../data/odbc/record-field-exchange-rfx.md)搭配使用。  RFX 會在資料來源的目前記錄與記錄集物件的欄位資料成員之間移動資料。 DDX 會將資料，從欄位資料成員移到表單中的控制項。 這種組合會在一開始以及使用者在記錄間移動時，填滿表單控制項。 它也可以將更新的資料移動回記錄集，然後移到資料來源。

下圖顯示記錄視圖的 DDX 和 RFX 之間的關聯性。

![對話方塊&#45;資料交換和記錄&#45;欄位交換](../data/media/vc37xt1.gif "對話方塊&#45;資料交換和記錄&#45;欄位交換")<br/>
對話方塊資料交換及記錄欄位交換

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../mfc/dialog-data-exchange-and-validation.md)。 如需 RFX 的詳細資訊，請參閱[記錄欄位交換（RFX）](../data/odbc/record-field-exchange-rfx.md)。

## <a name="see-also"></a>另請參閱

[資料錄檢視 (MFC 資料存取)](../data/record-views-mfc-data-access.md)<br/>
[ODBC 驅動程式清單](../data/odbc/odbc-driver-list.md)
