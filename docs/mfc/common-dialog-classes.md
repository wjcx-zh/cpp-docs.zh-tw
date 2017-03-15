---
title: "通用對話方塊類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "通用對話方塊 [C++]"
  - "通用對話方塊 [C++], 通用對話方塊類別"
  - "通用對話方塊類別 [C++]"
  - "對話方塊 [C++], Windows 通用對話方塊"
  - "對話方塊類別 [C++]"
  - "對話方塊類別 [C++], 通用"
  - "MFC 對話方塊, Windows 通用對話方塊"
  - "Windows 通用對話方塊 [C++]"
ms.assetid: 5c4f6443-896c-4b05-a7df-8169fdadc71d
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 通用對話方塊類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

除了類別 [CDialog](../mfc/reference/cdialog-class.md) 之外， MFC 提供封裝常用的對話方塊衍生自 `CDialog` 的數個類別，如下表所示。  封裝的對話方塊稱為「通用對話方塊」且為 Windows 通用對話程式庫 \(COMMDLG.DLL\) 的一部分。  這些類別的對話方塊樣板資源和程式碼都是 Windows 版本 3.1 的一部分和以後的 Windows 通用對話方塊所提供。  
  
### 通用對話方塊類別  
  
|衍生的對話方塊類別|用途|  
|---------------|--------|  
|[CColorDialog](../mfc/reference/ccolordialog-class.md)|讓使用者選取色彩。|  
|[CFileDialog](../mfc/reference/cfiledialog-class.md)|讓使用者選取要開啟或儲存的檔名。|  
|[CFindReplaceDialog](../mfc/reference/cfindreplacedialog-class.md)|讓使用者啟始尋找或取代文字檔中的作業。|  
|[CFontDialog](../mfc/reference/cfontdialog-class.md)|讓使用者指定字型。|  
|[CPrintDialog](../mfc/reference/cprintdialog-class.md)|讓使用者指定列印工作資訊。|  
|[CPrintDialogEx](../mfc/reference/cprintdialogex-class.md)|Windows 2000 列印屬性工作表。|  
  
 如需通用對話方塊類別的詳細資訊，請參閱《*MFC 參考*》中的個別類別名稱。  MFC 也提供用於 OLE 的一些準則對話方塊類別。  如需這些類別的詳細資訊，請參閱基底類別，在 *MFC 參考* 中的 [COleDialog](../mfc/reference/coledialog-class.md)。  
  
 在 MFC 中其他三個類別具有類似對話的特性。  如需類別 [CFormView](../mfc/reference/cformview-class.md)的資訊，請參閱 [CRecordView](../mfc/reference/crecordview-class.md)和 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)，請參閱《*MFC 參考*》中的類別。  如需類別 [CDialogBar](../mfc/reference/cdialogbar-class.md)的詳細資訊，請參閱 [對話方塊列](../mfc/dialog-bars.md)。  
  
## 請參閱  
 [對話方塊](../mfc/dialog-boxes.md)   
 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)   
 [OLE 中的對話方塊](../mfc/dialog-boxes-in-ole.md)