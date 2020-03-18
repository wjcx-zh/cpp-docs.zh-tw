---
title: ODBC 類別
ms.date: 11/04/2016
helpviewer_keywords:
- database classes [MFC], ODBC
- ODBC classes [MFC]
ms.assetid: 6c40fca8-3033-4873-9abe-7f51725de0e0
ms.openlocfilehash: a4cfa0d7afa197de7b65b6a0bd6b881a09534ef6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447692"
---
# <a name="odbc-classes"></a>ODBC 類別

這些類別會與其他應用程式架構類別搭配使用，讓您輕鬆存取可使用開放式資料庫連接（ODBC）驅動程式的各種資料庫。

使用 ODBC 資料庫的程式至少會有一個 `CDatabase` 物件和一個 `CRecordset` 物件。

[CDatabase](../mfc/reference/cdatabase-class.md)<br/>
封裝資料來源的連接，您可以在資料來源上操作。

[CRecordset](../mfc/reference/crecordset-class.md)<br/>
封裝從資料來源選取的一組記錄。 記錄集可讓您從記錄滾動到記錄、更新記錄（加入、編輯和刪除記錄）、使用篩選準則來限定選取範圍、排序選取範圍，以及使用在執行時間取得或計算的資訊將選取專案參數化。

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
提供直接連接到記錄集物件的表單檢視。 對話資料交換（DDX）機制會在記錄視圖的記錄集和控制項之間交換資料。 就像所有表單檢視一樣，記錄視圖是以對話方塊範本資源為基礎。 記錄視圖也支援從記錄移至記錄集內的記錄、更新記錄，以及在記錄視圖關閉時關閉相關聯的記錄集。

[CDBException](../mfc/reference/cdbexception-class.md)<br/>
因數據存取處理失敗而產生的例外狀況。 這個類別的用途與類別庫的例外狀況處理機制中的其他例外狀況類別相同。

[CFieldExchange](../mfc/reference/cfieldexchange-class.md)<br/>
提供內容資訊以支援記錄欄位交換（RFX），這會在記錄集物件的欄位資料成員與參數資料成員之間交換資料，以及在資料來源上對應的資料表資料行。 類似于類別[CDataExchange](../mfc/reference/cdataexchange-class.md)，其使用方式類似于對話資料交換（DDX）。

## <a name="related-classes"></a>相關類別

[CLongBinary](../mfc/reference/clongbinary-class.md)<br/>
封裝二進位大型物件（BLOB）（例如點陣圖）之儲存體的控制碼。 `CLongBinary` 物件是用來管理儲存在資料庫資料表中的大型資料物件。

[CDBVariant](../mfc/reference/cdbvariant-class.md)<br/>
可讓您儲存值，而不需擔心值的資料類型。 `CDBVariant` 會追蹤目前值的資料類型，並將其儲存在聯集內。

## <a name="see-also"></a>另請參閱

[類別總覽](../mfc/class-library-overview.md)
