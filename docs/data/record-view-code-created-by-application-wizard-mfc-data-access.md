---
title: 應用程式精靈所建立的記錄檢視程式碼 (MFC 資料存取)
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [C++], record view code
- record views, refreshing controls
- record views, application wizard code
ms.assetid: 18fd4703-5939-491d-b759-985f767b951f
ms.openlocfilehash: e25ca9cad1390dd11ab7328ffefed31badf6fc0b
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59036071"
---
# <a name="record-view-code-created-by-application-wizard--mfc-data-access"></a>應用程式精靈所建立的記錄檢視程式碼 (MFC 資料存取)

[MFC 應用程式精靈](../mfc/reference/database-support-mfc-application-wizard.md)覆寫檢視`OnInitialUpdate`和`OnGetRecordset`成員函式。 在架構建立框架視窗、文件和檢視之後，它會呼叫 `OnInitialUpdate` 來初始化檢視。 `OnInitialUpdate` 從文件中取得資料錄集的指標。 基底類別呼叫[cview:: Oninitialupdate](../mfc/reference/cview-class.md#oninitialupdate)函式會開啟資料錄集。 下列程式碼示範此程序`CRecordView`:

```cpp
void CSectionForm::OnInitialUpdate()
{
   m_pSet = &GetDocument()->m_sectionSet;
   CRecordView::OnInitialUpdate();
}
```

當資料錄集開啟時，它會選取資料錄。 [Crecordset:: Open](../mfc/reference/crecordset-class.md#open) DDX 會將資料從資料錄集的欄位資料成員對應表單控制項檢視中與目前的記錄，讓第一筆記錄。 如需 RFX 的詳細資訊，請參閱[資料錄欄位交換 (RFX)](../data/odbc/record-field-exchange-rfx.md)。 如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../mfc/dialog-data-exchange-and-validation.md)。 在文件/檢視建立程序的相關資訊，請參閱[使用類別來撰寫應用程式的 Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)。

> [!NOTE]
>  您應該讓使用者可以從資料錄集重新整理資料錄檢視控制項。 沒有此功能時，如果使用者將控制項的值變更為不合法的值，該使用者可能會永久卡在目前的資料錄上。 若要重新整理控制項，請呼叫`CWnd`成員函式[UpdateData](../mfc/reference/cwnd-class.md#updatedata)具有 FALSE 的參數。

## <a name="see-also"></a>另請參閱

[使用資料錄檢視](../data/using-a-record-view-mfc-data-access.md)