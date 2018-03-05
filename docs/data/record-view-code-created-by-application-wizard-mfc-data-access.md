---
title: "記錄由應用程式精靈 （MFC 資料存取） 所建立的檢視程式碼 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- application wizards [C++], record view code
- record views, refreshing controls
- record views, application wizard code
ms.assetid: 18fd4703-5939-491d-b759-985f767b951f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 239ace3f23987bc4f704515e7f87d62ba2e26543
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="record-view-code-created-by-application-wizard--mfc-data-access"></a>應用程式精靈所建立的記錄檢視程式碼 (MFC 資料存取)
[MFC 應用程式精靈](../mfc/reference/database-support-mfc-application-wizard.md)覆寫檢視`OnInitialUpdate`和`OnGetRecordset`成員函式。 在架構建立框架視窗、文件和檢視之後，它會呼叫 `OnInitialUpdate` 來初始化檢視。 `OnInitialUpdate` 從文件中取得指向資料錄集的指標。 基底類別呼叫[cview:: Oninitialupdate](../mfc/reference/cview-class.md#oninitialupdate)函式會開啟資料錄集。 下列程式碼將示範此程序`CRecordView`:  
  
```  
void CSectionForm::OnInitialUpdate()  
{  
   m_pSet = &GetDocument()->m_sectionSet;  
   CRecordView::OnInitialUpdate();  
}  
```  
  
 當資料錄集開啟時，它會選取資料錄。 [Crecordset:: Open](../mfc/reference/crecordset-class.md#open)讓目前的記錄和 DDX 會將資料從資料錄集的欄位資料成員對應表單控制項檢視中的第一筆記錄。 如需 RFX 的詳細資訊，請參閱[資料錄欄位交換 (RFX)](../data/odbc/record-field-exchange-rfx.md)。 如需有關 DDX 的詳細資訊，請參閱[對話方塊資料交換和驗證](../mfc/dialog-data-exchange-and-validation.md)。 在文件/檢視建立程序的相關資訊，請參閱[使用類別來撰寫 Windows 應用程式](../mfc/using-the-classes-to-write-applications-for-windows.md)。  
  
> [!NOTE]
>  您應該讓終端使用者可以從資料錄集重新整理資料錄檢視控制項。 沒有此功能時，如果使用者將控制項的值變更為不合法的值，該使用者可能會永久卡在目前的資料錄上。 若要重新整理控制項，您呼叫`CWnd`成員函式[UpdateData](../mfc/reference/cwnd-class.md#updatedata)和參數**FALSE**。  
  
## <a name="see-also"></a>請參閱  
 [使用資料錄檢視](../data/using-a-record-view-mfc-data-access.md)