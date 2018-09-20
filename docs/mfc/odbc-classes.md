---
title: ODBC 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.data
dev_langs:
- C++
helpviewer_keywords:
- database classes [MFC], ODBC
- ODBC classes [MFC]
ms.assetid: 6c40fca8-3033-4873-9abe-7f51725de0e0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 97bbdb74d122e633574dcf76876f0907de8ef2c4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400573"
---
# <a name="odbc-classes"></a>ODBC 類別

這些類別會使用各種不同的開放式資料庫連接 (ODBC) 驅動程式可供使用的資料庫以便輕鬆存取的其他應用程式架構類別。

使用 ODBC 資料庫的程式也可在至少`CDatabase`物件和`CRecordset`物件。

[CDatabase](../mfc/reference/cdatabase-class.md)<br/>
封裝資料來源，讓您可以操作的資料來源的連接。

[CRecordset](../mfc/reference/crecordset-class.md)<br/>
封裝一組從資料來源選取的記錄。 資料錄集啟用捲動記錄間，更新資料錄 （新增、 編輯和刪除記錄），利用篩選條件，限定選取項目排序選取範圍，並將參數化資訊的選取範圍取得，或在執行階段計算。

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
提供表單直接連接到資料錄集物件的檢視。 對話方塊資料交換 (DDX) 機制交換資料，資料錄集之間的資料錄檢視控制項。 所有的表單檢視中，例如資料錄檢視根據對話方塊範本資源。 資料錄檢視也支援資料錄集中移動記錄記錄、 更新記錄，並關閉相關聯的資料錄集資料錄檢視關閉時。

[CDBException](../mfc/reference/cdbexception-class.md)<br/>
所產生的資料存取中的失敗處理例外狀況。 這個類別會有相同的用途，做為其他的例外狀況類別中的類別庫的例外狀況處理機制。

[CFieldExchange](../mfc/reference/cfieldexchange-class.md)<br/>
提供內容資訊給支援資料錄欄位交換 (RFX)，其中的欄位資料成員和參數資料成員的資料錄集物件和資料來源上對應的資料表資料行之間交換資料。 相當於類別[CDataExchange](../mfc/reference/cdataexchange-class.md)，它用於同樣的對話方塊資料交換 (DDX)。

## <a name="related-classes"></a>相關的類別

[CLongBinary](../mfc/reference/clongbinary-class.md)<br/>
封裝的二進位大型物件 (BLOB)，儲存體的控制代碼，例如點陣圖。 `CLongBinary` 物件用來管理儲存在資料庫資料表中的大型資料物件。

[CDBVariant](../mfc/reference/cdbvariant-class.md)<br/>
可讓您儲存的值，而不需擔心值的資料類型。 `CDBVariant` 會追蹤目前的值等位中儲存的資料類型。

## <a name="see-also"></a>另請參閱

[類別概觀](../mfc/class-library-overview.md)

