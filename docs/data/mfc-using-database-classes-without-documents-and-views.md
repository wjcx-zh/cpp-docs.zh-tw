---
title: "MFC：使用不具文件和檢視的資料庫類別 | Microsoft Docs"
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
  - "應用程式精靈 [C++], 建立資料庫應用程式"
  - "CDaoRecordView 類別, 使用於資料庫應用程式"
  - "CRecordView 類別, 使用於資料庫應用程式"
  - "DAO [C++], 資料庫應用程式中的檔案支援"
  - "DAO [C++], 撰寫應用程式"
  - "資料庫應用程式 [C++], 應用程式精靈選項"
  - "資料庫應用程式 [C++], 不具有文件"
  - "資料庫應用程式 [C++], 不具有檢視"
  - "資料庫類別 [C++], MFC"
  - "文件/檢視架構 [C++], 在資料庫中"
  - "文件 [C++], 應用程式不含"
  - "檔案 [C++], MFC"
  - "ODBC [C++], 資料庫應用程式中的檔案支援"
  - "ODBC 應用程式 [C++]"
  - "ODBC 應用程式 [C++], 不具有文件"
  - "ODBC 應用程式 [C++], 不具有檢視"
  - "使用者介面 [C++], 繪製資訊"
ms.assetid: 15bf52d4-91cf-4b1d-8b37-87c3ae70123a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC：使用不具文件和檢視的資料庫類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

有時候您可能不想在資料庫應用程式中使用架構的文件\/檢視架構。  這個主題說明：  
  
-   [您不需要文件的時機](#_core_when_you_don.92.t_need_documents)，例如進行文件序列化時。  
  
-   [應用程式精靈選項](#_core_appwizard_options_for_documents_and_views)用來支援不具序列化和不具與文件相關的 \[檔案\] 功能表命令 \(例如 \[**新增**\]、\[**開啟**\]、\[**儲存**\] 和 \[**另存新檔**\]\) 之應用程式。  
  
-   [如何運用使用最少文件的應用程式](#_core_applications_with_minimal_documents)。  
  
-   [如何結構化不具有文件和檢視的應用程式](#_core_applications_with_no_document)。  
  
##  <a name="_core_when_you_don.92.t_need_documents"></a> 您不需要文件的時機  
 某些應用程式的文件概念截然不同。  這些應用程式通常使用 \[開啟檔案\] 命令，從儲存體將某個檔案的全部或大部分載入至記憶體中。  它們使用 \[檔案儲存\] 或 \[**另存新檔**\] 命令，將更新的檔案一次寫回至儲存體。  使用者所看到的是資料檔。  
  
 然而，某些種類的應用程式並不需要文件。  資料庫應用程式按照交易來運作。  應用程式從資料庫中選取資料錄並呈現給使用者，通常為一次一筆。  使用者所看見的通常是單一的目前資料錄，這可能是記憶體中唯一的一筆。  
  
 如果應用程式不需要文件來儲存資料，則您可以省卻架構之部分或所有的文件\/檢視架構。  要省卻多少完全依照您的喜好而定。  您可以：  
  
-   使用最少文件，將其視為儲存資料來源連接的一個位置，但省卻一般文件功能，例如序列化。  在您想要有數個資料的檢視，並想同步處理所有檢視、一併更新它們等情況時，將會相當實用。  
  
-   使用一個可直接繪製的框架視窗 \(Frame Window\)，而非使用一個檢視。  在這種情況下，您可省略文件並且將任何資料或資料連接儲存至框架視窗物件。  
  
##  <a name="_core_appwizard_options_for_documents_and_views"></a> 文件和檢視的應用程式精靈選項  
 MFC 應用程式精靈在 \[資料庫支援\] 中有許多選項，如下表所列。  如果使用 MFC 應用程式精靈來建立應用程式，則所有這些選項會產生具有文件和檢視的應用程式。  某些選項提供了已省略非必要文件功能的文件和檢視。  如需詳細資訊，請參閱[MFC 應用程式精靈、資料庫支援](../mfc/reference/database-support-mfc-application-wizard.md)。  
  
|選項|檢視|Document|  
|--------|--------|--------------|  
|**無**|衍生自 `CView`。|不提供任何資料庫支援。  這是預設選項。<br /><br /> 如果選取在[MFC 應用程式精靈、應用程式類型](../mfc/reference/application-type-mfc-application-wizard.md)頁面中的 \[**文件\/檢視架構支援**\] 選項，就能取得完整的文件支援，包括序列化和 \[**檔案**\] 功能表上的 \[`New`\]、\[**開啟**\]、\[**儲存**\] 和 \[**另存新檔**\] 命令。  請參閱[不具文件的應用程式](#_core_applications_with_no_document)。|  
|**只有標頭檔**|衍生自 `CView`。|為應用程式提供基本層級的資料庫支援。<br /><br /> 包含 Afxdb.h。  加入連結程式庫，但不建立任何特定資料庫類別。  您可於稍後建立資料錄集，並使用他們來檢查和更新資料錄。|  
|**不提供檔案支援的資料庫檢視**|衍生自 `CRecordView`|提供文件支援但沒有序列化支援。  文件能夠儲存資料錄集並協調多重檢視，但不支援序列化或 `New`、\[開啟\]、\[**儲存**\] 和 \[**另存新檔**\] 命令。  請參閱[使用最少文件的應用程式](#_core_applications_with_minimal_documents)。  如果您要包含資料庫檢視，則必須指定資料來源。<br /><br /> 包括資料庫標頭檔、連結程式庫、資料錄檢視和資料錄集\(僅適用於在[MFC 應用程式精靈、應用程式類型](../mfc/reference/application-type-mfc-application-wizard.md)頁面中選取 \[**文件\/檢視架構支援**\] 選項的應用程式\)。|  
|**提供檔案支援的資料庫檢視**|衍生自 `CRecordView`|提供完整的文件支援，包括序列化和文件相關的 \[檔案\] 功能表命令。  資料庫應用程式通常以每筆資料錄為操作基準，而非每個檔案，因此不需要序列化。  不過，您可用特殊的方式使用序列化。  請參閱[使用最少文件的應用程式](#_core_applications_with_minimal_documents)。  如果您要包含資料庫檢視，則必須指定資料來源。<br /><br /> 包括資料庫標頭檔、連結程式庫、資料錄檢視和資料錄集\(僅適用於在[MFC 應用程式精靈、應用程式類型](../mfc/reference/application-type-mfc-application-wizard.md)頁面中選取 \[**文件\/檢視架構支援**\] 選項的應用程式\)。|  
  
 如需序列化的替代項目以及序列化的替代用法之討論，請參閱[序列化：序列化和資料庫輸入\/輸出比較](../mfc/serialization-serialization-vs-database-input-output.md)。  
  
##  <a name="_core_applications_with_minimal_documents"></a> 使用最簡文件的應用程式  
 MFC 應用程式精靈有兩個支援表單架構資料存取應用程式的選項。  每個選項都會建立一個衍生自 `CRecordView` 的檢視類別和文件。  他們的分別就是在文件內所省略的項目不同。  
  
###  <a name="_core_a_document_without_file_support"></a> 未提供檔案支援的文件  
 如果您不需要文件序列化，請選取應用程式精靈中的 \[不提供檔案支援的資料庫檢視\] 資料庫選項。  此類文件用來：  
  
-   它是儲存 `CRecordset` 物件的便利位置。  
  
     這種使用方式和平常的文件概念相似：文件儲存資料 \(或在這種情況下，是一組資料錄\)，而檢視是文件的檢視。  
  
-   如果您的應用程式具有多重檢視 \(例如：多個資料錄檢視\)，則文件會支援協調這些檢視。  
  
     如果多個檢視都顯示同樣的資料，則當任一個檢視變更資料時，您可以使用 `CDocument::UpdateAllViews` 成員函式來協調所有檢視的更新。  
  
 您通常會針對簡單表單架構應用程式使用這個選項。  應用程式精靈自動地為此類應用程式支援一個便利的結構。  
  
###  <a name="_core_a_document_with_file_support"></a> 提供檔案支援的文件  
 當您將與文件相關的 \[檔案\] 功能表命令和文件序列化的用於其他方面時，請選取應用程式精靈的 \[提供檔案支援的資料庫檢視\] 資料庫選項。  對於程式的資料存取部分，您可以用[不提供檔案支援的文件](#_core_a_document_without_file_support)中說明的方式來使用文件。  您可以使用文件的序列化功能，例如，讀取和寫入一個已序列化的使用者設定檔文件 \(此文件儲存使用者的喜好設定或其他有用的資訊\)。  如需更多概念，請參閱[序列化：序列化和資料庫輸入\/輸出比較](../mfc/serialization-serialization-vs-database-input-output.md)。  
  
 應用程式精靈支援這項選項，但是您必須撰寫序列化文件的程式碼。  請將序列化資訊儲存在文件的資料成員中。  
  
##  <a name="_core_applications_with_no_document"></a> 不具文件的應用程式  
 您有時候可能想要撰寫一個不使用文件和檢視的應用程式。  若不使用文件，您必須將資料 \(例如 `CRecordset` 物件\) 儲存在框架視窗類別或應用程式類別中。  任何其他的需求取決於應用程式是否具有使用者介面。  
  
###  <a name="_core_database_support_with_a_user_interface"></a> 具有使用者介面的資料庫支援  
 如果您有一個使用者介面 \(例如除了主控台命令列介面以外的使用者介面\)，則應用程式將直接繪製至框架視窗的工作區 \(Client Area\) 上，而非繪製到檢視上。  這種應用程式並不使用 `CRecordView`、`CFormView` 或 `CDialog` 做為主要使用者介面，但通常會使用 `CDialog` 做為一般對話方塊。  
  
###  <a name="_core_writing_applications_without_documents"></a> 撰寫不具文件的應用程式  
 因為應用程式精靈並不支援建立沒有文件的應用程式，您必須撰寫自己的 `CWinApp` 衍生類別，並且視需要建立 `CFrameWnd` 或 `CMDIFrameWnd` 類別。  覆寫 `CWinApp::InitInstance` 並將應用程式物件宣告為：  
  
```  
CYourNameApp theApp;  
```  
  
 這個架構仍然提供訊息對應 \(Message Map\) 機制和許多其他的功能。  
  
###  <a name="_core_database_support_separate_from_the_user_interface"></a> 將資料庫支援和使用者介面分開  
 某些應用程式不需要使用者介面，或只需要最少一個使用者介面。  例如，如果您撰寫：  
  
-   其他應用程式 \(用戶端\) 呼叫來作特殊資料處理 \(介於應用程式和資料來源間\) 的中繼資料存取物件。  
  
-   一個無須使用者介入處理資料的應用程式，例如將資料從某個資料庫格式移動至另一個資料庫格式的應用程式，或進行計算和執行批次更新 \(Batch Update\) 的應用程式。  
  
 由於沒有文件擁有 `CRecordset` 或 `CDaoRecordset` 物件，所以您可能會想將它儲存為 `CWinApp` 衍生應用程式類別 \(Application Class\) 中的內嵌資料成員。  作法包括：  
  
-   不要保留永久的 `CRecordset` 或 `CDaoRecordset` 物件。  您可以將 **NULL** 傳遞至您的資料錄集類別建構函式。  於該情況下，架構會建立一個暫時的 `CDatabase` 或 `CDaoDatabase` 物件，使用資料錄集的 `GetDefaultConnect` 成員函式中的資訊。  這是最有可能的替代方式。  
  
-   使 `CRecordset` 或 `CDaoRecordset` 物件成為全域變數。  這個變數應該是一個您動態建立於 `CWinApp::InitInstance` 覆寫中，指向資料錄集物件的指標。  這樣可避免在架構初始化之前就試圖建構物件。  
  
-   在文件或檢視的內容之內使用想要的資料錄集物件。  將資料錄集建立在應用程式或框架視窗物件的成員函式內。  
  
## 請參閱  
 [MFC 資料庫類別 \(ODBC 和 DAO\)](../data/mfc-database-classes-odbc-and-dao.md)