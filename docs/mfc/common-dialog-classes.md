---
title: 通用對話方塊類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1cb8a9bacf7414a5a2fff246d796c94a8a1598d7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342211"
---
# <a name="common-dialog-classes"></a>通用對話方塊類別
除了類別之外[CDialog](../mfc/reference/cdialog-class.md)，MFC 還提供數個類別衍生自`CDialog`的封裝通常使用的對話方塊下, 表所示。 封裝的對話方塊稱為 「 通用對話方塊 」，則 Windows 通用對話方塊程式庫的一部分 (COMMDLG。DLL)。 對話方塊範本資源和程式碼，這些類別提供 Windows 通用對話方塊屬於 Windows 3.1 和更新版本的版本。  
  
### <a name="common-dialog-classes"></a>通用對話方塊類別  
  
|在衍生的對話方塊類別|用途|  
|--------------------------|-------------|  
|[CColorDialog](../mfc/reference/ccolordialog-class.md)|可讓使用者選取色彩。|  
|[CFileDialog](../mfc/reference/cfiledialog-class.md)|可讓使用者選擇開啟或儲存檔案名稱。|  
|[CFindReplaceDialog](../mfc/reference/cfindreplacedialog-class.md)|可讓使用者起始的尋找或取代文字檔案中的作業。|  
|[CFontDialog](../mfc/reference/cfontdialog-class.md)|可讓使用者指定的字型。|  
|[CPrintDialog](../mfc/reference/cprintdialog-class.md)|可讓使用者指定的列印工作資訊。|  
|[CPrintDialogEx](../mfc/reference/cprintdialogex-class.md)|Windows 列印屬性工作表。|  
  
 如需通用對話方塊類別的詳細資訊，請參閱中的個別的類別名稱*MFC 參考*。 MFC 也提供數個用於 OLE 的標準對話方塊類別。 如需這些類別資訊，請參閱基底類別， [COleDialog](../mfc/reference/coledialog-class.md)，請在*MFC 參考*。  
  
 在 MFC 中的其他三個類別具有類似對話方塊的特性。 如需類別資訊[CFormView](../mfc/reference/cformview-class.md)， [CRecordView](../mfc/reference/crecordview-class.md)，和[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)，請參閱中的類別*MFC 參考*。 如需類別資訊[CDialogBar](../mfc/reference/cdialogbar-class.md)，請參閱[對話方塊列](../mfc/dialog-bars.md)。  
  
## <a name="see-also"></a>另請參閱  
 [對話方塊](../mfc/dialog-boxes.md)   
 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)   
 [OLE 中的對話方塊](../mfc/dialog-boxes-in-ole.md)

