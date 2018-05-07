---
title: 資料來源： 管理連接 (ODBC) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC data sources [C++], multiuser environments
- generalizing connection strings
- ODBC [C++], disconnecting from data sources
- connection strings [C++], generalizing
- database connections [C++], creating
- GetDefaultConnect method
- connections [C++], data source
- ODBC connections [C++], configuring
- disconnecting from data sources
- databases [C++], connecting to
- ODBC connections [C++], disconnecting
- data sources [C++], connecting to
- ODBC connections [C++], connecting to data source
- ODBC data sources [C++], connections
- database connections [C++], MFC ODBC classes
ms.assetid: c0adbcdd-c000-40c6-b199-09ffdc7b6ef2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 100c06773a8f0ffa79631339384bd4ec42fa4b52
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="data-source-managing-connections-odbc"></a>資料來源：管理連接 (ODBC)
本主題適用於 MFC ODBC 類別。  
  
 本主題說明：  
  
-   [如何設定資料來源](#_core_configuring_a_data_source)。  
  
-   [多使用者環境會影響資料來源和其資料錄集](#_core_working_in_a_multiuser_environment)。  
  
-   [為什麼一般化資料來源的連接字串](#_core_generalizing_the_connection_string)。  
  
-   [如何連接到資料來源](#_core_connecting_to_a_specific_data_source)。  
  
-   [如何從資料來源中斷連接](#_core_disconnecting_from_a_data_source)。  
  
-   [如何重複使用 CDatabase 物件](#_core_reusing_a_cdatabase_object)。  
  
 連接到資料來源是指建立通訊皆使用 dbms，才可存取的資料。 當您從應用程式透過 ODBC 驅動程式連接到資料來源時，驅動程式 」 建立的連接，請在本機或網路上。  
  
 您可以連接至具有 ODBC 驅動程式的任何資料來源。 應用程式的使用者也必須有相同的 ODBC 驅動程式，其資料來源。 如需轉散發 ODBC 驅動程式的詳細資訊，請參閱[轉散發 ODBC 元件給您的客戶](../../data/odbc/redistributing-odbc-components-to-your-customers.md)。  
  
##  <a name="_core_configuring_a_data_source"></a> 設定資料來源  
 ODBC 管理員用來設定您的資料來源。 您也可以在安裝後使用 ODBC 管理員，來新增或移除資料來源。 當您建立應用程式時，您可以讓他們新增資料來源 ODBC 管理員將使用者導向，或您可以藉由直接呼叫 ODBC 安裝到您的應用程式建立這項功能。 如需詳細資訊，請參閱[ODBC 管理員](../../data/odbc/odbc-administrator.md)。  
  
 您可以使用 Excel 檔案做為資料來源，以及您需要註冊，使其出現在設定檔案**選取資料來源** 對話方塊。  
  
#### <a name="to-use-an-excel-file-as-a-data-source"></a>若要使用 Excel 檔案做為資料來源  
  
1.  設定檔案使用 ODBC 資料來源管理員。  
  
2.  在**檔案 DSN**索引標籤上，按一下 **新增**。  
  
3.  在**建立新的資料來源**對話方塊中，選取 Excel 驅動程式，然後按一下**下一步**。  
  
4.  按一下**瀏覽**，然後選取要做為資料來源檔案的名稱。  
  
> [!NOTE]
>  您可能需要選取**所有檔案**下拉式選單，若要檢視.xls 檔案中。  
  
1.  按 [下一步] ，然後按一下 [完成] 。  
  
2.  在**ODBC Microsoft Excel 安裝**對話方塊方塊中，選取的資料庫版本和活頁簿。  
  
##  <a name="_core_working_in_a_multiuser_environment"></a> 在多使用者環境中工作  
 如果多個使用者連接到資料來源，他們可以變更資料，您會在您的資料錄集中操作時。 同樣地，您的變更可能會影響其他使用者的資料錄集。 如需詳細資訊，請參閱[資料錄集： 資料錄集更新資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)和[異動 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
##  <a name="_core_generalizing_the_connection_string"></a> 一般化連接字串  
 精靈會使用預設連接字串來建立資料來源的連接。 您可以使用這個連接來開發您的應用程式時，檢視資料表和資料行。 不過，這個預設的連接字串不可能適用於您的使用者資料來源連接到您的應用程式。 比方說，他們的資料來源以及其位置的路徑可能不同於開發應用程式中使用。 在此情況下，您應該實作[CRecordset::GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect)成員函式以更泛型的方式，並捨棄精靈實作。 例如，使用下列方法之一：  
  
-   登錄和管理使用 ODBC 管理員的連接字串。  
  
-   編輯連接字串，並移除資料來源名稱。 架構會提供 ODBC 做為資料來源;在執行階段，ODBC 會顯示對話方塊，詢問的資料來源名稱和任何其他必要的連接資訊。  
  
-   資料來源僅提供名稱。 必要時，會要求使用者識別碼和密碼的 ODBC。 例如，一般化之前的連接字串看起來像這樣：  
  
    ```  
    CString CApp1Set::GetDefaultConnect()  
    {  
       return "ODBC;DSN=afx;Trusted_Connection=Yes;";  
    }  
    ```  
  
     這個連接字串指定信任的連接，這會使用 Windows NT 整合式安全性。 您應該避免進行硬式編碼密碼，或指定空白的密碼，因為這樣會建立主要的安全性弱點。 相反地，您就能給予`GetDefaultConnect`新的連接字串，以便進行查詢的使用者識別碼和密碼。  
  
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
  
##  <a name="_core_connecting_to_a_specific_data_source"></a> 連接到特定的資料來源  
 若要連接到特定的資料來源，您的資料來源必須已經設定使用[ODBC 管理員](../../data/odbc/odbc-administrator.md)。  
  
#### <a name="to-connect-to-a-specific-data-source"></a>若要連接到特定的資料來源  
  
1.  建構`CDatabase`物件。  
  
2.  呼叫其`OpenEx`或**開啟**成員函式。  
  
 如需如何在您使用精靈指定以外的項目時，指定資料來源的詳細資訊，請參閱[CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex)或[CDatabase::Open](../../mfc/reference/cdatabase-class.md#open)中*MFC參考*。  
  
##  <a name="_core_disconnecting_from_a_data_source"></a> 從資料來源中斷連線  
 您必須先關閉任何開啟的資料錄集之前先呼叫**關閉**成員函式`CDatabase`。 在相關聯的資料錄集中`CDatabase`物件您想要關閉任何暫止`AddNew`或**編輯**陳述式則會取消，且所有暫止的交易會會回復。  
  
#### <a name="to-disconnect-from-a-data-source"></a>若要從資料來源中斷連線  
  
1.  呼叫`CDatabase`物件的[關閉](../../mfc/reference/cdatabase-class.md#close)成員函式。  
  
2.  終結物件，除非您想要重複使用它。  
  
##  <a name="_core_reusing_a_cdatabase_object"></a> 重複使用 CDatabase 物件  
 您可以重複使用`CDatabase`之後中斷，無論您是使用它來重新連線到相同的資料來源，或連接到不同的資料來源的物件。  
  
#### <a name="to-reuse-a-cdatabase-object"></a>若要重複使用 CDatabase 物件  
  
1.  關閉物件的原始連接。  
  
2.  而不是終結物件，呼叫其`OpenEx`或**開啟**成員函式一次。  
  
## <a name="see-also"></a>另請參閱  
 [資料來源 (ODBC)](../../data/odbc/data-source-odbc.md)   
 [資料來源： 決定資料來源 (ODBC) 的結構描述](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)   
 [CRecordset 類別](../../mfc/reference/crecordset-class.md)