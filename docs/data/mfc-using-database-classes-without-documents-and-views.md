---
title: MFC：使用不具文件和檢視的資料庫類別
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC applications [C++], without views
- documents [C++], applications without
- ODBC applications [C++]
- document/view architecture [C++], in databases
- files [C++], MFC
- database classes [C++], MFC
- CRecordView class, using in database applications
- database applications [C++], without views
- database applications [C++], application wizard options
- application wizards [C++], creating database applications
- ODBC [C++], file support in database applications
- ODBC applications [C++], without documents
- database applications [C++], without documents
- user interface [C++], drawing information
ms.assetid: 15bf52d4-91cf-4b1d-8b37-87c3ae70123a
ms.openlocfilehash: 57a7abd89bc9bfb465912a35c21f9780668f4466
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213352"
---
# <a name="mfc-using-database-classes-without-documents-and-views"></a>MFC：使用不具文件和檢視的資料庫類別

有時候，您可能不會想要在資料庫應用程式中使用架構的檔/視圖架構。 本主題將說明：

- [當您不需要使用](#_core_when_you_don.92.t_need_documents)檔序列化這類檔時。

- [應用程式精靈選項](#_core_appwizard_options_for_documents_and_views)可支援沒有序列化的應用程式，而且沒有**檔**相關的檔案功能表命令，例如新增、**開啟**、**儲存**和**另存** **新**檔。

- [如何使用最少使用檔的應用程式](#_core_applications_with_minimal_documents)。

- [如何不使用檔或視圖來結構應用程式](#_core_applications_with_no_document)。

##  <a name="when-you-do-not-need-documents"></a><a name="_core_when_you_don.92.t_need_documents"></a>當您不需要檔時

有些應用程式有不同的檔概念。 這些應用程式通常會使用 [**開啟**檔案] 命令，將所有或大部分檔案從儲存體載入記憶體中。 他們會使用 [檔案] **[儲存] 或 [** **另存**新檔] 命令，一次將更新的檔案寫回儲存體。 使用者看到的是資料檔案。

不過，某些類別的應用程式不需要檔。 資料庫應用程式會以交易的方式運作。 應用程式會從資料庫中選取記錄，並將它們呈現給使用者，通常是一次一個。 使用者看到的內容通常是單一的目前記錄，這可能是唯一的記憶體。

如果您的應用程式不需要檔來儲存資料，您可以使用架構的部分或全部檔/視圖架構。 您所分配的數量取決於您偏好的方法。 您可能會：

- 使用最小的檔做為儲存資料來源連接的位置，但使用一般檔功能（例如序列化）。 當您想要多個資料檢視，而且想要同步處理所有視圖、一次更新全部，依此類推，這項功能就很有用。

- 使用您直接繪製的框架視窗，而不是使用 view。 在此情況下，您會省略檔，並將任何資料或資料連線儲存在框架視窗物件中。

##  <a name="application-wizard-options-for-documents-and-views"></a><a name="_core_appwizard_options_for_documents_and_views"></a>檔和視圖的應用程式精靈選項

[MFC 應用程式精靈] 在 [**選取資料庫支援**] 中有數個選項，如下表所列。 如果您使用 MFC 應用程式精靈來建立應用程式，所有這些選項都會產生具有檔和視圖的應用程式。 有些選項會提供省略不必要檔功能的檔和視圖。 如需詳細資訊，請參閱[MFC 應用程式精靈的資料庫支援](../mfc/reference/database-support-mfc-application-wizard.md)。

|選項|檢視|Document|
|------------|----------|--------------|
|**None**|衍生自 `CView`。|不提供資料庫支援。 這是預設選項。<br /><br /> 如果您在 [[應用程式類型] 的 [MFC 應用程式]](../mfc/reference/application-type-mfc-application-wizard.md)頁面上選取 [**檔** **/視圖架構支援**] 選項，您會在 [檔案] 功能表上取得完整檔支援，包括 [序列化] 和 [**開啟**]、[**儲存**] 和 **另存** **新**檔 請參閱[沒有檔的應用程式](#_core_applications_with_no_document)。|
|**僅限標頭檔**|衍生自 `CView`。|為您的應用程式提供基本層級的資料庫支援。<br /><br /> 包含 Afxdb。 會新增程式庫，但不會建立任何資料庫特定的類別。 您可以稍後建立記錄集，並使用它們來檢查和更新記錄。|
|**不支援檔案的資料庫檢視**|衍生自 `CRecordView`|提供檔支援，但不支援序列化。 檔可以儲存記錄集並協調多個視圖;不支援序列化或新增、**開啟**、**儲存**和**另存** **新**檔命令。 查看[具有最少檔的應用程式](#_core_applications_with_minimal_documents)。 如果您包含資料庫檢視，就必須指定資料的來源。<br /><br /> 包含資料庫標頭檔、程式庫、記錄檔視圖和記錄集。 （僅適用于已在 [[應用程式類型]、[MFC 應用程式]](../mfc/reference/application-type-mfc-application-wizard.md)頁面上選取 [**檔/視圖架構支援**] 選項的應用程式）。|
|**具有檔案支援的資料庫檢視**|衍生自 `CRecordView`|提供完整的檔支援，包括序列化和**檔**相關的檔案功能表命令。 資料庫應用程式通常會針對每個記錄執行，而不是以個別檔案為基礎，因此不需要序列化。 不過，您可能會特別使用序列化。 查看[具有最少檔的應用程式](#_core_applications_with_minimal_documents)。 如果您包含資料庫檢視，就必須指定資料的來源。<br /><br /> 包含資料庫標頭檔、程式庫、記錄檔視圖和記錄集。 （僅適用于已在 [[應用程式類型]、[MFC 應用程式]](../mfc/reference/application-type-mfc-application-wizard.md)頁面上選取 [**檔/視圖架構支援**] 選項的應用程式）。|

如需序列化的替代專案和序列化的替代用法討論，請參閱[序列化：序列化和資料庫輸入/輸出](../mfc/serialization-serialization-vs-database-input-output.md)。

##  <a name="applications-with-minimal-documents"></a><a name="_core_applications_with_minimal_documents"></a>具有最少檔的應用程式

[MFC 應用程式精靈] 有兩個選項可支援表單架構的資料存取應用程式。 每個選項都會建立一個 `CRecordView`衍生的 view 類別和一個檔。 它們在檔中留下的不同。

###  <a name="document-without-file-support"></a><a name="_core_a_document_without_file_support"></a>不支援檔案的檔

如果您不需要檔序列化，請選取 [應用程式精靈] 資料庫選項 [**資料庫檢視但不支援**檔案]。 此檔有下列用途：

- 這是儲存 `CRecordset` 物件的方便位置。

   這種用法等同于一般檔概念：檔會儲存資料（在此案例中為一組記錄），而視圖則是檔的視圖。

- 如果您的應用程式顯示多個視圖（例如多個記錄視圖），檔支援協調視圖。

   如果多個視圖顯示相同的資料，您可以使用 `CDocument::UpdateAllViews` 成員函式，在任何視圖變更資料時協調所有視圖的更新。

您通常會將此選項用於簡單的表單架構應用程式。 應用程式精靈會自動為這類應用程式支援方便的結構。

###  <a name="document-with-file-support"></a><a name="_core_a_document_with_file_support"></a>包含檔案支援的檔

當您可以使用檔相關的 [檔案] 功能表命令和 **[檔序列化**] 時，選取 [檔案支援] 的 [應用程式精靈] 資料庫選項 [**資料庫檢視**]。 對於程式的資料存取部分，您可以使用檔中所述的相同方式，[而不需要檔案支援](#_core_a_document_without_file_support)。 例如，您可以使用檔的序列化功能來讀取及寫入序列化的使用者設定檔，以儲存使用者的喜好設定或其他有用的資訊。 如需更多的想法，請參閱[序列化：序列化和資料庫輸入/輸出](../mfc/serialization-serialization-vs-database-input-output.md)。

應用程式精靈支援此選項，但您必須撰寫程式碼來序列化檔。 將序列化資訊儲存在檔資料成員中。

##  <a name="applications-with-no-document"></a><a name="_core_applications_with_no_document"></a>沒有檔的應用程式

有時候，您可能會想要撰寫不使用檔或 views 的應用程式。 若沒有檔，您可以將資料（例如 `CRecordset` 物件）儲存在框架視窗類別或應用程式類別中。 任何額外的需求都取決於應用程式是否呈現使用者介面。

###  <a name="database-support-with-a-user-interface"></a><a name="_core_database_support_with_a_user_interface"></a>使用者介面的資料庫支援

如果您有使用者介面（例如，主控台命令列介面），您的應用程式會直接繪製到框架視窗的工作區，而不是在視圖中。 這類應用程式不會使用 `CRecordView`、`CFormView`或 `CDialog` 作為其主要使用者介面，但通常會針對一般對話使用 `CDialog`。

###  <a name="writing-applications-without-documents"></a><a name="_core_writing_applications_without_documents"></a>撰寫不含檔的應用程式

因為應用程式精靈不支援建立不含檔的應用程式，所以您必須撰寫自己的 `CWinApp`衍生類別，並在必要時也建立 `CFrameWnd` 或 `CMDIFrameWnd` 類別。 覆寫 `CWinApp::InitInstance` 並將應用程式物件宣告為：

```cpp
CYourNameApp theApp;
```

架構仍然提供訊息對應機制和許多其他功能。

###  <a name="database-support-separate-from-the-user-interface"></a><a name="_core_database_support_separate_from_the_user_interface"></a>不同于使用者介面的資料庫支援

有些應用程式不需要使用者介面或只有最少一個。 例如，假設您要撰寫：

- 中繼資料存取物件，其他應用程式（用戶端）會呼叫以在應用程式與資料來源之間進行特殊的資料處理。

- 在不需要使用者介入的情況下處理資料的應用程式，例如將資料從某個資料庫格式移至另一個或進行計算並執行批次更新的應用程式。

因為沒有任何檔擁有 `CRecordset` 物件，所以您可能會想要將它儲存為 `CWinApp`衍生應用程式類別中的內嵌資料成員。 替代方案包括：

- 不保持永久的 `CRecordset` 物件。 您可以將 Null 傳遞給您的記錄集類別的函式。 在此情況下，架構會使用記錄集 `GetDefaultConnect` 成員函式中的資訊來建立暫存 `CDatabase` 物件。 這是最可能的替代方法。

- 將 `CRecordset` 物件設為全域變數。 這個變數應該是您在 `CWinApp::InitInstance` 覆寫中動態建立的記錄集物件的指標。 這可避免在初始化架構之前嘗試建立物件。

- 使用記錄集物件，就像在檔或視圖的內容中一樣。 在應用程式或框架視窗物件的成員函式中建立記錄集。

## <a name="see-also"></a>另請參閱

[MFC 資料庫類別](../data/mfc-database-classes-odbc-and-dao.md)
