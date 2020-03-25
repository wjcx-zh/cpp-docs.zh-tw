---
title: 您在使用記錄檢視上的角色 (MFC 資料存取)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, customizing default code
- MFC, record views
ms.assetid: 691e89a5-ff21-4ca3-9278-69d4678288bb
ms.openlocfilehash: 351aa2d5ce950017aa8c1b3d99c8d297a423ad9f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208997"
---
# <a name="your-role-in-working-with-a-record-view--mfc-data-access"></a>您在使用記錄檢視上的角色 (MFC 資料存取)

下表顯示您通常必須執行什麼操作才能使用資料錄檢視以及該架構為您執行什麼操作。

### <a name="working-with-a-record-view-you-and-the-framework"></a>使用資料錄檢視：您與架構

|您|架構|
|---------|-------------------|
|使用 Visual C++ 的話方塊編輯器來設計表單。|建立對話方塊樣板資源 (含控制項)。|
|使用[MFC 應用程式精靈](../mfc/reference/database-support-mfc-application-wizard.md)來建立衍生自[CRecordView](../mfc/reference/crecordview-class.md)和[CRecordset](../mfc/reference/crecordset-class.md)的類別。|為您撰寫類別。|
|將資料錄檢視控制項對應至資料錄集欄位資料成員。|提供控制項與資料錄集欄位之間的 DDX。|
||提供預設的命令處理常式，以在功能表或工具列按鈕上**先移動**、**移動最後**一個、**移動下一個**，以及**移動先前**的命令。|
||將變更更新到資料來源。|
|[選用] 撰寫程式碼，以第二個資料錄集中的資料填入清單方塊或下拉式方塊或是其他控制項。||
|[選用] 針對任何特殊驗證撰寫程式碼。||
|[選用] 撰寫程式碼來加入或刪除資料錄。||

表單架構程式設計是唯一一個使用資料庫的方法。 如需使用其他使用者介面或無使用者介面之應用程式的相關資訊，請參閱[mfc：使用具有檔和視圖的資料庫類別](../data/mfc-using-database-classes-with-documents-and-views.md)和[Mfc：使用沒有檔和視圖的資料庫類別](../data/mfc-using-database-classes-without-documents-and-views.md)。 如需顯示資料庫記錄的替代方法，請參閱類別[CListView](../mfc/reference/clistview-class.md)和[CTreeView](../mfc/reference/ctreeview-class.md)。

## <a name="see-also"></a>另請參閱

[資料錄檢視 (MFC 資料存取)](../data/record-views-mfc-data-access.md)<br/>
[ODBC 驅動程式清單](../data/odbc/odbc-driver-list.md)
