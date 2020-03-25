---
title: 顯示和操作表單中的資料
ms.date: 11/04/2016
helpviewer_keywords:
- forms [C++], displaying data
- displaying data [C++], forms
- ODBC [C++], forms
- record views [C++], displaying data
- data [MFC]
- data [MFC], displaying in a form
ms.assetid: c56185c4-12cb-40b1-b499-02b29ea83e3a
ms.openlocfilehash: 6b663fabd0c87d9a2773e6f5a2796bcc8f57ce29
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213248"
---
# <a name="displaying-and-manipulating-data-in-a-form"></a>顯示和操作表單中的資料

許多資料存取應用程式會選取資料，並將它顯示在表單的欄位中。 [資料庫類別[CRecordView](../../mfc/reference/crecordview-class.md) ] 可讓您直接連接到記錄集物件的[CFormView](../../mfc/reference/cformview-class.md)物件。 記錄視圖會使用[對話方塊資料交換（DDX）](../../mfc/dialog-data-exchange-and-validation.md) ，將目前記錄的欄位值從記錄集移至表單上的控制項，並將更新的資訊移回記錄集。 然後，記錄集會使用記錄欄位交換（RFX），在其欄位資料成員和資料來源上資料表中的對應資料行之間移動資料。

您可以使用 [MFC 應用程式精靈] 或 [**加入類別**] （如[加入 Mfc ODBC 取用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)中所述）來建立 view 類別及其相關聯的記錄集類別。

當您關閉檔時，會終結記錄視圖及其記錄集。 如需記錄視圖的詳細資訊，請參閱[記錄 views](../../data/record-views-mfc-data-access.md)。 如需 RFX 的詳細資訊，請參閱[記錄欄位交換（RFX）](../../data/odbc/record-field-exchange-rfx.md)。

## <a name="see-also"></a>另請參閱

[ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)
