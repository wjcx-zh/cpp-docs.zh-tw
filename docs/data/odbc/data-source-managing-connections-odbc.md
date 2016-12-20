---
title: "資料來源：管理連接 (ODBC) | Microsoft Docs"
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
  - "連接字串 [C++], 一般化"
  - "連接 [C++], 資料來源"
  - "資料來源 [C++], 連接至"
  - "資料庫連接 [C++], 建立"
  - "資料庫連接 [C++], MFC ODBC 類別"
  - "資料庫 [C++], 連接至"
  - "中斷與資料來源的連接"
  - "一般化連接字串"
  - "GetDefaultConnect 方法"
  - "ODBC [C++], 中斷與資料來源的連接"
  - "ODBC 連接 [C++], 設定"
  - "ODBC 連接 [C++], 連接至資料來源"
  - "ODBC 連接 [C++], 中斷連接"
  - "ODBC 資料來源 [C++], 連接"
  - "ODBC 資料來源 [C++], 多使用者環境"
ms.assetid: c0adbcdd-c000-40c6-b199-09ffdc7b6ef2
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 資料來源：管理連接 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件適用於 MFC ODBC 類別。  
  
 這個主題說明：  
  
-   [如何設定資料來源](#_core_configuring_a_data_source)。  
  
-   [多使用者環境如何影響資料來源和其資料錄集](#_core_working_in_a_multiuser_environment)。  
  
-   [您為何要將連接字串一般化成資料來源](#_core_generalizing_the_connection_string)。  
  
-   [如何連接資料來源](#_core_connecting_to_a_specific_data_source)。  
  
-   [如何從資料來源中斷連接](#_core_disconnecting_from_a_data_source)。  
  
-   [如何重新使用 CDatabase 物件](#_core_reusing_a_cdatabase_object)。  
  
 連接資料來源是指建立與 DBMS 的溝通以便存取資料。  當您透過一個 ODBC 驅動程式從一個應用程式連接到資料來源時，驅動程式會為您製作一個連接 \(無論是本機或是透過網路的\)。  
  
 您可以連接到任何您有 ODBC 驅動程式的資料來源。  您的應用程式使用者必須也具有其資料來源相同的 ODBC 驅動程式。  如需轉散發 ODBC 驅動程式的詳細資訊，請參閱[轉散發 ODBC 元件給您的客戶](../../data/odbc/redistributing-odbc-components-to-your-customers.md)。  
  
##  <a name="_core_configuring_a_data_source"></a> 設定資料來源  
 ODBC 管理員可用來設定您的資料來源。  您也可以在完成安裝之後，使用 ODBC 管理員來加入或移除資料來源。  建立應用程式時，您可以將使用者導向 ODBC 管理員，讓使用者可以加入資料來源，或者利用製作直接的 ODBC 安裝呼叫，將這個功能建置在您的應用程式中。  如需詳細資訊，請參閱 [ODBC 管理員](../../data/odbc/odbc-administrator.md)。  
  
 您可以將一個 Excel 檔案當成資料來源來使用，此外您必須將該檔案設定為登錄，使其出現在 \[選定資料來源\] 對話方塊中。  
  
#### 若要將 Excel 檔案當做資料來源來使用  
  
1.  設定 ODBC 資料來源管理員的檔案。  
  
2.  在 \[檔案型 DSN\] 標籤上，按一下 \[加入\]。  
  
3.  在 \[建立新資料來源\] 對話方塊中選取 Excel 驅動程式，然後按 \[**下一步**\]。  
  
4.  按一下 \[瀏覽\]，然後選取要當做資料來源的檔案名稱。  
  
> [!NOTE]
>  您可能會需要在下拉式功能表中 \[**所有檔案**\] 以檢視 .xls 檔案。  
  
1.  按 \[**下一步**\]，再按一下 \[**完成**\]。  
  
2.  在 \[ODBC Microsoft Excel 設定\] 對話方塊中，選取資料庫版本和活頁簿。  
  
##  <a name="_core_working_in_a_multiuser_environment"></a> 在多使用者環境中作業  
 若有多位使用者連接到一個資料來源，他們就可在您操作資料錄集的資料來源時改變資料。  同樣地，您做的變更可能會影響其他使用者的資料錄集。  如需詳細資訊，請參閱[資料錄集：資料錄集更新資料錄的方式 \(ODBC\)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) 和[交易 \(ODBC\)](../../data/odbc/transaction-odbc.md)。  
  
##  <a name="_core_generalizing_the_connection_string"></a> 連接字串一般化  
 精靈會使用一個預設的連接字串來建立資料來源的連接。  您可以在開發應用程式時，使用這個連接來檢視資料表和資料行。  但是，這個預設的連接字串可能不適用於透過應用程式來進行使用者與資料來源的連接。  例如，他們的資料來源和位置路徑，可能和您在開發應用程式時所用的不相同。  因此，您應該以更廣義的形式來重新實作 [CRecordset::GetDefaultConnect](../Topic/CRecordset::GetDefaultConnect.md) 成員函式，並捨棄精靈的實作方式。  例如，使用下列其中之一方法：  
  
-   使用 ODBC 管理員登錄和管理連接字串。  
  
-   編輯連接字串並移除資料來源名稱。  此架構提供 ODBC 做為資料來源，而 ODBC 會在執行階段顯示對話方塊，要求資料來源名稱和其他任何所需的連接資訊。  
  
-   僅提供資料來源名稱。  ODBC 在必要時會要求使用者 ID 和密碼。  例如，連接字串在一般化之前看起來會像是這樣：  
  
    ```  
    CString CApp1Set::GetDefaultConnect()  
    {  
       return "ODBC;DSN=afx;Trusted_Connection=Yes;";  
    }  
    ```  
  
     此連接字串會指定信任的連接 \(使用 Windows NT 的整合式安全性\)。  您應避免將密碼直接寫入程式碼內，或指定空白的密碼，因為這樣做會產生重大的安全性漏洞。  反之，您可提供 `GetDefaultConnect` 一個新的連接字串，以便讓它查詢使用者 ID 和密碼。  
  
    ```  
    // User must select data source and supply user ID and password:  
        return "ODBC;";  
    // User ID and password required:  
        return "ODBC;DSN=mydb;";  
    // Password required (myuserid must be replaced with a valid user ID):  
        return "ODBC;DSN=mydb;UID=myuserid;";  
    // Hard-coded user ID and password (SECURITY WEAKNESS--AVOID):  
        return "ODBC;DSN=mydb;UID=sa;PWD=777;";  
    ```  
  
##  <a name="_core_connecting_to_a_specific_data_source"></a> 連接特定資料來源  
 若要連接一個特定資料來源，您的資料來源必須已經使用 [ODBC 管理員](../../data/odbc/odbc-administrator.md)完成設定。  
  
#### 若要連接特定資料來源  
  
1.  建構 `CDatabase` 物件。  
  
2.  呼叫該物件的 `OpenEx` 或 **Open** 成員函式。  
  
 如需指定在精靈以外指定的資料來源之詳細資訊，請參閱《MFC 參考》中的 [CDatabase::OpenEx](../Topic/CDatabase::OpenEx.md) 或 [CDatabase::Open](../Topic/CDatabase::Open.md)。  
  
##  <a name="_core_disconnecting_from_a_data_source"></a> 從資料來源中斷連接  
 您必須在呼叫 `CDatabase` 的 **Close** 成員函式之前關閉任何開啟的資料錄集。  在與您想關閉的 `CDatabase` 物件相關聯的資料錄集中，任何暫止的 `AddNew` 或 **Edit** 陳述式都會被取消，且會復原所有暫止的交易。  
  
#### 若要從資料來源中斷連接  
  
1.  呼叫 `CDatabase` 物件的 [Close](../Topic/CDatabase::Close.md) 成員函式。  
  
2.  除非您希望重新使用此物件否則請將其終止。  
  
##  <a name="_core_reusing_a_cdatabase_object"></a> 重新使用 CDatabase 物件  
 您可以在從 `CDatabase` 物件中斷連接之後重新使用該物件，不管您會將其重新連接到相同的資料來源或是不同的資料來源。  
  
#### 若要重新使用 CDatabase 物件  
  
1.  關閉物件的原始連接。  
  
2.  無需終止此物件，請再次呼叫其 `OpenEx` 或 **Open** 成員函式。  
  
## 請參閱  
 [資料來源 \(ODBC\)](../../data/odbc/data-source-odbc.md)   
 [資料來源：決定資料來源的結構描述 \(ODBC\)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)