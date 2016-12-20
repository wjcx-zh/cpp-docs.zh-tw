---
title: "應用程式精靈所建立的記錄檢視程式碼 (MFC 資料存取) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "應用程式精靈 [C++], 資料錄檢視程式碼"
  - "資料錄檢視, 應用程式精靈程式碼"
  - "資料錄檢視, 重新整理控制項"
ms.assetid: 18fd4703-5939-491d-b759-985f767b951f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 應用程式精靈所建立的記錄檢視程式碼 (MFC 資料存取)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[MFC 應用程式精靈](../mfc/reference/database-support-mfc-application-wizard.md)會覆寫檢視的 `OnInitialUpdate` 和 `OnGetRecordset` 成員函式。  在架構建立框架視窗、文件和檢視之後，它會呼叫 `OnInitialUpdate` 來初始化檢視。  `OnInitialUpdate` 從文件中取得指向資料錄集的指標。  呼叫基底類別 [CView::OnInitialUpdate](../Topic/CView::OnInitialUpdate.md) 函式會開啟資料錄集。  下列程式碼將示範 `CRecordView` 的這項程序，`CDaoRecordView` 的程式碼很類似：  
  
```  
void CSectionForm::OnInitialUpdate()  
{  
   m_pSet = &GetDocument()->m_sectionSet;  
   CRecordView::OnInitialUpdate();  
}  
```  
  
 當資料錄集開啟時，它會選取資料錄。  [CRecordset::Open](../Topic/CRecordset::Open.md) 或[CDaoRecordset::Open](../Topic/CDaoRecordset::Open.md) 會製作第一個資料錄和目前資料錄，而 DDX 會將資料從資料錄集的欄位資料成員移至檢視中的對應表單控制項。  如需 RFX 的詳細資訊，請參閱[資料錄欄位交換 \(RFX\)](../data/odbc/record-field-exchange-rfx.md)。  如需 DDX 的詳細資訊，請參閱[對話方塊資料交換和驗證](../mfc/dialog-data-exchange-and-validation.md)。  如需文件\/檢視建立程序的詳細資訊，請參閱[使用類別來撰寫 Windows 的應用程式](../mfc/using-the-classes-to-write-applications-for-windows.md)。  
  
> [!NOTE]
>  您應該讓使用者可以從資料錄集重新整理資料錄檢視控制項。  沒有此功能時，如果使用者將控制項的值變更為不合法的值，該使用者可能會永久卡在目前的資料錄上。  若要重新整理控制項，請呼叫帶有參數 **FALSE** 的 `CWnd` 成員函式[UpdateData](../Topic/CWnd::UpdateData.md)。  
  
## 請參閱  
 [使用資料錄檢視](../data/using-a-record-view-mfc-data-access.md)