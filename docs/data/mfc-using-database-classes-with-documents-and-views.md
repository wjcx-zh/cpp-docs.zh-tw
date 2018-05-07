---
title: MFC： 使用具有文件和檢視的資料庫類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- documents [C++], database applications
- recordsets [C++], documents and views
- CRecordView class, using in database forms
- views [C++], database applications
- forms [C++], database applications
- record views [C++], form-based applications
- document/view architecture [C++], in databases
- database applications [C++], forms
- database classes [C++], MFC
- ODBC recordsets [C++], documents and views
- ODBC [C++], forms
ms.assetid: 83979974-fc63-46ac-b162-e8403a572e2c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fcaee376b53c1d592f02aafc830a35d72f64feeb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-using-database-classes-with-documents-and-views"></a>MFC：使用具有文件和檢視的資料庫類別
使用或不使用文件/檢視架構，您可以使用 MFC 資料庫類別。 本主題將強調使用文件和檢視。 它會說明：  
  
-   [如何撰寫表單架構應用程式](#_core_writing_a_form.2d.based_application)使用`CRecordView`物件做為文件上的主要檢視。  
  
-   [如何使用文件和檢視中的資料錄集物件](#_core_using_recordsets_in_documents_and_views)。  
  
-   [其他考量](#_core_other_factors)。  
  
 替代項目，請參閱[MFC： 使用資料庫類別不具文件和檢視表](../data/mfc-using-database-classes-without-documents-and-views.md)。  
  
##  <a name="_core_writing_a_form.2d.based_application"></a> 撰寫表單架構應用程式  
 許多資料存取應用程式是以表單為基礎。 使用者介面是包含的控制項，使用者會檢查、 輸入，或編輯資料的表單。 若要讓基礎的應用程式表單，請使用類別`CRecordView`。 當您執行 MFC 應用程式精靈，並選取**ODBC**上的用戶端類型**資料庫支援** 頁面上，該專案使用`CRecordView`檢視類別。
  
 在表單架構應用程式中，每個資料錄檢視物件儲存的指標`CRecordset`物件。 架構的資料錄欄位交換 (RFX) 機制之間交換資料的資料錄集和資料來源。 對話方塊資料交換 (DDX) 機制交換資料之間的資料錄集物件的欄位資料成員和表單上的控制項。 `CRecordView` 也提供預設命令處理常式函式在表單上巡覽記錄記錄。  
  
 若要建立表單架構應用程式使用應用程式精靈，請參閱[建立表單架構的 MFC 應用程式](../mfc/reference/creating-a-forms-based-mfc-application.md)和[MFC 應用程式精靈、 資料庫支援](../mfc/reference/database-support-mfc-application-wizard.md)。  
  
 如需表單的完整討論，請參閱[資料錄檢視](../data/record-views-mfc-data-access.md)。  
  
##  <a name="_core_using_recordsets_in_documents_and_views"></a> 使用文件和檢視中的資料錄集  
 許多簡單的表單架構應用程式不需要文件。 如果您的應用程式更複雜，您可能想要使用的資料庫做為 proxy 的文件時，儲存`CDatabase`連接到資料來源的物件。 表單架構應用程式通常會儲存在檢視中的資料錄集物件的指標。 其他種類的資料庫應用程式儲存資料錄集和`CDatabase`文件中的物件。 以下是一些可能的資料庫應用程式中使用文件：  
  
-   如果您要存取的本機環境中的資料錄集，請建立`CRecordset`視需要在本機物件中的文件或檢視中，成員函式。  
  
     將資料錄集物件宣告為函式中的區域變數。 傳遞**NULL**建構函式，而導致架構，以建立及開啟暫存`CDatabase`為您的物件。 或者，傳遞指標`CDatabase`物件。 使用資料錄集內的函式，並讓它的函式結束時自動終結。  
  
     當您將傳遞**NULL**資料錄集建構函式，架構會使用傳回的資料錄集的資訊`GetDefaultConnect`成員函式來建立`CDatabase`物件，並將它開啟。 這些精靈實作`GetDefaultConnect`您。  
  
-   如果您要存取資料錄集文件的存留期間，內嵌一或多個`CRecordset`文件中的物件。  
  
     初始化文件或視需要請建構資料錄集物件。 您可以撰寫資料錄集傳回的指標，如果已經存在或建構，而且如果它尚未存在，就會開啟資料錄集的函式。 關閉、 刪除和重新建立資料錄集，如有需要或呼叫其**Requery**成員函式以重新整理記錄。  
  
-   如果您要存取資料來源文件的存留期間，內嵌`CDatabase`或物件的指標儲存至`CDatabase`中它的物件。  
  
     `CDatabase`物件會管理您的資料來源的連接。 文件在建構期間，自動建構物件，並呼叫其**開啟**成員函式時初始化文件。 建構時文件成員函式中的資料錄集物件，您將指標傳遞至文件的`CDatabase`物件。 這樣會將每個資料錄集關聯與其資料來源。 在文件關閉時，通常就會終結資料庫物件。 當離開函式範圍，通常會終結資料錄集物件。  
  
##  <a name="_core_other_factors"></a> 其他因素  
 表單架構應用程式通常不需要使用任何架構的文件序列化機制，因此您可能想要移除、 停用，或取代`New`和**開啟**命令**檔案**功能表。 請參閱文章[序列化： 序列化 vs。資料庫輸入/輸出](../mfc/serialization-serialization-vs-database-input-output.md)。  
  
 您可能也要使用的架構可以支援的許多使用者介面可能性。 例如，您可以使用多個`CRecordView`物件在分隔視窗中，開啟多個資料錄集不同的多個文件介面 (MDI) 子視窗，等。  
  
 您可能想要實作的任何檢視中的列印，無論是透過實作表單`CRecordView`或其他項目。 為類別衍生自`CFormView`，`CRecordView`確實支援列印，但是您可以覆寫`OnPrint`允許列印成員函式。 如需詳細資訊，請參閱類別[CFormView](../mfc/reference/cformview-class.md)。  
  
 您可能不想使用完全使用文件和檢視。 在此情況下，請參閱[MFC： 使用資料庫類別不具文件和檢視表](../data/mfc-using-database-classes-without-documents-and-views.md)。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 資料庫類別 (../ data/mfc-database-classes-odbc-and-dao.md）