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
ms.openlocfilehash: 872fa7229738314b86b6ae6c0d5dc5a5562b27f1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360607"
---
# <a name="recordset-working-with-large-data-items-odbc"></a>資料錄集：使用大型的資料項目 (ODBC)

本主題適用於 MFC ODBC 類和 MFC DAO 類。

> [!NOTE]
> 如果使用 MFC DAO 類,請使用類[CByteArray](../../mfc/reference/cbytearray-class.md)而不是[CLongBinary](../../mfc/reference/clongbinary-class.md)管理大型數據項。 如果使用具有大量的 MFC ODBC,請使用`CLongBinary`而不是`CByteArray`。 有關批量行提取的詳細資訊,請參閱[記錄集:批量提取記錄 (ODBC)。](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

假設您的資料庫可以存儲大量數據,如位圖(員工照片、地圖、產品圖片、OLE 物件等)。 此類資料通常稱為二進位元組物件(或 BLOB),因為:

- 每個欄位值都很大。

- 與數位和其他簡單數據類型不同,它沒有可預測的大小。

- 從程式的角度來看,數據是無成形的。

本主題介紹資料庫類為處理此類物件提供哪些支援。

## <a name="managing-large-objects"></a><a name="_core_managing_large_objects"></a>管理大型物件

記錄集有兩種方法可以解決管理二進位大型物件的特殊困難。 您可以使用類別[CByteArray,](../../mfc/reference/cbytearray-class.md)也可以使用[CLongBinary](../../mfc/reference/clongbinary-class.md)類別 。 通常,`CByteArray`是管理大型二進位數據的首選方法。

`CByteArray`所需的開銷比`CLongBinary`但更有能力,如[CByteArray 類](#_core_the_cbytearray_class)中所述。 `CLongBinary`在[CLongBinary 類](#_core_the_clongbinary_class)中簡要描述。

有關使用`CByteArray`大型資料項的詳細資訊,請參閱[技術說明 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md)。

## <a name="cbytearray-class"></a><a name="_core_the_cbytearray_class"></a>C位元組類別

`CByteArray`是 MFC 集合類之一。 `CByteArray`物件儲存位元組的動態數位 - 如果需要,陣列可以增長。 類提供按索引快速訪問,與內置C++數位一樣。 `CByteArray`出於診斷目的,可以序列化並轉儲物件。 類提供成員函數,用於獲取和設置指定的位元組、插入和追加位元組以及刪除一個字節或所有位元組。 這些功能使分析二進位數據更容易。 例如,如果二進位物件是 OLE 物件,則可能需要處理某些標頭位元組才能到達實際物件。

## <a name="using-cbytearray-in-recordsets"></a><a name="_core_using_cbytearray_in_recordsets"></a>在紀錄集中使用 CByteArray

通過為記錄集的欄位數據成員提供類型`CByteArray`,可以提供固定的基[,RFX](../../data/odbc/record-field-exchange-rfx.md)可以從中管理記錄集和數據源之間的此類物件的傳輸,並透過該庫操作物件內的數據。 RFX 需要一個用於檢索數據的特定網站,並且您需要一種方法來訪問基礎數據。

有關使用`CByteArray`大型資料項的詳細資訊,請參閱[技術說明 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md)。

## <a name="clongbinary-class"></a><a name="_core_the_clongbinary_class"></a>CLongBinary 類別

[CLongBinary](../../mfc/reference/clongbinary-class.md)對像是`HGLOBAL`圍繞 句柄對堆上分配的存儲塊的簡單外殼。 當它綁定包含二進位大型物件的表列時,RFX 在需要將資料傳輸`HGLOBAL`到 記錄集並將句柄存儲在`CLongBinary`記錄集 的欄位中時分配句柄。

反過來,使用`HGLOBAL`句`m_hData`柄 , 處理數據本身, 操作它,就像對任何句柄數據一樣. 這是[CByteArray](../../mfc/reference/cbytearray-class.md)添加功能的位置。

> [!CAUTION]
> CLongBinary 物件不能用作函數調用中的參數。 此外,它們的實現(調用`::SQLGetData`)必然會降低可滾動快照的滾動性能。 當您使用`::SQLGetData`自己調用來檢索動態架構列時,情況可能也是如此。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：取得 SUM 和其他彙總結果 (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[記錄現場交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)
