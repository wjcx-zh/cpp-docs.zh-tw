---
title: 資料來源：管理連接 (ODBC)
ms.date: 11/04/2016
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
ms.openlocfilehash: 5b646ca0eb86d3addabaad59ca23f56cfe914114
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041159"
---
# <a name="data-source-managing-connections-odbc"></a>資料來源：管理連接 (ODBC)

本主題適用於 MFC ODBC 類別。

本主題說明：

- [如何設定資料來源](#_core_configuring_a_data_source)。

- [在多使用者環境會影響資料來源和其資料錄集](#_core_working_in_a_multiuser_environment)。

- [將一般化的資料來源的連接字串的原因](#_core_generalizing_the_connection_string)。

- [如何連接到資料來源](#_core_connecting_to_a_specific_data_source)。

- [如何從資料來源中斷連接](#_core_disconnecting_from_a_data_source)。

- [如何重新使用 CDatabase 物件](#_core_reusing_a_cdatabase_object)。

連接到資料來源是指建立與 DBMS，才可存取資料的通訊。 當您從應用程式透過 ODBC 驅動程式連接到資料來源時，此驅動程式在本機或網路上，就會建立為您的連接。

您可以連接到您的 ODBC 驅動程式的任何資料來源。 應用程式的使用者也必須擁有相同的 ODBC 驅動程式，其資料來源。 如需有關如何轉散發 ODBC 驅動程式的詳細資訊，請參閱 <<c0> [ 轉散發 ODBC 元件給您的客戶](../../data/odbc/redistributing-odbc-components-to-your-customers.md)。

##  <a name="_core_configuring_a_data_source"></a> 設定資料來源

ODBC 管理員來設定您的資料來源。 您也可以在安裝後使用 ODBC 管理員，來新增或移除資料來源。 當您建立應用程式時，您可以將使用者以 ODBC 管理員，讓使用者加入資料來源導向，或您可以藉由直接呼叫 ODBC 安裝應用程式中建置這項功能。 如需詳細資訊，請參閱 < [ODBC 管理員](../../data/odbc/odbc-administrator.md)。

您可以使用 Excel 檔案作為資料來源，以及您需要設定檔案，因此，它會註冊，並會出現在**選取資料來源** 對話方塊。

#### <a name="to-use-an-excel-file-as-a-data-source"></a>若要使用的 Excel 檔案做為資料來源

1. 使用 ODBC 資料來源管理員 」 中設定檔案。

1. 在 **檔案 DSN**索引標籤上，按一下**新增**。

1. 在 **建立新的資料來源** 對話方塊中，選取 Excel 驅動程式，然後按一下**下一步**。

1. 按一下 **瀏覽**，然後選取要用作資料來源的檔案名稱。

> [!NOTE]
>  您可能需要選取**的所有檔案**下拉式選單，以檢視.xls 檔案中。

1. 按 [下一步] ，然後按一下 [完成] 。

1. 在  **ODBC Microsoft Excel 設定**對話方塊方塊中，選取的資料庫版本和活頁簿。

##  <a name="_core_working_in_a_multiuser_environment"></a> 在多使用者環境中工作

如果多個使用者連接到資料來源，他們就可以變更資料，而您正在操作它在您的資料錄集。 同樣地，您的變更可能會影響其他使用者的資料錄集。 如需詳細資訊，請參閱[資料錄集：資料錄集更新資料錄 (ODBC) 的方式](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)並[異動 (ODBC)](../../data/odbc/transaction-odbc.md)。

##  <a name="_core_generalizing_the_connection_string"></a> 連接字串一般化

精靈會使用預設的連接字串來建立資料來源的連接。 您可以使用這個連接若要檢視資料表和資料行，而您正在開發您的應用程式。 不過，這個預設的連接字串可能不適合您的使用者連線到資料來源，透過您的應用程式。 比方說，他們的資料來源和其位置的路徑可能不同於另一個用於開發您的應用程式。 在此情況下，您應該實作[crecordset:: Getdefaultconnect](../../mfc/reference/crecordset-class.md#getdefaultconnect)成員函式以更泛型的方式，並捨棄精靈的實作。 例如，使用下列方法之一：

- 註冊並管理使用 ODBC 管理員的連接字串。

- 編輯連接字串，並移除資料來源的名稱。 此架構提供 ODBC 做為資料來源;在執行階段，ODBC 會顯示對話方塊，詢問的資料來源名稱和其他任何必要的連接資訊。

- 提供的資料來源名稱。 如有需要，會要求使用者識別碼和密碼的 ODBC。 比方說，然後再將一般化，連接字串看起來像這樣：

    ```cpp
    CString CApp1Set::GetDefaultConnect()
    {
       return "ODBC;DSN=afx;Trusted_Connection=Yes;";
    }
    ```

   此連接字串會指定信任的連接，它會使用 Windows NT 整合式安全性。 您應該避免硬式編碼的密碼，或指定空白的密碼，因為這樣會建立主要的安全性弱點。 相反地，您可以提供`GetDefaultConnect`新的連接字串，以便讓它查詢使用者 ID 和密碼。

    ```cpp
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

若要連接到特定的資料來源，您的資料來源必須已經有設有[ODBC 管理員](../../data/odbc/odbc-administrator.md)。

#### <a name="to-connect-to-a-specific-data-source"></a>若要連接到特定的資料來源

1. 建構`CDatabase`物件。

1. 呼叫其`OpenEx`或`Open`成員函式。

如需如何指定資料來源，如果您使用精靈所指定以外的詳細資訊，請參閱[CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex)或是[Openex](../../mfc/reference/cdatabase-class.md#open)在*MFC參考*。

##  <a name="_core_disconnecting_from_a_data_source"></a> 從資料來源中斷連接

您必須先關閉任何開啟的記錄集，然後再呼叫`Close`成員函式`CDatabase`。 在相關聯的資料錄集中`CDatabase`物件您想要關閉任何暫止`AddNew`或`Edit`陳述式會取消，且會回復所有暫止交易。

#### <a name="to-disconnect-from-a-data-source"></a>若要從資料來源中斷連線

1. 呼叫`CDatabase`物件的[關閉](../../mfc/reference/cdatabase-class.md#close)成員函式。

1. 終結物件，除非您想要重複使用它。

##  <a name="_core_reusing_a_cdatabase_object"></a> 重新使用 CDatabase 物件

您可以重複使用`CDatabase`之後中斷，不論您是使用它來重新連線到相同的資料來源，或連接到不同的資料來源的物件。

#### <a name="to-reuse-a-cdatabase-object"></a>若要使用 CDatabase 物件

1. 關閉物件的原始連接。

1. 而不是終止此物件，呼叫其`OpenEx`或`Open`成員函式一次。

## <a name="see-also"></a>另請參閱

[資料來源 (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[資料來源：判斷資料來源 (ODBC) 的結構描述](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)