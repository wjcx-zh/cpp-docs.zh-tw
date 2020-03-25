---
title: 記錄捲動的命令處理常式 (MFC 資料存取)
ms.date: 11/04/2016
helpviewer_keywords:
- record views [C++], scrolling
- record scrolling [C++]
- scrolling records
ms.assetid: f8b13477-2a37-459e-a30c-806fb78165ac
ms.openlocfilehash: 8bbacd6625e846381d2bafc8133e8b36efe51b1a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213443"
---
# <a name="command-handlers-for-record-scrolling--mfc-data-access"></a>記錄捲動的命令處理常式 (MFC 資料存取)

[CRecordView](../mfc/reference/crecordview-class.md)類別會針對下列標準命令提供預設的命令處理：

- ID_RECORD_MOVE_FIRST

- ID_RECORD_MOVE_LAST

- ID_RECORD_MOVE_NEXT

- ID_RECORD_MOVE_PREV

`OnMove` 成員函式會針對所有四個命令提供預設的命令處理，這會從記錄移至記錄。 發出這些命令時，RFX (或 DFX) 會將新的記錄載入記錄集的欄位，DDX 則將值移到記錄表單的控制項中。 如需 RFX 的詳細資訊，請參閱[記錄欄位交換（RFX）](../data/odbc/record-field-exchange-rfx.md)。

> [!NOTE]
>  請務必為與標準記錄巡覽命令相關聯的任何使用者介面物件，使用這些標準命令 ID。

## <a name="see-also"></a>另請參閱

[支援記錄視圖中的導覽](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)
