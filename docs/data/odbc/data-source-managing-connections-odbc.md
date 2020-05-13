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
ms.openlocfilehash: 107a5e20b70f67be74b6e6f861bd539446e9d4ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374522"
---
# <a name="data-source-managing-connections-odbc"></a>資料來源：管理連接 (ODBC)

本主題適用於 MFC ODBC 類別。

本主題將說明：

- [如何設定資料來源](#_core_configuring_a_data_source)。

- [多使用者環境如何影響資料來源與紀錄集](#_core_working_in_a_multiuser_environment)。

- [為什麼將連接字串的概括為資料來源](#_core_generalizing_the_connection_string)。

- [如何連線到資料來源](#_core_connecting_to_a_specific_data_source)。

- [如何斷線與資料來源的連線](#_core_disconnecting_from_a_data_source)。

- [如何重用 CDatabase 物件](#_core_reusing_a_cdatabase_object)。

連接到數據源意味著與 DBMS 建立通信以訪問數據。 當您透過 ODBC 驅動程式從應用程式連接到資料來源時,驅動程式會在本地或網路中為您建立連接。

您可以連接到具有 ODBC 驅動程式的任何資料來源。 應用程式的用戶還必須為其數據來源使用相同的ODBC驅動程式。 有關重新分發 ODBC 驅動程式的詳細資訊,請參閱[將 ODBC 元件重新分發給您的客戶](../../data/odbc/redistributing-odbc-components-to-your-customers.md)。

## <a name="configuring-a-data-source"></a><a name="_core_configuring_a_data_source"></a>設定資料來源

ODBC 管理員用於配置數據源。 您還可以在安裝後使用 ODBC 管理員添加或刪除數據來源。 創建應用程式時,可以將使用者定向到 ODBC 管理員,讓他們添加數據源,也可以通過直接進行 ODBC 安裝調用將此功能構建到應用程式中。 有關詳細資訊,請參閱[ODBC 管理員](../../data/odbc/odbc-administrator.md)。

您可以將 Excel 檔用作資料來源,並且需要設定該檔,以便該檔被註冊並顯示在 **「選擇資料來源**」對話框中。

#### <a name="to-use-an-excel-file-as-a-data-source"></a>將 Excel 檔案用作資料來源

1. 使用 ODBC 資料來源管理員配置檔。

1. 在 **「檔案 DSN」** 選項卡上,按下「**添加**」 。

1. 在 **"創建新資料源'** 對話框中,選擇 Excel 驅動程式,然後單擊「**下一步**」。

1. 按下 **「瀏覽**」並選擇要用作日期來源的檔案名稱。

> [!NOTE]
> 您可能需要選擇下拉選單中的所有**檔案**才能查看 .xls 檔案。

1. 按 [下一步]****，然後按一下 [完成]****。

1. 在**ODBC 微軟 Excel 設置**對話框中,選擇資料庫版本和工作簿。

## <a name="working-in-a-multiuser-environment"></a><a name="_core_working_in_a_multiuser_environment"></a>在多使用者環境中工作

如果多個使用者連接到數據源,則可以在記錄集中操作數據時更改數據。 同樣,您的更改可能會影響其他用戶的記錄集。 有關詳細資訊,請參閱[記錄集:記錄集如何更新記錄 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)和[事務 (ODBC)。](../../data/odbc/transaction-odbc.md)

## <a name="generalizing-the-connection-string"></a><a name="_core_generalizing_the_connection_string"></a>概括連接字串

嚮導使用預設連接字串建立與數據源的連接。 在開發應用程式時,使用此連接可以查看表和列。 但是,此預設連接字串可能不適合用戶通過應用程式連接到數據源。 例如,它們的數據源及其位置的路徑可能與開發應用程式時所使用的路徑不同。 在這種情況下,您應該以更通用的方式重新實現[CRecordset::getDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect)成員函數,並放棄嚮導實現。 例如,使用以下方法之一:

- 使用 ODBC 管理員註冊和管理連接字串。

- 編輯連接字串並刪除資料來源名稱。 該框架提供ODBC作為數據源;在運行時,ODBC 將顯示一個對話框,詢問數據源名稱和任何其他必需的連接資訊。

- 僅提供數據源名稱。 如果需要,ODBC 會詢問使用者 ID 和密碼。 例如,在概括之前,連接字串如下所示:

    ```cpp
    CString CApp1Set::GetDefaultConnect()
    {
       return "ODBC;DSN=afx;Trusted_Connection=Yes;";
    }
    ```

   此連接字串指定使用 Windows NT 整合安全性的受信任連接。 應避免對密碼進行硬編碼或指定空白密碼,因為這樣做會產生重大的安全缺陷。 相反,您可以提供新的`GetDefaultConnect`連接字串,以便它查詢使用者 ID 和密碼。

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

## <a name="connecting-to-a-specific-data-source"></a><a name="_core_connecting_to_a_specific_data_source"></a>連接到特定資料來源

要連線到特定資料來源,資料來源必須設定了[ODBC 管理員](../../data/odbc/odbc-administrator.md)。

#### <a name="to-connect-to-a-specific-data-source"></a>連接到特定資料來源

1. 構造`CDatabase`物件。

1. 調用其`OpenEx``Open`或成員函數。

有關如何指定數據源(如果數據來源是使用嚮導指定的數據源以外的數據來源)的詳細資訊,請參閱[CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex)或[CDatabase::](../../mfc/reference/cdatabase-class.md#open)在*MFC 參考*中打開。

## <a name="disconnecting-from-a-data-source"></a><a name="_core_disconnecting_from_a_data_source"></a>與資料源斷線連線

在呼叫的成員函數之前,`Close`必須關閉任何打開的記錄`CDatabase`集。 在與要關閉`CDatabase`的物件關聯的記錄集中,將取消任何掛`AddNew`起`Edit`或語句,並回滾所有掛起的事務。

#### <a name="to-disconnect-from-a-data-source"></a>與資料源斷線連線

1. 調用`CDatabase`物件的[關閉](../../mfc/reference/cdatabase-class.md#close)成員函數。

1. 銷毀物件,除非您要重用它。

## <a name="reusing-a-cdatabase-object"></a><a name="_core_reusing_a_cdatabase_object"></a>重用 C 資料庫物件

在斷開`CDatabase`物件斷開后,可以重用該物件,無論是使用它重新連接到同一數據源還是連接到其他數據源。

#### <a name="to-reuse-a-cdatabase-object"></a>重用 CDatabase 物件

1. 關閉對象的原始連接。

1. 不要破壞物件,而是再次調用其`OpenEx``Open`或成員函數。

## <a name="see-also"></a>另請參閱

[資料來源](../../data/odbc/data-source-odbc.md)<br/>
[資料來源：決定資料來源的結構描述 (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)
