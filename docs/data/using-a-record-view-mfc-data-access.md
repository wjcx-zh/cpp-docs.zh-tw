---
title: 使用記錄檢視 (MFC 資料存取)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, customizing default code
ms.assetid: 91f2828f-0666-4273-ae28-e4703fd98521
ms.openlocfilehash: 611ddfd755eec84d4f2572a50c18802f988c5c3d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209023"
---
# <a name="using-a-record-view--mfc-data-access"></a>使用記錄檢視 (MFC 資料存取)

本主題說明通常如何自訂精靈為您撰寫的資料錄檢視的預設程式碼。 一般來說，您會想要使用[篩選準則](../data/odbc/recordset-filtering-records-odbc.md)或[參數](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)來限制記錄選取範圍，或許可以[排序](../data/odbc/recordset-sorting-records-odbc.md)記錄，並自訂 SQL 語句。

使用 `CRecordView` 與使用[CFormView](../mfc/reference/cformview-class.md)很相似。 基本方法是使用資料錄檢視顯示甚或更新單一資料錄集的記錄。 除此之外，您可能也會想要使用其他記錄集，如[記錄視圖：從第二個記錄集填入清單方塊](../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md)中所述。

## <a name="see-also"></a>另請參閱

[資料錄檢視 (MFC 資料存取)](../data/record-views-mfc-data-access.md)<br/>
[ODBC 驅動程式清單](../data/odbc/odbc-driver-list.md)
