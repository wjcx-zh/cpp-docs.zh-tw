---
title: "MFC：使用具有文件和檢視的資料庫類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoRecordView 類別, 使用於資料庫應用程式"
  - "CDaoRecordView 類別, 使用於資料庫表單"
  - "CRecordView 類別, 使用於資料庫表單"
  - "DAO [C++], 資料庫應用程式中的表單"
  - "DAO 資料錄集 [C++]"
  - "DAO 資料錄集 [C++], 文件和檢視"
  - "資料庫應用程式 [C++], 表單"
  - "資料庫類別 [C++], MFC"
  - "文件/檢視架構 [C++], 在資料庫中"
  - "文件 [C++], 資料庫應用程式"
  - "表單 [C++], 資料庫應用程式"
  - "ODBC [C++], 表單"
  - "ODBC 資料錄集 [C++], 文件和檢視"
  - "資料錄檢視 [C++], 表單架構應用程式"
  - "資料錄集 [C++], 文件和檢視"
  - "檢視 [C++], 資料庫應用程式"
ms.assetid: 83979974-fc63-46ac-b162-e8403a572e2c
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# MFC：使用具有文件和檢視的資料庫類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以使用具有或不具有文件\/檢視架構的 MFC 資料庫類別 － DAO 或 ODBC。  這個主題強調於使用文件和檢視。  並說明下列主題：  
  
-   [如何撰寫表單架構應用程式](#_core_writing_a_form.2d.based_application)，藉由使用 `CRecordView` 或 `CDaoRecordView` 物件當做文件上主檢視的方式。  
  
-   [如何在文件和檢視中使用資料錄集](#_core_using_recordsets_in_documents_and_views)。  
  
-   [其他注意事項](#_core_other_factors)。  
  
 如需其他方法的詳細資訊，請參閱 [MFC：使用不具文件和檢視的資料庫類別](../data/mfc-using-database-classes-without-documents-and-views.md)。  
  
##  <a name="_core_writing_a_form.2d.based_application"></a> 撰寫表單架構應用程式  
 許多資料存取應用程式是採用表單架構。  使用者介面是一個表單，包含了使用者檢查、輸入或編輯資料的控制項。  若要使應用程式成為表單架構，請使用 `CRecordView` 或 `CDaoRecordView` 類別。  當您執行 MFC 應用程式精靈並在 \[資料庫支援\] 頁面上選取 **ODBC** 用戶端類型時，專案會使用 `CRecordView` 做為檢視類別。  此精靈不再支援 DAO，如果您要使用 `CDaoRecordView`，就必須手動加入它的程式碼。  
  
 在表單架構應用程式 \(Form\-Based Application\) 中，每個資料錄檢視 \(Record View\) 物件都儲存了一個指向 `CRecordset` 或 `CDaoRecordset` 物件的指標。  此架構的資料錄欄位交換 \(Record Field Exchange，RFX\) 機制負責交換資料錄集 \(Recordset\) 和資料來源之間的資料。  對話資料交換 \(Dialog Data Exchange，DDX\) 機制會在資料錄集物件之欄位資料成員和表單上之控制項間交換資料。  `CRecordView` 或 `CDaoRecordView` 還提供了預設的命令處理常式函式，可在表單上逐一巡覽資料錄。  
  
 若要使用應用程式精靈建立表單架構應用程式，請參閱[建立表單架構的 MFC 應用程式](../mfc/reference/creating-a-forms-based-mfc-application.md)和 [MFC 應用程式精靈、資料庫支援](../mfc/reference/database-support-mfc-application-wizard.md)。  
  
 如需表單的詳細討論，請參閱[資料錄檢視](../data/record-views-mfc-data-access.md)。  
  
##  <a name="_core_using_recordsets_in_documents_and_views"></a> 在文件和檢視中使用資料錄集  
 許多簡單的表單架構應用程式並不需要文件說明。  如果您的應用程式比較複雜，可能要使用文件來做為資料庫的 Proxy，儲存連接至資料來源的 `CDatabase` 或 `CDaoDatabase` 物件。  表單架構應用程式通常在檢視中儲存一個指向資料錄集物件的指標。  其他種類的資料庫應用程式則是在文件中儲存資料錄集和 `CDatabase` 或 `CDaoDatabase` 物件。  以下是在資料庫應用程式中使用文件的幾種可能狀況：  
  
-   如果您打算在區域內容中存取資料錄集，請視需要在文件或檢視的成員函式內建立區域的 `CRecordset` 或 `CDaoRecordset` 物件。  
  
     在函式中宣告一個資料錄集物件為區域變數 \(Local Variable\)。  將 **NULL** 傳遞至建構函式 \(Constructor\)，使架構建立並開啟一個暫存的 `CDatabase` 或 `CDaoDatabase` 物件。  或者，將一個指標傳遞至 `CDatabase` 或 `CDaoDatabase` 物件。  請在函式之中使用此資料錄集，並於函式結束時使其自動終結。  
  
     當將 **NULL** 傳遞至資料錄集建構函式時，架構會使用由資料錄集的 `GetDefaultConnect` 成員函式所傳回的資訊，來建立一個 `CDatabase` 或 `CDaoDatabase` 物件並開啟它。  精靈為您實作了 `GetDefaultConnect`。  
  
-   如果您打算於文件的存留期 \(Lifetime\) 存取資料錄集，請在文件中嵌入一或多個 `CRecordset` 或 `CDaoRecordset` 物件。  
  
     請於初始化文件時或視需要建構資料錄集物件。  如果資料錄集已經存在，您可以撰寫傳回指向資料錄集的指標的函式，如果資料錄集尚不存在，就請建構並開啟它。  請視需要關閉、刪除和重新建立資料錄集，或呼叫它的 **Requery** 成員函式以重新整理資料錄。  
  
-   如果您要於文件存留期間存取資料來源，請在文件中嵌入一個 `CDatabase` 或 `CDaoDatabase` 物件或儲存指向 `CDatabase` 或 `CDaoDatabase` 物件的指標。  
  
     `CDatabase` 或 `CDaoDatabase` 物件會管理連到您資料來源的連接。  此物件在文件建構期間時便自動建構，並且在您初始化文件時就呼叫了它的 **Open** 成員函式。  當您在文件成員函式中建構資料錄集物件時，便會將指標傳遞至文件的 `CDatabase` 或 `CDaoDatabase` 物件。  這使得每一個資料錄集和它的資料來源產生關聯。  資料庫物件通常於文件關閉時被終結。  資料錄集物件則通常於物件離開函式範圍 \(Scope\) 時被終結。  
  
##  <a name="_core_other_factors"></a> 其他因素  
 表單架構應用程式往往並未使用架構的文件序列化 \(Serialization\) 機制，所以您可能想要移除、停用或取代 \[**檔案**\] 功能表上的 \[`New`\] 和 \[**開啟**\] 命令。  請參閱文件[序列化：序列化和資料庫輸入\/輸出](../mfc/serialization-serialization-vs-database-input-output.md)。  
  
 您也可以利用此架構所支援的多使用者介面。  例如，您可以在分割視窗中使用多個 `CRecordView` 或 `CDaoRecordView` 物件，或將多個資料錄集開啟在不同的多重文件介面 \(MDI\) 子視窗上等等。  
  
 您可能會想實作列印在檢視中的任何內容，無論它是使用 `CRecordView` 或 `CDaoRecordView` 類別來實作的表單或其他內容。  衍生自 `CFormView`、`CRecordView` 和 `CDaoRecordView` 的類別並不支援列印，但是您可以覆寫 `OnPrint` 成員函式來允許列印。  如需詳細資訊，請參閱 [CFormView](../mfc/reference/cformview-class.md) 類別。  
  
 您可能根本不想要使用文件和檢視。  在這種情形下，請參閱 [MFC：使用不具文件和檢視的資料庫類別](../data/mfc-using-database-classes-without-documents-and-views.md)。  
  
## 請參閱  
 [MFC 資料庫類別 \(ODBC 和 DAO\)](../data/mfc-database-classes-odbc-and-dao.md)