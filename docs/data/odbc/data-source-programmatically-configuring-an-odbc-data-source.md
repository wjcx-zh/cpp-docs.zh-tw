---
title: 資料來源：以程式設計方式設定 ODBC 資料來源
ms.date: 11/04/2016
f1_keywords:
- SQLConfigDataSource
helpviewer_keywords:
- ODBC data sources, configuring
- SQLConfigDataSource method example
- ODBC connections, configuring
- configuring ODBC data sources
ms.assetid: b8cabe9b-9e12-4d73-ae36-7cb12dee3213
ms.openlocfilehash: 38f0f383256a05c983fb7e7d7a498e16881c7b78
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446951"
---
# <a name="data-source-programmatically-configuring-an-odbc-data-source"></a>資料來源：以程式設計方式設定 ODBC 資料來源

本主題說明如何以程式設計方式來設定開放式資料庫連接（ODBC）資料來源名稱。 這可讓您彈性地存取資料，而不會強制使用者明確地使用 ODBC 系統管理員或其他程式來指定資料來源的名稱。

一般來說，如果相關聯的資料庫管理系統（DBMS）支援這種作業，使用者就會執行 ODBC 系統管理員來建立資料來源。

透過 ODBC 管理員建立 Microsoft Access ODBC 資料來源時，您有兩個選擇：您可以選取現有的 .mdb 檔案，也可以建立新的 .mdb 檔案。 沒有任何程式設計方式可從 MFC ODBC 應用程式建立 .mdb 檔案。 因此，如果您的應用程式要求您將資料放入 Microsoft Access 資料來源（.mdb 檔案），您很可能會想要有一個空的 .mdb 檔案，您可以在需要時使用或複製該檔案。

不過，許多 Dbms 允許以程式設計方式建立資料來源。 某些資料來源會維護資料庫的目錄規格。 也就是說，目錄是資料來源，而資料來源中的每個資料表都儲存在另一個檔案中（在 dBASE 的案例中，每個資料表都是 .dbf 檔案）。 其他 ODBC 資料庫的驅動程式（例如 Microsoft Access 和 SQL Server）需要先滿足一些特定準則，才能建立資料來源。 例如，使用 SQL Server ODBC 驅動程式時，您必須已建立 SQL Server 電腦。

##  <a name="_core_sqlconfigdatasource_example"></a>SQLConfigDataSource 範例

下列範例會使用 `::SQLConfigDataSource` ODBC API 函式來建立新的 Excel 資料來源，稱為新的 Excel 資料來源：

```
SQLConfigDataSource(NULL,ODBC_ADD_DSN, "Excel Files (*.xls)",
                   "DSN=New Excel Data Source\0"
                   "Description=New Excel Data Source\0"
                   "FileType=Excel\0"
                   "DataDirectory=C:\\EXCELDIR\0"
                   "MaxScanRows=20\0");
```

請注意，資料來源實際上是目錄（C:\EXCELDIR）;此目錄必須存在。 Excel 驅動程式會使用目錄做為其資料來源和檔案，做為個別資料表（每個 .xls 檔案一個資料表）。

如需建立資料表的詳細資訊，請參閱[資料來源：以程式設計方式建立 ODBC 資料來源中的資料表](../../data/odbc/data-source-programmatically-creating-a-table-in-an-odbc-data-source.md)。

下列資訊將討論需要傳遞給 `::SQLConfigDataSource` ODBC API 函式的參數。 若要使用 `::SQLConfigDataSource`，您必須包含 Odbcinst 標頭檔，並使用 Odbcinst 的匯入程式庫。 此外，Odbccp32 在執行時間的路徑中必須是（或16位則為 Odbcinst）。

您可以使用 ODBC 系統管理員或類似的公用程式來建立 ODBC 資料來源名稱。 不過，有時候您會想要直接從您的應用程式建立資料來源名稱來取得存取權，而不需要使用者執行個別的公用程式。

ODBC 系統管理員（通常安裝在 [控制台] 中）會藉由將專案放在 Windows 登錄中（或在 Odbc .ini 檔案中為16位），來建立新的資料來源。 ODBC 驅動程式管理員會查詢此檔案，以取得資料來源的必要資訊。 請務必知道需要在登錄中放置哪些資訊，因為您需要使用 `::SQLConfigDataSource`的呼叫來提供它。

雖然這項資訊可以直接寫入登錄，而不需使用 `::SQLConfigDataSource`，但任何執行此動作的應用程式都依賴驅動程式管理員用來維護其資料的目前技術。 如果 ODBC 驅動程式管理員的更新版本以不同的方式來保存資料來源的記錄，則任何使用這項技術的應用程式都會中斷。 當提供 API 函式時，通常建議使用它。 例如，如果您使用 `::SQLConfigDataSource` 函式，您的程式碼可以從16位移植到32位，因為函式會正確寫入至 Odbc .ini 檔案或登錄。

##  <a name="_core_sqlconfigdatasource_parameters"></a>SQLConfigDataSource 參數

以下說明 `::SQLConfigDataSource` 函數的參數。 大部分的資訊都是從 ODBC API 程式設計*人員參考*（隨附于 Visual C++ 1.5 和更新版本）取得。

###  <a name="_core_function_prototype"></a>函數原型

```
BOOL SQLConfigDataSource(HWND hwndParent,UINT fRequest, LPCSTR lpszDriver, LPCSTR lpszAttributes);
```

### <a name="remarks"></a>備註

####  <a name="_core_parameters_and_usage"></a>參數和使用方式

*hwndParent*<br/>
此視窗指定為 ODBC 驅動程式管理員或特定 ODBC 驅動程式所建立之任何對話方塊的擁有者，以向使用者取得有關新資料來源的其他資訊。 如果*lpszAttributes*參數未提供足夠的資訊，則會出現對話方塊。 *HwndParent*參數可能是 Null。

*lpszDriver*<br/>
驅動程式描述。 這是向使用者顯示的名稱，而不是實體驅動程式名稱（DLL）。

*lpszAttributes*<br/>
格式為 "keyname = value" 的屬性清單。 這些字串會以 null 結束字元隔開，清單結尾有兩個連續的 null 結束字元。 這些屬性主要是預設的驅動程式特定專案，會進入新資料來源的登錄。 此函式的 ODBC API 參考中未提及的一個重要索引鍵是 "DSN" （"資料來源名稱"），它會指定新資料來源的名稱。 其餘的專案則是新資料來源的驅動程式所特有。 通常不需要提供所有專案，因為驅動程式可能會提示使用者提供新值的對話方塊。 （將*hwndParent*設定為 Null 會造成此問題）。您可能會想要明確提供預設值，讓使用者不會收到提示。

#### <a name="to-determine-the-description-of-a-driver-for-the-lpszdriver-parameter-using-odbc-administrator"></a>使用 ODBC 管理員判斷 lpszDriver 參數的驅動程式描述

1. 執行 ODBC 系統管理員。

1. 按一下 [新增]。

這會提供已安裝驅動程式的清單及其描述。 使用此描述做為*lpszDriver*參數。 請注意，您會使用完整的描述，例如 "Excel Files （* .xls）"，包括副檔名和括弧（如果它們存在於描述中）。

或者，您可以檢查登錄（或16位的檔案 Odbcinst），其中包含登錄機碼「ODBC 驅動程式」（或 Odbcinst 中的 [ODBC 驅動程式] 區段）底下所有驅動程式專案和描述的清單。

若要尋找*lpszAttributes*參數的 keynames 和值，其中一種方法是檢查已設定之資料來源（可能是由 Odbc 系統管理員設定的）的 Odbc .ini 檔案。

#### <a name="to-find-keynames-and-values-for-the-lpszattributes-parameter"></a>尋找 lpszAttributes 參數的 keynames 和值

1. 執行 Windows 登錄編輯程式（或者，針對16位，開啟 Odbc .ini 檔案）。

1. 使用下列其中一項來尋找 [ODBC 資料來源] 資訊：

   - 若為32位，請尋找**HKEY_CURRENT_USER \software\odbc\odbc. 的金鑰INI\ODBC**左窗格中的資料來源。

      右窗格會列出下列格式的專案：「pub： REG_SZ： *\<資料來源名稱 >* 」，其中 *\<資料來源名稱 >* 是已使用您想要使用之驅動程式的所需設定進行設定的資料來源。 選取您想要的資料來源，例如 SQL Server。 字串 "pub：" 後面的專案會依序列出*lpszAttributes*參數中要使用的 keyname 和 value。

   - 若是16位，請在 [ *\<資料來源名稱 >* ] 標記的 Odbc .ini 檔案中尋找區段。

      這一行後面的程式碼的格式為 "keyname = value"。 這些就是要在您的*lpszAttributes*參數中使用的專案。

您也可能想要檢查您要使用之特定驅動程式的檔集。 您可以在此驅動程式的線上說明中找到有用的資訊，您可以執行 ODBC 系統管理員來存取。 這些說明檔通常會放在 Windows NT、Windows 3.1 或 Windows 95 的 WINDOWS\SYSTEM 目錄中。

#### <a name="to-obtain-online-help-for-your-odbc-driver"></a>取得 ODBC 驅動程式的線上說明

1. 執行 ODBC 系統管理員。

1. 按一下 [新增]。

1. 選取驅動程式名稱。

1. 按一下 [確定]。

當 [ODBC 管理員] 顯示為該特定驅動程式建立新資料來源的資訊時，**請按一下 [** 說明]。 這會開啟該特定驅動程式的說明檔，其中通常包含有關使用驅動程式的重要資訊。

## <a name="see-also"></a>另請參閱

[資料來源 (ODBC)](../../data/odbc/data-source-odbc.md)
