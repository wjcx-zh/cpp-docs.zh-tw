---
title: 通用對話方塊類別
ms.date: 11/04/2016
helpviewer_keywords:
- dialog classes [MFC]
- dialog boxes [MFC], Windows common dialogs
- common dialog boxes [MFC], common dialog classes
- common dialog classes [MFC]
- MFC dialog boxes [MFC], Windows common dialogs
- Windows common dialogs [MFC]
- dialog classes [MFC], common
- common dialog boxes [MFC]
ms.assetid: 5c4f6443-896c-4b05-a7df-8169fdadc71d
ms.openlocfilehash: 2efe095a6d5b71321cbbe56fdee662509baa4573
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619028"
---
# <a name="common-dialog-classes"></a>通用對話方塊類別

除了類別[CDialog](reference/cdialog-class.md)，MFC 也提供數個衍生自的類別，以 `CDialog` 封裝常用的對話方塊，如下表所示。 封裝的對話方塊稱為「通用對話方塊」，屬於 Windows 通用對話方塊程式庫（COMMDLG。DLL）。 這些類別的對話方塊範本資源和程式碼是在屬於 Windows 3.1 版和更新版本的 Windows 通用對話方塊中提供。

### <a name="common-dialog-classes"></a>通用對話方塊類別

|衍生的對話方塊類別|目的|
|--------------------------|-------------|
|[CColorDialog](reference/ccolordialog-class.md)|讓使用者選取色彩。|
|[CFileDialog](reference/cfiledialog-class.md)|讓使用者選取要開啟或儲存的檔案名。|
|[CFindReplaceDialog](reference/cfindreplacedialog-class.md)|讓使用者在文字檔中起始尋找或取代作業。|
|[CFontDialog](reference/cfontdialog-class.md)|讓使用者指定字型。|
|[CPrintDialog](reference/cprintdialog-class.md)|讓使用者指定列印工作的資訊。|
|[CPrintDialogEx](reference/cprintdialogex-class.md)|Windows 列印屬性工作表。|

如需通用對話方塊類別的詳細資訊，請參閱*MFC 參考*中的個別類別名稱。 MFC 也提供一些用於 OLE 的標準對話方塊類別。 如需這些類別的詳細資訊，請參閱*MFC 參考*中的基類[COleDialog](reference/coledialog-class.md)。

MFC 中的其他三個類別具有類似對話的特性。 如需有關[CFormView](reference/cformview-class.md)、 [CRecordView](reference/crecordview-class.md)和[CDaoRecordView](reference/cdaorecordview-class.md)類別的詳細資訊，請參閱*MFC 參考*中的類別。 如需類別[CDialogBar](reference/cdialogbar-class.md)的詳細資訊，請參閱[對話方塊](dialog-bars.md)列。

## <a name="see-also"></a>另請參閱

[對話方塊](dialog-boxes.md)<br/>
[在 MFC 中使用對話方塊](life-cycle-of-a-dialog-box.md)<br/>
[OLE 中的對話方塊](dialog-boxes-in-ole.md)
