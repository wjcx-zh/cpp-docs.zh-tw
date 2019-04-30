---
title: 記錄檢視類別的功能 (MFC 資料存取)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, classes
- record view classes
ms.assetid: e7b2820f-09c4-483f-83c0-317e8be42bdf
ms.openlocfilehash: 5f8de956065571109c988bd2940d21822bba7cfd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397948"
---
# <a name="features-of-record-view-classes--mfc-data-access"></a>記錄檢視類別的功能 (MFC 資料存取)

您可以使用類別的以 form 為基礎的資料存取程式設計[CFormView](../mfc/reference/cformview-class.md)，但[CRecordView](../mfc/reference/crecordview-class.md)通常是較佳的類別衍生自。 除了其`CFormView`功能， `CRecordView`:

- 提供表單控制項和相關聯的資料錄集物件之間的對話資料交換 (DDX)。

- 處理移到最前面、 移到下一個、 移到上一個和最後一個移動瀏覽的記錄相關聯的資料錄集物件中的命令。

- 如果使用者移到另一筆記錄，更新會變更為目前的記錄。

如需有關瀏覽的詳細資訊，請參閱[資料錄檢視：支援資料錄檢視的瀏覽](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)。

## <a name="see-also"></a>另請參閱

[資料錄檢視 (MFC 資料存取)](../data/record-views-mfc-data-access.md)<br/>
[ODBC 驅動程式清單](../data/odbc/odbc-driver-list.md)