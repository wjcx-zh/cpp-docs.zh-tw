---
title: 記錄檢視類別的功能 (MFC 資料存取)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, classes
- record view classes
ms.assetid: e7b2820f-09c4-483f-83c0-317e8be42bdf
ms.openlocfilehash: 62597a3eb3f7a7e779ca57c9781565176df568d4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213430"
---
# <a name="features-of-record-view-classes--mfc-data-access"></a>記錄檢視類別的功能 (MFC 資料存取)

您可以使用類別[CFormView](../mfc/reference/cformview-class.md)進行表單架構的資料存取程式設計，但[CRecordView](../mfc/reference/crecordview-class.md)通常是衍生自的較佳類別。 除了其 `CFormView` 功能以外，`CRecordView`：

- 提供表單控制項和相關聯之記錄集物件之間的對話資料交換（DDX）。

- 先處理 Move、Move Next、Move Previous 和 Move 最後一個命令，以流覽相關聯的記錄集物件中的記錄。

- 當使用者移至另一筆記錄時，更新目前記錄的變更。

如需有關導覽的詳細資訊，請參閱[記錄視圖：支援記錄視圖中的導覽](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)。

## <a name="see-also"></a>另請參閱

[資料錄檢視 (MFC 資料存取)](../data/record-views-mfc-data-access.md)<br/>
[ODBC 驅動程式清單](../data/odbc/odbc-driver-list.md)
