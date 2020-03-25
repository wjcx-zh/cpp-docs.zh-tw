---
title: MFC：使用具有文件和檢視的資料庫類別
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
ms.openlocfilehash: e2b073b20b9518667b43c30e7ee3199a84a3ad38
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213378"
---
# <a name="mfc-using-database-classes-with-documents-and-views"></a>MFC：使用具有文件和檢視的資料庫類別

您可以使用 MFC 資料庫類別搭配或不搭配檔/視圖架構。 本主題強調如何使用檔和視圖。 其中說明：

- 如何使用 `CRecordView` 物件[來撰寫表單架構應用程式](#_core_writing_a_form.2d.based_application)，做為檔的主要視圖。

- [如何在您的檔和視圖中使用記錄集物件](#_core_using_recordsets_in_documents_and_views)。

- [其他考慮](#_core_other_factors)。

如需替代方法，請參閱[MFC：使用沒有檔和視圖的資料庫類別](../data/mfc-using-database-classes-without-documents-and-views.md)。

##  <a name="writing-a-form-based-application"></a><a name="_core_writing_a_form.2d.based_application"></a>撰寫以表單為基礎的應用程式

許多資料存取應用程式都是以表單為基礎。 使用者介面是包含控制項的表單，使用者可在其中檢查、輸入或編輯資料。 若要讓您的應用程式表單為基礎，請使用類別 `CRecordView`。 當您執行 MFC 應用程式精靈，並在 [**資料庫支援**] 頁面上選取 [ **ODBC**用戶端類型] 時，專案會使用 view 類別的 `CRecordView`。

在以表單為基礎的應用程式中，每個記錄 view 物件都會儲存 `CRecordset` 物件的指標。 架構的記錄欄位交換（RFX）機制會在記錄集和資料來源之間交換資料。 對話資料交換（DDX）機制會在記錄集物件的欄位資料成員與表單上的控制項之間交換資料。 `CRecordView` 也會提供預設的命令處理常式函式，以便從記錄導覽至表單上的記錄。

若要使用應用程式精靈來建立表單架構應用程式，請參閱[建立以表單為基礎的 mfc](../mfc/reference/creating-a-forms-based-mfc-application.md)應用程式和[資料庫支援（MFC 應用程式精靈）](../mfc/reference/database-support-mfc-application-wizard.md)。

如需表單的完整討論，請參閱[記錄 Views](../data/record-views-mfc-data-access.md)。

##  <a name="using-recordsets-in-documents-and-views"></a><a name="_core_using_recordsets_in_documents_and_views"></a>在檔和視圖中使用記錄集

許多簡單的表單架構應用程式都不需要檔。 如果您的應用程式更複雜，您可能會想要使用檔作為資料庫的 proxy，並儲存連接至資料來源的 `CDatabase` 物件。 以表單為基礎的應用程式通常會在視圖中儲存記錄集物件的指標。 其他類型的資料庫應用程式會儲存記錄集，並 `CDatabase` 檔中的物件。 以下是在資料庫應用程式中使用檔的一些可能性：

- 如果您要存取本機內容中的記錄集，請視需要在檔或視圖的成員函式中，于本機建立 `CRecordset` 物件。

   將記錄集物件宣告為函式中的區域變數。 將 Null 傳遞至函式，這會導致架構為您建立並開啟暫存 `CDatabase` 物件。 或者，將指標傳遞給 `CDatabase` 物件。 使用函式中的記錄集，並讓它在函式結束時自動終結。

   當您將 Null 傳遞給記錄集的函式時，架構會使用記錄集之 `GetDefaultConnect` 成員函式所傳回的資訊來建立 `CDatabase` 物件並加以開啟。 這些嚮導會為您執行 `GetDefaultConnect`。

- 如果您在檔的存留期間存取記錄集，請在檔中內嵌一或多個 `CRecordset` 物件。

   當您初始化檔時，或視需要建立記錄集物件。 您可以撰寫函式，以傳回記錄集的指標（如果它已經存在），或如果記錄集尚未存在，則會加以結構和開啟。 視需要關閉、刪除和重新建立記錄集，或呼叫其 `Requery` 成員函式以重新整理記錄。

- 如果您要在檔的存留期間存取資料來源，請內嵌 `CDatabase` 物件，或在其中儲存 `CDatabase` 物件的指標。

   `CDatabase` 物件會管理與資料來源的連接。 在檔結構化期間，會自動建立物件，而當您初始化檔時，會呼叫其 `Open` 成員函式。 當您在檔成員函式中建立記錄集物件時，會將指標傳遞至檔的 `CDatabase` 物件。 這會使每個記錄集與其資料來源產生關聯。 當檔關閉時，通常會終結資料庫物件。 記錄集物件通常會在離開函式的範圍時終結。

##  <a name="other-factors"></a><a name="_core_other_factors"></a>其他因素

以表單為基礎的應用程式通常不會針對架構的**檔**序列化機制使用，因此您可能會想要移除、停用或取代 [檔案] 功能表上的 [**新增**] 和 [**開啟**] 命令。 請參閱[序列化：序列化和資料庫輸入/輸出](../mfc/serialization-serialization-vs-database-input-output.md)一文。

您可能也會想要利用架構可支援的許多使用者介面可能性。 例如，您可以在分隔器視窗中使用多個 `CRecordView` 物件、在不同的多重文件介面（MDI）子視窗中開啟多個記錄集等等。

您可能會想要在您的觀點中執行任何動作的列印，不論是使用 `CRecordView` 或其他東西來執行的表單。 作為衍生自 `CFormView`的類別，`CRecordView` 不支援列印，但是您可以覆寫 `OnPrint` 成員函式以允許列印。 如需詳細資訊，請參閱類別[CFormView](../mfc/reference/cformview-class.md)。

您可能不想要使用檔和視圖。 在此情況下，請參閱[MFC：使用沒有檔和視圖的資料庫類別](../data/mfc-using-database-classes-without-documents-and-views.md)。

## <a name="see-also"></a>另請參閱

[MFC 資料庫類別](../data/mfc-database-classes-odbc-and-dao.md)
