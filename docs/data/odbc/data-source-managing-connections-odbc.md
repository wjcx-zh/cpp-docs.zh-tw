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
ms.openlocfilehash: 6186199ea51c1fc966783ed3c0a73496c6a307ee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213288"
---
# <a name="data-source-managing-connections-odbc"></a>資料來源：管理連接 (ODBC)

本主題適用於 MFC ODBC 類別。

本主題將說明：

- [如何設定資料來源](#_core_configuring_a_data_source)。

- [多使用者環境如何影響資料來源及其記錄集](#_core_working_in_a_multiuser_environment)。

- [為何將連接字串一般化至資料來源](#_core_generalizing_the_connection_string)。

- [如何連接至資料來源](#_core_connecting_to_a_specific_data_source)。

- [如何中斷與資料來源的](#_core_disconnecting_from_a_data_source)連線。

- [如何重複使用 CDatabase 物件](#_core_reusing_a_cdatabase_object)。

連接到資料來源表示要建立與 DBMS 的通訊來存取資料。 當您透過 ODBC 驅動程式從應用程式連接到資料來源時，驅動程式會在本機或網路上為您建立連接。

您可以連接到任何具有 ODBC 驅動程式的資料來源。 應用程式使用者的資料來源也必須有相同的 ODBC 驅動程式。 如需轉散發 ODBC 驅動程式的詳細資訊，請參閱將[Odbc 元件轉散發給您的客戶](../../data/odbc/redistributing-odbc-components-to-your-customers.md)。

##  <a name="configuring-a-data-source"></a><a name="_core_configuring_a_data_source"></a>設定資料來源

ODBC 管理員是用來設定您的資料來源。 您也可以在安裝後使用 [ODBC 管理員] 來新增或移除資料來源。 當您建立應用程式時，您可以將使用者導向至 ODBC 系統管理員，讓他們新增資料來源，或者您可以藉由直接 ODBC 安裝呼叫，在應用程式中建立這項功能。 如需詳細資訊，請參閱[ODBC 系統管理員](../../data/odbc/odbc-administrator.md)。

您可以使用 Excel 檔案做為資料來源，而且您需要設定該檔案，使其已註冊並出現在 [**選取資料來源**] 對話方塊中。

#### <a name="to-use-an-excel-file-as-a-data-source"></a>若要使用 Excel 檔案做為資料來源

1. 使用 [ODBC 資料來源管理員] 來設定檔案。

1. 在 [檔案**DSN** ] 索引標籤上，按一下 [**新增**]。

1. 在 [**建立新的資料來源**] 對話方塊中，選取 Excel 驅動程式，然後按 **[下一步]** 。

1. 按一下 **[流覽]** ，然後選取要當做日期來源使用的檔案名。

> [!NOTE]
>  您可能需要選取下拉式功能表中的 [**所有**檔案]，以查看 .xls 檔案。

1. 按 **[下一步]** ，再按一下 **[完成]** 。

1. 在 [ **ODBC Microsoft Excel 安裝程式**] 對話方塊中，選取 [資料庫版本] 和 [活頁簿]。

##  <a name="working-in-a-multiuser-environment"></a><a name="_core_working_in_a_multiuser_environment"></a>在多使用者環境中工作

如果有多個使用者連接到資料來源，當您在記錄集中運算元據時，他們可以變更資料。 同樣地，您的變更可能會影響其他使用者的記錄集。 如需詳細資訊，請參閱[記錄集：記錄集更新記錄的方式（odbc）](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)和[交易（odbc）](../../data/odbc/transaction-odbc.md)。

##  <a name="generalizing-the-connection-string"></a><a name="_core_generalizing_the_connection_string"></a>將連接字串一般化

這些嚮導會使用預設連接字串來建立資料來源的連接。 當您開發應用程式時，您可以使用此連接來查看資料表和資料行。 不過，這個預設連接字串可能不適合您的使用者透過應用程式連接到資料來源的情況。 例如，其資料來源和其位置路徑可能與開發應用程式時所使用的不同。 在這種情況下，您應該以更通用的方式重新執行[CRecordset：： GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect)成員函式，並捨棄 wizard 的執行功能。 例如，請使用下列其中一種方法：

- 使用 ODBC 管理員來註冊和管理連接字串。

- 編輯連接字串，並移除資料來源名稱。 此架構會提供 ODBC 做為資料來源;在執行時間，ODBC 會顯示對話方塊，要求您提供資料來源名稱和任何其他必要的連接資訊。

- 僅提供資料來源名稱。 如有需要，ODBC 會要求使用者識別碼和密碼。 例如，在一般化之前，連接字串看起來像這樣：

    ```cpp
    CString CApp1Set::GetDefaultConnect()
    {
       return "ODBC;DSN=afx;Trusted_Connection=Yes;";
    }
    ```

   此連接字串指定了信任連接，其使用 Windows NT 整合式安全性。 您應該避免硬式編碼密碼或指定空白密碼，因為這樣做會造成重大的安全性弱點。 相反地，您可以提供 `GetDefaultConnect` 新的連接字串，讓它查詢使用者識別碼和密碼。

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

##  <a name="connecting-to-a-specific-data-source"></a><a name="_core_connecting_to_a_specific_data_source"></a>連接到特定資料來源

若要連接到特定的資料來源，您的資料來源必須已經使用[ODBC 管理員](../../data/odbc/odbc-administrator.md)設定。

#### <a name="to-connect-to-a-specific-data-source"></a>若要連接到特定資料來源

1. 建立 `CDatabase` 物件。

1. 呼叫其 `OpenEx` 或 `Open` 成員函式。

如需如何指定資料來源的詳細資訊（如果它不是您使用 wizard 所指定的來源），請參閱*MFC 參考*中的[Cdatabase：： microsoft.office.interop.visio.documents.open](../../mfc/reference/cdatabase-class.md#openex)或[cdatabase：： Open](../../mfc/reference/cdatabase-class.md#open) 。

##  <a name="disconnecting-from-a-data-source"></a><a name="_core_disconnecting_from_a_data_source"></a>中斷與資料來源的連線

您必須先關閉任何開啟的記錄集，再呼叫 `CDatabase`的 `Close` 成員函式。 在與您要關閉的 `CDatabase` 物件相關聯的記錄集內，會取消任何暫止的 `AddNew` 或 `Edit` 語句，並復原所有暫止的交易。

#### <a name="to-disconnect-from-a-data-source"></a>中斷與資料來源的連線

1. 呼叫 `CDatabase` 物件的[Close](../../mfc/reference/cdatabase-class.md#close)成員函式。

1. 終結物件，除非您想要重複使用它。

##  <a name="reusing-a-cdatabase-object"></a><a name="_core_reusing_a_cdatabase_object"></a>重複使用 CDatabase 物件

您可以在中斷連接後重複使用 `CDatabase` 物件，不論您是使用它來重新連接到相同的資料來源，還是連接到不同的資料來源。

#### <a name="to-reuse-a-cdatabase-object"></a>重複使用 CDatabase 物件

1. 關閉物件的原始連接。

1. 請不要終結物件，而是再次呼叫其 `OpenEx` 或 `Open` 成員函式。

## <a name="see-also"></a>另請參閱

[資料來源 (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[資料來源：決定資料來源的結構描述 (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)
