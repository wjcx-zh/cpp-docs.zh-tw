---
title: 應用程式精靈所建立的記錄檢視程式碼 (MFC 資料存取)
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [C++], record view code
- record views, refreshing controls
- record views, application wizard code
ms.assetid: 18fd4703-5939-491d-b759-985f767b951f
ms.openlocfilehash: 69bebe978d03e5777f20765ac0bcf9a344f69320
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209153"
---
# <a name="record-view-code-created-by-application-wizard--mfc-data-access"></a>應用程式精靈所建立的記錄檢視程式碼 (MFC 資料存取)

[MFC 應用程式精靈](../mfc/reference/database-support-mfc-application-wizard.md)會覆寫視圖的 `OnInitialUpdate` 和 `OnGetRecordset` 成員函式。 在架構建立框架視窗、文件和檢視之後，它會呼叫 `OnInitialUpdate` 來初始化檢視。 `OnInitialUpdate` 從文件中取得指向資料錄集的指標。 基類[CView：： OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)函數的呼叫會開啟記錄集。 下列程式碼會顯示 `CRecordView`的這個進程：

```cpp
void CSectionForm::OnInitialUpdate()
{
   m_pSet = &GetDocument()->m_sectionSet;
   CRecordView::OnInitialUpdate();
}
```

當資料錄集開啟時，它會選取資料錄。 [CRecordset：： Open](../mfc/reference/crecordset-class.md#open)會使第一個記錄成為目前的記錄，而 DDX 會將資料從記錄集的欄位資料成員移至視圖中的對應表單控制項。 如需 RFX 的詳細資訊，請參閱[記錄欄位交換（RFX）](../data/odbc/record-field-exchange-rfx.md)。 如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../mfc/dialog-data-exchange-and-validation.md)。 如需檔/視圖建立程式的相關資訊，請參閱[使用類別來撰寫適用于 Windows 的應用程式](../mfc/using-the-classes-to-write-applications-for-windows.md)。

> [!NOTE]
>  您應該讓使用者可以從資料錄集重新整理資料錄檢視控制項。 沒有此功能時，如果使用者將控制項的值變更為不合法的值，該使用者可能會永久卡在目前的資料錄上。 若要重新整理控制項，請呼叫 `CWnd` 成員函式[UpdateData](../mfc/reference/cwnd-class.md#updatedata) ，並將參數設為 FALSE。

## <a name="see-also"></a>另請參閱

[使用記錄視圖](../data/using-a-record-view-mfc-data-access.md)
