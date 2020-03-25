---
title: 資料錄集：使用大型的資料項目 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- BLOB (binary large object), recordsets
- ODBC recordsets, binary large objects
- recordsets, binary large objects
- binary large objects
- CLongBinary class, using in recordsets
ms.assetid: 3e80b5a8-b6e7-43c6-a816-e54befc513a3
ms.openlocfilehash: b84365461ce6d45fccdf1922974feff5af93f99f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212754"
---
# <a name="recordset-working-with-large-data-items-odbc"></a>資料錄集：使用大型的資料項目 (ODBC)

本主題適用于 MFC ODBC 類別和 MFC DAO 類別。

> [!NOTE]
>  如果您使用 MFC DAO 類別，請使用類別[CByteArray](../../mfc/reference/cbytearray-class.md) （而不是類別[CLongBinary](../../mfc/reference/clongbinary-class.md)）來管理您的大型資料項目。 如果您使用 MFC ODBC 類別來進行大量資料列提取，請使用 `CLongBinary`，而不是 `CByteArray`。 如需大量資料列提取的詳細資訊，請參閱[記錄集：大量提取記錄（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

假設您的資料庫可以儲存大量的資料，例如點陣圖（員工相片、地圖、產品的圖片、OLE 物件等等）。 這類資料通常稱為二進位大型物件（或 BLOB），原因如下：

- 每個域值都很大。

- 不同于數位和其他簡單的資料類型，它沒有可預測的大小。

- 從您的程式觀點來看，資料是 formless 的。

本主題說明資料庫類別提供來處理這類物件的支援。

##  <a name="managing-large-objects"></a><a name="_core_managing_large_objects"></a>管理大型物件

記錄集有兩種方式可以解決管理二進位大型物件的特殊困難。 您可以使用 [類別[CByteArray](../../mfc/reference/cbytearray-class.md) ]，也可以使用 [類別[CLongBinary](../../mfc/reference/clongbinary-class.md)]。 一般來說，`CByteArray` 是管理大型二進位資料的慣用方式。

`CByteArray` 所需的額外負荷比 `CLongBinary` 更多，但更有能力，如[CByteArray 類別](#_core_the_cbytearray_class)中所述。 `CLongBinary` 會在[CLongBinary 類別](#_core_the_clongbinary_class)中簡短說明。

如需使用 `CByteArray` 來處理大型資料項目的詳細資訊，請參閱[技術提示 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md)。

##  <a name="cbytearray-class"></a><a name="_core_the_cbytearray_class"></a>CByteArray 類別

`CByteArray` 是其中一個 MFC 集合類別。 `CByteArray` 物件會儲存位元組的動態陣列，陣列可以視需要成長。 類別提供索引的快速存取，就像使用內C++建陣列一樣。 基於診斷目的，`CByteArray` 物件可以序列化和傾印。 類別提供成員函式，用來取得和設定指定的位元組、插入和附加位元組，以及移除一個位元組或所有位元組。 這些功能可讓您更輕鬆地剖析二進位資料。 例如，如果二進位物件是 OLE 物件，您可能必須處理一些標頭位元組，才能到達實際的物件。

##  <a name="using-cbytearray-in-recordsets"></a><a name="_core_using_cbytearray_in_recordsets"></a>在記錄集中使用 CByteArray

藉由提供記錄集的欄位資料成員類型 `CByteArray`，您可以提供一個固定的基底，讓[RFX](../../data/odbc/record-field-exchange-rfx.md)能夠記錄管理集和資料來源之間這類物件的傳送，以及您可以在物件內運算元據的方式。 RFX 需要特定的網站來取得已抓取的資料，而且您需要一種方式來存取基礎資料。

如需使用 `CByteArray` 來處理大型資料項目的詳細資訊，請參閱[技術提示 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md)。

##  <a name="clongbinary-class"></a><a name="_core_the_clongbinary_class"></a>CLongBinary 類別

[CLongBinary](../../mfc/reference/clongbinary-class.md)物件是一個 `HGLOBAL` 控制碼周圍的簡單 shell，用於在堆積上配置的儲存區。 當它系結包含二進位大型物件的資料表資料行時，RFX 會在需要將資料傳送至記錄集時配置 `HGLOBAL` 控制碼，並將控制碼儲存在記錄集的 [`CLongBinary`] 欄位中。

接著，您可以使用 `HGLOBAL` 控制碼（`m_hData`）來處理資料本身，如同處理資料一樣，對其進行操作。 這就是[CByteArray](../../mfc/reference/cbytearray-class.md)新增功能的位置。

> [!CAUTION]
>  CLongBinary 物件不能當做函式呼叫中的參數使用。 此外，它們的執行會呼叫 `::SQLGetData`，因此一定會使可滾動快照的滾動效能變慢。 當您使用 `::SQLGetData` 呼叫自己來取出動態架構資料行時，也可能會發生這種情況。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：取得 SUM 和其他彙總結果 (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)
