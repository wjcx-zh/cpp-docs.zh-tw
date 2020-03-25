---
title: 記錄檢視 (MFC 資料存取)
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], record views
- ODBC recordsets [C++], record views
- databases [C++], record views
- record views [C++]
- forms [C++], data access tasks
ms.assetid: 562122d9-01d8-4284-acf6-ea109ab0408d
ms.openlocfilehash: 31dbd92219f263c625050524279b97ef38ba9ba1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209127"
---
# <a name="record-views--mfc-data-access"></a>記錄檢視 (MFC 資料存取)

本節僅適用于 MFC ODBC 類別。 如需 OLE DB 記錄 視圖的詳細資訊，請參閱[COleDBRecordView](../mfc/reference/coledbrecordview-class.md)和[使用 OLE DB 記錄 views](../data/oledb/using-ole-db-record-views.md)。

為了支援表單架構的資料存取應用程式，類別庫提供類別[CRecordView](../mfc/reference/crecordview-class.md)。 [記錄] 視圖是表單檢視物件，其控制項直接對應至[記錄集](../data/odbc/recordset-odbc.md)物件的欄位資料成員（並間接對應至資料來源上查詢結果或資料表中的對應資料行）。 如同其基類[CFormView](../mfc/reference/cformview-class.md)，`CRecordView` 是以對話方塊範本資源為基礎。

## <a name="form-uses"></a>表單用途

表單對於各種資料存取工作非常有用：

- 輸入資料

- 執行資料的唯讀檢查

- 更新資料

## <a name="further-reading-about-record-views"></a>深入了解資料錄檢視

主題中的資料適用於 ODBC 架構和 DAO 架構類別。 若為 ODBC 請使用 `CRecordView`，若為 DAO 則使用 `CDaoRecordView`。

主題包括：

- [記錄視圖類別的功能](../data/features-of-record-view-classes-mfc-data-access.md)

- [記錄視圖的資料交換](../data/data-exchange-for-record-views-mfc-data-access.md)

- [您在使用記錄視圖時的角色](../data/your-role-in-working-with-a-record-view-mfc-data-access.md)

- [設計和建立記錄視圖](../data/designing-and-creating-a-record-view-mfc-data-access.md)

- [使用記錄視圖](../data/using-a-record-view-mfc-data-access.md)

## <a name="see-also"></a>另請參閱

[資料存取程式設計 (MFC/ATL)](../data/data-access-programming-mfc-atl.md)<br/>
[ODBC 驅動程式清單](../data/odbc/odbc-driver-list.md)
