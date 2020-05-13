---
title: 應用程式精靈所建立的記錄檢視程式碼 (MFC 資料存取)
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [C++], record view code
- record views, refreshing controls
- record views, application wizard code
ms.assetid: 18fd4703-5939-491d-b759-985f767b951f
ms.openlocfilehash: 69481299980329b98e378f02e090670fa3d7ece2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376025"
---
# <a name="record-view-code-created-by-application-wizard--mfc-data-access"></a>應用程式精靈所建立的記錄檢視程式碼 (MFC 資料存取)

[MFC 應用程式精靈](../mfc/reference/database-support-mfc-application-wizard.md)覆蓋檢視和`OnInitialUpdate``OnGetRecordset`成員函數。 在架構建立框架視窗、文件和檢視之後，它會呼叫 `OnInitialUpdate` 來初始化檢視。 `OnInitialUpdate` 從文件中取得指向資料錄集的指標。 對基類[CView::on 初始更新](../mfc/reference/cview-class.md#oninitialupdate)函數的調用將打開記錄集。 以下代碼顯示了`CRecordView`的 此過程:

```cpp
void CSectionForm::OnInitialUpdate()
{
   m_pSet = &GetDocument()->m_sectionSet;
   CRecordView::OnInitialUpdate();
}
```

當資料錄集開啟時，它會選取資料錄。 [CRecordset::打開](../mfc/reference/crecordset-class.md#open)使第一個記錄成為當前記錄,DDX 將數據從記錄集的欄位數據成員移動到視圖中的相應窗體控件。 有關 RFX 的詳細資訊,請參閱[記錄欄位交換 (RFX)。](../data/odbc/record-field-exchange-rfx.md) 如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../mfc/dialog-data-exchange-and-validation.md)。 關於文件/檢視建立行程的資訊,請參閱[使用類為 Windows 編寫應用程式](../mfc/using-the-classes-to-write-applications-for-windows.md)。

> [!NOTE]
> 您應該讓使用者可以從資料錄集重新整理資料錄檢視控制項。 沒有此功能時，如果使用者將控制項的值變更為不合法的值，該使用者可能會永久卡在目前的資料錄上。 要刷新控制項,請使用 FALSE`CWnd`參數呼叫成員函數[UpdateData。](../mfc/reference/cwnd-class.md#updatedata)

## <a name="see-also"></a>另請參閱

[使用資料錄檢視](../data/using-a-record-view-mfc-data-access.md)
