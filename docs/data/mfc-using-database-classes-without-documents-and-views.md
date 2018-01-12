---
title: "MFC： 使用不具文件和檢視的資料庫類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1691d1f90201b25cc53cd07e80626e98c447e66b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-using-database-classes-without-documents-and-views"></a>MFC：使用不具文件和檢視的資料庫類別
有時候您可能不想使用在您的資料庫應用程式架構的文件/檢視架構。 本主題說明：  
  
-   [當您不需要使用文件](#_core_when_you_don.92.t_need_documents)例如文件序列化。  
  
-   [應用程式精靈選項](#_core_appwizard_options_for_documents_and_views)以支援應用程式而不需要序列化以及文件相關**檔案**功能表命令，例如**新增**，**開啟**，**儲存**，和**存**。  
  
-   [如何使用最少的文件的應用程式使用](#_core_applications_with_minimal_documents)。  
  
-   [如何組織應用程式與文件或檢視表沒有](#_core_applications_with_no_document)。  
  
##  <a name="_core_when_you_don.92.t_need_documents"></a>當您不需要文件  
 某些應用程式具有不同的文件概念。 這些應用程式通常是檔案的全部或大部分從儲存體使用載入至記憶體**開啟舊檔**命令。 它們將更新的檔案寫回一次使用的儲存體**檔案儲存**或**存**命令。 使用者所看見的資料檔案。  
  
 不過，某些種類的應用程式，不需要文件。 資料庫應用程式操作方面的交易。 應用程式從資料庫選取記錄，並呈現給使用者，通常一次。 使用者所看見通常是單一的目前記錄，這可能是在記憶體中的只有一個。  
  
 如果您的應用程式不需要將資料儲存的文件，其可以分配您進行部分或所有架構的文件/檢視架構。 您省卻多少取決於您偏好的方法。 您可以：  
  
-   使用最少的文件做為位置，以儲存您的資料來源的連接，但省卻一般文件功能，例如序列化。 當您要資料的數個檢視，而且想要同步處理所有檢視、 更新一次，依此類推，這非常有用。  
  
-   使用框架視窗，在其中繪製直接管理，而不是使用檢視。 在此情況下，您會省略文件和框架視窗物件中儲存任何資料或資料連接。  
  
##  <a name="_core_appwizard_options_for_documents_and_views"></a>文件和檢視應用程式精靈選項  
 MFC 應用程式精靈提供數個選項**選取資料庫支援**下, 表列出這些。 如果您使用 MFC 應用程式精靈建立應用程式時，所有這些選項會產生應用程式與文件和檢視。 某些選項會提供文件和省略不必要的文件功能的檢視。 如需詳細資訊，請參閱[MFC 應用程式精靈、 資料庫支援](../mfc/reference/database-support-mfc-application-wizard.md)。  
  
|選項|檢視|文件|  
|------------|----------|--------------|  
|**無**|衍生自 `CView`。|不提供資料庫支援。 這是預設選項。<br /><br /> 如果您選取**文件/檢視架構支援**選項[應用程式類型、 MFC 應用程式精靈](../mfc/reference/application-type-mfc-application-wizard.md) 頁面上，取得完整的文件的支援，包含序列化和`New`， **開啟**，**儲存**，和**存**命令**檔案**功能表。 請參閱[不具文件的應用程式](#_core_applications_with_no_document)。|  
|**僅限標頭檔**|衍生自 `CView`。|提供您的應用程式的資料庫支援的基本層級。<br /><br /> 包含 Afxdb.h。 加入連結程式庫，但不會建立任何資料庫特有類別。 您可以稍後再建立資料錄集，並用來檢查和更新記錄。|  
|**未提供檔案支援的資料庫檢視**|衍生自`CRecordView`|提供文件支援，但沒有序列化支援。 文件可以儲存資料錄集，並協調多個檢視。不支援序列化或`New`，**開啟**，**儲存**，和**存**命令。 請參閱[應用程式的最小的文件](#_core_applications_with_minimal_documents)。 如果您包含資料庫檢視，您必須指定資料的來源。<br /><br /> 包含資料庫標頭檔、 連結程式庫、 資料錄檢視和資料錄集。 (僅適用於應用程式與**文件/檢視架構支援**上選取的選項[應用程式類型、 MFC 應用程式精靈](../mfc/reference/application-type-mfc-application-wizard.md)頁面。)|  
|**提供檔案支援的資料庫檢視**|衍生自`CRecordView`|提供完整的文件支援，包括序列化和文件相關**檔案**功能表命令。 資料庫應用程式通常會操作針對每一筆記錄，而非每個檔案，因此不需要序列化。 不過，您可能必須進行序列化的特殊使用。 請參閱[應用程式的最小的文件](#_core_applications_with_minimal_documents)。 如果您包含資料庫檢視，您必須指定資料的來源。<br /><br /> 包含資料庫標頭檔、 連結程式庫、 資料錄檢視和資料錄集。 (僅適用於應用程式與**文件/檢視架構支援**上選取的選項[應用程式類型、 MFC 應用程式精靈](../mfc/reference/application-type-mfc-application-wizard.md)頁面。)|  
  
 如需序列化和使用序列化替代的替代方式的討論，請參閱[序列化： 序列化 vs。資料庫輸入/輸出](../mfc/serialization-serialization-vs-database-input-output.md)。  
  
##  <a name="_core_applications_with_minimal_documents"></a>具有最少的文件的應用程式  
 MFC 應用程式精靈可支援表單為主的資料存取應用程式的兩個選項。 每個選項會建立`CRecordView`-衍生檢視類別和文件。 但在它們離開超出文件不同。  
  
###  <a name="_core_a_document_without_file_support"></a>未提供檔案支援的文件  
 選取應用程式精靈資料庫選項**Database 未提供檔案支援檢視**如果您不需要文件序列化。 文件會提供下列實用的用途：  
  
-   它是方便的位置來儲存`CRecordset`物件。  
  
     這種使用方式與一般的文件概念： 文件儲存的資料 （或在此案例中的一組記錄），而檢視是文件的檢視。  
  
-   如果您的應用程式 （例如多個資料錄檢視） 的多個檢視，文件支援協調這些檢視。  
  
     如果多個檢視將顯示相同的資料，您可以使用`CDocument::UpdateAllViews`成員函式來協調所有檢視的更新，當任何檢視會將資料變更時。  
  
 您通常會針對簡單的表單架構應用程式使用此選項。 應用程式精靈這類應用程式的支援方便結構的自動。  
  
###  <a name="_core_a_document_with_file_support"></a>提供檔案支援的文件  
 選取應用程式精靈資料庫選項**資料庫檔案支援的檢視**當您有一個替代用途的文件相關**檔案**功能表命令以及文件序列化。 資料存取程式的部分，您可以使用文件中的相同方式中所述[文件不提供檔案支援](#_core_a_document_without_file_support)。 您可以讀取及寫入儲存使用者的喜好設定或其他實用資訊的序列化的使用者設定檔文件，例如，使用文件的序列化功能。 如需詳細資訊，請參閱[序列化： 序列化 vs。資料庫輸入/輸出](../mfc/serialization-serialization-vs-database-input-output.md)。  
  
 應用程式精靈支援此選項，但您必須撰寫程式碼序列化文件。 在文件資料成員中儲存的序列化的資訊。  
  
##  <a name="_core_applications_with_no_document"></a>不具文件的應用程式  
 您有時可能會想要撰寫的應用程式不會使用文件或檢視表。 不具有文件，您可以儲存您的資料 (例如`CRecordset`物件) 在框架視窗類別或應用程式類別。 任何額外的需求取決於應用程式是否提供使用者介面。  
  
###  <a name="_core_database_support_with_a_user_interface"></a>資料庫支援使用者介面  
 如果您有使用者介面 （例如主控台命令列介面以外），您的應用程式會繪製直接在框架視窗的工作區中，而不是插入檢視。 這類應用程式不會使用`CRecordView`， `CFormView`，或`CDialog`其主要的使用者介面，但它通常使用`CDialog`一般的對話方塊。  
  
###  <a name="_core_writing_applications_without_documents"></a>不具有文件撰寫應用程式  
 因為應用程式精靈不支援不具有文件的建立應用程式，您必須撰寫您自己`CWinApp`-衍生的類別，如有需要並建立`CFrameWnd`或`CMDIFrameWnd`類別。 覆寫`CWinApp::InitInstance`和應用程式物件宣告為：  
  
```  
CYourNameApp theApp;  
```  
  
 架構仍會提供訊息對應機制和許多其他功能。  
  
###  <a name="_core_database_support_separate_from_the_user_interface"></a>資料庫支援不同的使用者介面  
 某些應用程式需要任何使用者介面或最少一個。 例如，假設您要撰寫：  
  
-   中繼資料存取物件的其他應用程式 （用戶端） 呼叫的應用程式與資料來源之間的資料的特殊處理。  
  
-   處理資料，不需要使用者介入，例如將資料從一個資料庫格式移到另一部或進行計算，而且會執行批次更新的應用程式的應用程式。  
  
 由於沒有文件擁有`CRecordset`物件，您可能想要將它儲存為內嵌的資料成員中您`CWinApp`-衍生的應用程式類別。 替代項目包括：  
  
-   勿使永久`CRecordset`完全物件。 您可以傳遞**NULL**資料錄集類別建構函式。 在此情況下，架構會建立暫存`CDatabase`物件中資料錄集的使用資訊`GetDefaultConnect`成員函式。 這是最可能的替代方式。  
  
-   進行`CRecordset`物件的全域變數。 此變數應為您建立以動態方式在資料錄集物件的指標您`CWinApp::InitInstance`覆寫。 這可避免嘗試之前在架構初始化建構物件。  
  
-   如同文件或檢視的內容中使用資料錄集物件。 建立資料錄集在成員函式的應用程式或框架視窗物件。  
  
## <a name="see-also"></a>請參閱  
 [MFC 資料庫類別](../data/mfc-database-classes-odbc-and-dao.md)