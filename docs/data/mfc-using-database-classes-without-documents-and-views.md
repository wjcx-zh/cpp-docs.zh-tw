---
title: MFC： 使用不具文件和檢視的資料庫類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 999fa2e30a769f925555207675010cf1039bfb8b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46101986"
---
# <a name="mfc-using-database-classes-without-documents-and-views"></a>MFC：使用不具文件和檢視的資料庫類別

有時候您可能不想使用架構的文件/檢視架構，在您的資料庫應用程式。 本主題說明：  
  
- [當您不需要使用文件](#_core_when_you_don.92.t_need_documents)例如文件序列化。  
  
- [應用程式精靈選項](#_core_appwizard_options_for_documents_and_views)來支援應用程式沒有序列化而文件相關**檔案** 功能表命令，例如**新增**，**開啟****儲存**，並**存**。  
  
- [如何使用最少的文件的應用程式使用](#_core_applications_with_minimal_documents)。  
  
- [如何建構不含文件或檢視的應用程式](#_core_applications_with_no_document)。  
  
##  <a name="_core_when_you_don.92.t_need_documents"></a> 當您不需要文件  

有些應用程式會有不同的概念文件。 這些應用程式通常所有或大多數檔案從儲存體載入記憶體**開啟舊檔**命令。 它們將更新的檔案寫回全部一次使用儲存體**檔案儲存**或是**另存新檔**命令。 使用者所看見的資料檔案。  
  
不過，某些種類的應用程式，不需要文件。 資料庫應用程式會處理交易。 應用程式從資料庫選取的記錄，並將它們呈現給使用者，通常一次一個。 哪些使用者會看到，通常是單一的目前記錄，這可能是記憶體中的唯一的。  
  
如果您的應用程式不需要將資料儲存的文件，您可以省略了部分或所有架構的文件/檢視架構。 您省卻的程度取決於您偏好的方法。 您可能會：  
  
- 使用做為位置的最小的文件，來儲存您的資料來源的連接，但省略了標準的文件功能，例如序列化。 當您要資料的數個檢視，而且想要同步處理所有的檢視中，更新它們全部一次，依此類推，這非常有用。  
  
- 使用框架視窗，其中您繪製直接管理，而不是使用檢視。 在此情況下，您會省略文件，並在框架視窗物件中儲存任何資料或資料連接。  
  
##  <a name="_core_appwizard_options_for_documents_and_views"></a> 應用程式的文件和檢視的精靈選項  

MFC 應用程式精靈] 有幾個選項**選取 [資料庫支援**下, 表列出。 如果您使用 MFC 應用程式精靈建立應用程式時，所有這些選項會產生應用程式與文件和檢視。 某些選項會提供文件和檢視，以省略不必要的文件的功能。 如需詳細資訊，請參閱 < [MFC 應用程式精靈、 資料庫支援](../mfc/reference/database-support-mfc-application-wizard.md)。  
  
|選項|檢視|文件|  
|------------|----------|--------------|  
|**無**|衍生自 `CView`。|不會提供資料庫支援。 這是預設選項。<br /><br /> 如果您選取**文件/檢視架構支援**選項[應用程式類型、 MFC 應用程式精靈](../mfc/reference/application-type-mfc-application-wizard.md)頁面上，取得完整的文件的支援，包括序列化及**新增**，**開放**，**儲存**，和**另存新檔**上的命令**檔案**功能表。 請參閱[不具文件的應用程式](#_core_applications_with_no_document)。|  
|**僅限標頭檔**|衍生自 `CView`。|提供您的應用程式的資料庫支援基本的層級。<br /><br /> 包含 Afxdb.h。 新增連結程式庫，但不會建立任何資料庫特有類別。 您可以稍後再建立資料錄集，並使用它們來檢查和更新記錄。|  
|**不附檔案支援的資料庫檢視**|衍生自 `CRecordView`|提供文件支援，但沒有序列化支援。 文件可以儲存的資料錄集，並協調多個檢視;不支援序列化或**新增**，**開放**，**儲存**，以及**另存新檔**命令。 請參閱[應用程式的最小的文件](#_core_applications_with_minimal_documents)。 如果您包含資料庫檢視，您必須指定資料的來源。<br /><br /> 包含資料庫標頭檔、 連結程式庫、 資料錄檢視和資料錄集。 (僅適用於應用程式**文件/檢視架構支援**上所選取的選項[應用程式類型、 MFC 應用程式精靈](../mfc/reference/application-type-mfc-application-wizard.md)頁面。)|  
|**附檔案支援的資料庫檢視**|衍生自 `CRecordView`|提供完整的文件的支援，包括序列化及相關的文件**檔案**功能表命令。 資料庫應用程式通常會對各個記錄而不是每個檔案為基礎，因此不需要序列化。 不過，您可能必須序列化的特殊用途。 請參閱[應用程式的最小的文件](#_core_applications_with_minimal_documents)。 如果您包含資料庫檢視，您必須指定資料的來源。<br /><br /> 包含資料庫標頭檔、 連結程式庫、 資料錄檢視和資料錄集。 (僅適用於應用程式**文件/檢視架構支援**上所選取的選項[應用程式類型、 MFC 應用程式精靈](../mfc/reference/application-type-mfc-application-wizard.md)頁面。)|  
  
如需序列化和序列化的其他用法的替代方案的討論，請參閱[序列化： 序列化 vs。資料庫輸入/輸出](../mfc/serialization-serialization-vs-database-input-output.md)。  
  
##  <a name="_core_applications_with_minimal_documents"></a> 最小的文件的應用程式  

MFC 應用程式精靈可支援以 form 為基礎的資料存取應用程式的兩個選項。 每個選項會建立`CRecordView`-衍生檢視類別和文件。 但在它們離開文件不同。  
  
###  <a name="_core_a_document_without_file_support"></a> 不附檔案支援的文件  

選取應用程式精靈 的資料庫選項**資料庫檢視不附檔案支援**如果您不需要文件序列化。 文件會提供下列實用的用途：  
  
- 它是一個便利的位置來儲存`CRecordset`物件。  
  
     這種使用方式和一般的文件概念相似： 文件會儲存資料 （或在此情況下，一組記錄），而檢視是文件的檢視。  
  
- 如果您的應用程式顯示 （例如多個資料錄檢視） 的多個檢視，文件支援協調這些檢視。  
  
     如果多個檢視會顯示相同的資料，您可以使用`CDocument::UpdateAllViews`協調所有檢視的更新時的任何檢視會將資料變更的成員函式。  
  
您通常會針對簡單的表單架構應用程式使用此選項。 應用程式精靈 支援方便結構這類應用程式自動。  
  
###  <a name="_core_a_document_with_file_support"></a> 附檔案支援的文件  

選取應用程式精靈 的資料庫選項**資料庫檢視附檔案支援**當您有用於其他方面的文件相關**檔案**功能表命令和文件序列化。 資料存取程式的部分，您可以使用文件中的相同方式中所述[文件不提供檔案支援](#_core_a_document_without_file_support)。 您可用的文件序列化功能，比方說，讀取及寫入使用者的喜好設定或其他有用的資訊會儲存已序列化的使用者設定檔文件。 如需詳細資訊，請參閱[序列化： 序列化 vs。資料庫輸入/輸出](../mfc/serialization-serialization-vs-database-input-output.md)。  
  
應用程式精靈 支援此選項，但您必須撰寫的程式碼，將序列化文件。 將序列化的資訊儲存在文件資料成員。  
  
##  <a name="_core_applications_with_no_document"></a> 不具文件的應用程式  

您有時可能會想要撰寫的應用程式，不會使用文件或檢視表。 您可以不使用文件，儲存您的資料 (例如`CRecordset`物件) 框架視窗類別或您的應用程式類別中。 任何額外的需求取決於應用程式是否呈現的使用者介面。  
  
###  <a name="_core_database_support_with_a_user_interface"></a> 具有使用者介面的資料庫支援  

如果您有使用者介面 （而不是，比方說，主控台命令列介面），直接在框架視窗的工作區中，而不是插入檢視，也會繪製您的應用程式。 這類應用程式不會使用`CRecordView`， `CFormView`，或`CDialog`對於它的主要使用者介面，但它通常使用`CDialog`一般對話方塊。  
  
###  <a name="_core_writing_applications_without_documents"></a> 不使用文件的撰寫應用程式  

因為應用程式精靈 不支援建立的應用程式不使用文件，您必須撰寫您自己`CWinApp`-衍生類別，而且如果有需要也可以建立`CFrameWnd`或`CMDIFrameWnd`類別。 覆寫`CWinApp::InitInstance`和應用程式物件宣告為：  
  
```cpp  
CYourNameApp theApp;  
```  
  
架構仍會提供訊息對應機制及許多其他功能。  
  
###  <a name="_core_database_support_separate_from_the_user_interface"></a> 資料庫支援不同，從使用者介面  

某些應用程式需要任何使用者介面或只需最小的密碼。 例如，假設您正在撰寫：  
  
- 中繼資料存取物件，其他應用程式 （用戶端） 呼叫的應用程式與資料來源之間的資料的特殊處理。  
  
- 處理資料，不需要使用者介入，例如將資料從某種資料庫格式移至另一個或一，會進行計算，並執行批次更新的應用程式的應用程式。  
  
因為沒有文件擁有`CRecordset`物件，您可能想要將它儲存為內嵌的資料成員中您`CWinApp`-衍生的應用程式類別。 替代項目包括：  
  
- 不保留永久`CRecordset`所有物件。 您可以傳遞 NULL 給您的資料錄集類別建構函式。 在此情況下，此架構會建立暫存`CDatabase`物件中資料錄集的使用資訊`GetDefaultConnect`成員函式。 這是最可能的替代方法。  
  
- 讓`CRecordset`物件的全域變數。 這個變數必須是您建立以動態方式在資料錄集物件的指標您`CWinApp::InitInstance`覆寫。 這可避免嘗試初始化架構之前建構物件。  
  
- 如同文件或檢視的內容中，請使用資料錄集物件。 建立資料錄集成員中的應用程式或框架視窗物件的函式。  
  
## <a name="see-also"></a>另請參閱  

[MFC 資料庫類別](../data/mfc-database-classes-odbc-and-dao.md)