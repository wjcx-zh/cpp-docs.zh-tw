---
title: 記錄捲動的命令處理常式 (MFC 資料存取)
ms.date: 11/04/2016
helpviewer_keywords:
- record views [C++], scrolling
- record scrolling [C++]
- scrolling records
ms.assetid: f8b13477-2a37-459e-a30c-806fb78165ac
ms.openlocfilehash: 14ef845c3029f1d9a30d257f91c1b33017b6ec8b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336934"
---
# <a name="command-handlers-for-record-scrolling--mfc-data-access"></a>記錄捲動的命令處理常式 (MFC 資料存取)

[CRecordView](../mfc/reference/crecordview-class.md)類別指令提供預設指令處理:

- ID_RECORD_MOVE_FIRST

- ID_RECORD_MOVE_LAST

- ID_RECORD_MOVE_NEXT

- ID_RECORD_MOVE_PREV

成員`OnMove`函數為所有四個命令提供預設命令處理,這些命令從記錄移動到記錄。 發出這些命令時，RFX (或 DFX) 會將新的記錄載入記錄集的欄位，DDX 則將值移到記錄表單的控制項中。 有關 RFX 的資訊,請參閱[記錄欄位交換 (RFX)。](../data/odbc/record-field-exchange-rfx.md)

> [!NOTE]
> 請務必為與標準記錄巡覽命令相關聯的任何使用者介面物件，使用這些標準命令 ID。

## <a name="see-also"></a>另請參閱

[支援資料錄檢視的巡覽](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)
