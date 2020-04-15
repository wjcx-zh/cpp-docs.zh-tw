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
ms.openlocfilehash: c914a449b73e7da876d2e05b894c016b53881c3b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360676"
---
# <a name="mfc-using-database-classes-without-documents-and-views"></a>MFC：使用不具文件和檢視的資料庫類別

有時,您可能不希望在資料庫應用程式中使用框架的文檔/視圖體系結構。 本主題將說明：

- [當您不需要使用文檔](#_core_when_you_don.92.t_need_documents)(如文件序列化)時。

- [應用程式精靈選項](#_core_appwizard_options_for_documents_and_views),支援應用程式不序列化與沒有文件相關的**檔案**選單指令,如**新建**、**開啟**、**儲存**與**儲存為**。

- [如何使用使用最小文件的應用程式](#_core_applications_with_minimal_documents)。

- [如何建立沒有文件或檢視的應用程式](#_core_applications_with_no_document)。

## <a name="when-you-do-not-need-documents"></a><a name="_core_when_you_don.92.t_need_documents"></a>當您不需要文件時

某些應用程式具有文檔的不同概念。 這些應用程式通常使用**檔案打開**命令將儲存中的所有或大部分檔載入到記憶體中。 他們用**檔案儲存**或**儲存為**命令一次將更新的檔案寫回儲存。 使用者看到的是一個數據檔。

但是,某些類別的應用程式不需要文檔。 資料庫應用程式在事務方面運行。 應用程式從資料庫中選擇記錄,並將記錄呈現給使用者,通常一次一個。 使用者看到的通常是單個當前記錄,這可能是記憶體中唯一的記錄。

如果應用程式不需要用於存儲數據的文件,則可以免除框架的文檔/檢視體系結構的部分或全部內容。 你放棄多少取決於你喜歡的方法。 您可以:

- 使用最小文件作為存儲與數據源的連接的位置,但無需使用常規文檔功能(如序列化)。 當您想要數據的幾個檢視並且想要同步所有檢視、一次更新所有檢視等時,這非常有用。

- 使用直接繪製的幀視窗,而不是使用視圖。 在這種情況下,您省略文檔並將任何資料或資料連接儲存在框架視窗物件中。

## <a name="application-wizard-options-for-documents-and-views"></a><a name="_core_appwizard_options_for_documents_and_views"></a>文件與檢視的應用程式精靈選項

MFC 應用程式精靈在 **「選擇資料庫支援」** 中有幾個選項,這些選項列在下表中。 如果使用 MFC 應用程式精靈建立應用程式,所有這些選項都會產生包含文件和檢視的應用程式。 某些選項提供忽略不需要的文檔功能的文件和檢視。 有關詳細資訊,請參閱[資料庫支援 MFC 應用程式精靈](../mfc/reference/database-support-mfc-application-wizard.md)。

|選項|檢視|Document|
|------------|----------|--------------|
|**None**|衍生自 `CView`。|不提供資料庫支援。 這是預設選項。<br /><br /> 如果在[「應用程式類型」 MFC 應用程式精靈](../mfc/reference/application-type-mfc-application-wizard.md)頁上選擇**文件/檢視體系結構支援**選項,則可以在 **「檔」** 選單上獲得完整的文件支援,包括序列化和**新建**、**打開**、**儲存**和**儲存為**命令。 請參考[沒有文件的應用程式](#_core_applications_with_no_document)。|
|**只有標題檔案**|衍生自 `CView`。|為應用程式提供基本級別的資料庫支援。<br /><br /> 包括 Afxdb.h. 添加連結庫,但不創建任何特定於資料庫的類。 您可以稍後創建記錄集,並使用它們來檢查和更新記錄。|
|**沒有檔案支援的資料庫檢視**|來自`CRecordView`|提供文件支援,但不提供序列化支援。 文檔可以儲存記錄集並協調多個檢視;不支援序列化或**新建**、**開啟**、**儲存**和**儲存為**命令。 請參考[有最小文件的應用程式](#_core_applications_with_minimal_documents)。 如果包含資料庫檢視,則必須指定數據源。<br /><br /> 包括資料庫標頭檔、連結庫、記錄檢視和記錄集。 (僅適用於在[「應用程式類型」MFC 應用程式精靈](../mfc/reference/application-type-mfc-application-wizard.md)頁面上選擇**的文件/視圖體系結構支援**選項的應用程式。|
|**支援檔案的資料庫檢視**|來自`CRecordView`|提供完整的文件支援,包括序列化和文件相關的**檔案**功能表命令。 資料庫應用程式通常以每記錄為基礎,而不是基於每個檔運行,因此不需要序列化。 但是,您可能有序列化的特殊用途。 請參考[有最小文件的應用程式](#_core_applications_with_minimal_documents)。 如果包含資料庫檢視,則必須指定數據源。<br /><br /> 包括資料庫標頭檔、連結庫、記錄檢視和記錄集。 (僅適用於在[「應用程式類型」MFC 應用程式精靈](../mfc/reference/application-type-mfc-application-wizard.md)頁面上選擇**的文件/視圖體系結構支援**選項的應用程式。|

有關序列化的替代和序列化的替代用途的討論,請參閱[序列化:序列化與資料庫輸入/輸出](../mfc/serialization-serialization-vs-database-input-output.md)。

## <a name="applications-with-minimal-documents"></a><a name="_core_applications_with_minimal_documents"></a>具有最小文件的應用程式

MFC 應用程式精靈有兩個選項支援基於表單的資料存取應用程式。 每個選項都創建`CRecordView`一個派生視圖類和一個文檔。 他們留下的檔不同。

### <a name="document-without-file-support"></a><a name="_core_a_document_without_file_support"></a>沒有檔案支援的文件

如果不需要文件序列化,請選擇應用程式精靈資料庫選項**資料庫選項資料庫檢視,而無需檔案支援**。 此文件具有以下有用目的:

- 這是存儲物件的`CRecordset`方便場所。

   此用法與普通文件概念類似:文件存儲數據(或,在本例中為一組記錄),視圖是文檔的檢視。

- 如果應用程式顯示多個檢視(如多個記錄檢視),則文檔支援協調視圖。

   如果多個檢視顯示相同的數據,則可以使用`CDocument::UpdateAllViews`成員函數協調所有檢視的更新,當任何視圖更改數據時。

通常,對於簡單的基於表單的應用程式,通常使用此選項。 應用程式向導自動支援此類應用程式的便捷結構。

### <a name="document-with-file-support"></a><a name="_core_a_document_with_file_support"></a>包含檔案支援的文件

當您對文件相關的**檔案**選單指令與文件序列化具有替代用途時,選擇**具有檔案支援的應用程式精靈資料庫選項資料庫檢視**。 對於程式的資料存取部分,可以使用文件的方式與[「無檔支援文件」](#_core_a_document_without_file_support)中所述的方式相同。 例如,可以使用文檔的序列化功能讀取和寫入存儲使用者首選項或其他有用資訊的序列化使用者設定檔文檔。 有關詳細資訊,請參閱[序列化:序列化與資料庫輸入/輸出](../mfc/serialization-serialization-vs-database-input-output.md)。

應用程式精靈支援此選項,但必須編寫序列化文件的代碼。 將序列化資訊儲存在文件數據成員中。

## <a name="applications-with-no-document"></a><a name="_core_applications_with_no_document"></a>沒有文件應用程式

有時,您可能希望編寫不使用文檔或視圖的應用程式。 如果沒有文件,則可以將數據(如`CRecordset`物件)存儲在框架視窗類或應用程式類中。 任何其他要求取決於應用程式是否提供用戶介面。

### <a name="database-support-with-a-user-interface"></a><a name="_core_database_support_with_a_user_interface"></a>具有使用者介面的資料庫支援

如果您有使用者介面(例如,主控台命令列介面),則應用程式將直接繪製到框架視窗的工作區,而不是到視圖中。 此類應用程式不使用`CRecordView``CFormView``CDialog`或用於其主用戶介面,但它通常`CDialog`用於普通對話方塊。

### <a name="writing-applications-without-documents"></a><a name="_core_writing_applications_without_documents"></a>編寫無文件的應用程式

由於應用程式精靈不支援在沒有文件的情況下創建應用程式,因此必須編寫自己的`CWinApp`派生類,如果需要,還必須創建或`CFrameWnd``CMDIFrameWnd`類。 重寫`CWinApp::InitInstance`應用程式物件並將其聲明為:

```cpp
CYourNameApp theApp;
```

該框架仍然提供消息映射機制和許多其他功能。

### <a name="database-support-separate-from-the-user-interface"></a><a name="_core_database_support_separate_from_the_user_interface"></a>資料庫支援獨立於使用者介面

某些應用程式不需要用戶介面或只需要最少的用戶介面。 例如,假設您正在編寫:

- 其他應用程式(用戶端)要求在應用程式和數據源之間特殊處理數據的中間數據訪問物件。

- 處理資料而不進行使用者干預的應用程式,例如將數據從一種資料庫格式移動到另一種資料庫格式或執行批處理更新的應用程式。

由於沒有文件擁有該`CRecordset`物件,因此您可能希望將其存儲`CWinApp`為 派生應用程式類中的嵌入式數據成員。 替代專案包括:

- 根本不保留永久`CRecordset`物件。 您可以將 NULL 傳遞給記錄集類建構函數。 在這種情況下,框架使用記錄集`CDatabase``GetDefaultConnect`的成員函數中的資訊創建一個臨時物件。 這是最有可能的替代方法。

- 使`CRecordset`對象成為全域變數。 此變數應指向在`CWinApp::InitInstance`重寫中動態創建的記錄集物件的指標。 這樣可以避免在初始化框架之前嘗試構造物件。

- 在文件或檢視的上下文中使用記錄集物件。 在應用程式或框架視窗物件的成員函數中創建記錄集。

## <a name="see-also"></a>另請參閱

[MFC 資料庫類別](../data/mfc-database-classes-odbc-and-dao.md)
