---
title: MFC:使用具有文件和檢視資料庫類別
ms.date: 11/04/2016
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
ms.openlocfilehash: 78765d17b52889123f13c492699230834decba66
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182895"
---
# <a name="mfc-using-database-classes-with-documents-and-views"></a>MFC:使用具有文件和檢視資料庫類別

使用或不使用文件/檢視架構，您可以使用 MFC 資料庫類別。 本主題著重在使用文件和檢視。 它會說明：

- [如何撰寫以 form 為基礎的應用程式](#_core_writing_a_form.2d.based_application)使用`CRecordView`為您的文件上的主要檢視的物件。

- [如何使用您的文件和檢視表中的資料錄集物件](#_core_using_recordsets_in_documents_and_views)。

- [其他考量](#_core_other_factors)。

替代項目，請參閱[MFC:使用不具文件和檢視的資料庫類別](../data/mfc-using-database-classes-without-documents-and-views.md)。

##  <a name="_core_writing_a_form.2d.based_application"></a> 撰寫以 Form 為基礎的應用程式

許多資料存取應用程式是以表單為基礎。 使用者介面是包含的控制項的使用者會檢查、 輸入，或編輯資料的表單。 若要讓基礎的應用程式表單，使用類別`CRecordView`。 當您執行 MFC 應用程式精靈，並選取**ODBC**上的用戶端型別**資料庫支援**頁面上，專案會使用`CRecordView`檢視類別。

在表單架構應用程式中，每個資料錄檢視物件儲存的指標`CRecordset`物件。 架構的資料錄欄位交換 (RFX) 機制之間交換資料的資料錄集和資料來源。 對話方塊資料交換 (DDX) 機制交換資料之間的資料錄集物件的欄位資料成員和表單上的控制項。 `CRecordView` 也提供預設命令處理常式函式在表單上巡覽記錄記錄。

若要使用應用程式精靈建立的以 form 為基礎的應用程式，請參閱[建立表單架構的 MFC 應用程式](../mfc/reference/creating-a-forms-based-mfc-application.md)並[MFC 應用程式精靈、 資料庫支援](../mfc/reference/database-support-mfc-application-wizard.md)。

表單的完整討論，請參閱 <<c0> [ 資料錄檢視](../data/record-views-mfc-data-access.md)。

##  <a name="_core_using_recordsets_in_documents_and_views"></a> 使用文件和檢視表中的資料錄集

許多簡單的表單架構應用程式不需要文件。 如果您的應用程式是更複雜，您可能想要使用做為 proxy 的文件資料庫，儲存`CDatabase`連接到資料來源的物件。 表單架構應用程式通常會儲存在檢視中的資料錄集物件的指標。 其他種類的資料庫應用程式儲存資料錄集和`CDatabase`文件中的物件。 以下是一些可能的資料庫應用程式中使用文件：

- 如果您要存取的資料錄集的本機環境中，建立`CRecordset`視需要在本機物件中的文件或檢視中，成員函式。

   宣告為區域變數函式中的資料錄集物件。 將 NULL 傳遞給建構函式，這會導致建立及開啟暫存 framework`CDatabase`為您的物件。 或者，將傳遞的指標`CDatabase`物件。 使用資料錄集內的函式，並讓它函式結束時自動終結。

   當您將 NULL 傳遞至資料錄集的建構函式時，架構會使用傳回的資料錄集的資訊`GetDefaultConnect`成員函式來建立`CDatabase`物件，並將它開啟。 這些精靈實作`GetDefaultConnect`您。

- 如果您要存取的資料錄集文件的存留期間，內嵌一個或多個`CRecordset`文件中的物件。

   當您初始化文件或視需要請建構資料錄集物件。 您可以撰寫資料錄集傳回的指標，如果已經存在或建構並開啟資料錄集，如果它尚不存在的函式。 關閉、 刪除和重新建立資料錄集，如有需要或呼叫其`Requery`成員函式來重新整理記錄。

- 如果您要存取的資料來源的文件的存留期間，內嵌`CDatabase`物件，或儲存的指標`CDatabase`裡面的物件。

   `CDatabase`物件會管理您的資料來源的連接。 文件在建構期間，會自動建構物件，並呼叫其`Open`成員函式時初始化文件。 當您建構文件成員函式中的資料錄集物件時，您將指標傳遞至文件的`CDatabase`物件。 這會將每個資料錄集關聯其資料來源。 文件關閉時，通常是損毀的資料庫物件。 資料錄集物件通常會在它們結束函式的範圍時終結。

##  <a name="_core_other_factors"></a> 其他因素

表單架構應用程式通常並沒有任何使用架構的文件序列化機制，因此您可能想要移除、 停用，或取代**的新**並**開啟**命令**檔案**功能表。 請參閱文章[序列化：序列化與資料庫輸入/輸出](../mfc/serialization-serialization-vs-database-input-output.md)。

您也可能會想要使用的架構可支援許多使用者介面可能性。 例如，您可以使用多個`CRecordView`物件在分隔器視窗中，開啟多個資料錄集不同多個文件介面 (MDI) 子視窗，等。

您可能想要實作列印中的檢視，無論是使用實作表單`CRecordView`或其他項目。 類別衍生自`CFormView`，`CRecordView`確實支援列印，但您可以覆寫`OnPrint`成員函式，允許進行列印。 如需詳細資訊，請參閱類別[CFormView](../mfc/reference/cformview-class.md)。

您可能不想要完全使用文件和檢視。 在此情況下，請參閱[MFC:使用不具文件和檢視的資料庫類別](../data/mfc-using-database-classes-without-documents-and-views.md)。

## <a name="see-also"></a>另請參閱

[MFC 資料庫類別](../data/mfc-database-classes-odbc-and-dao.md)