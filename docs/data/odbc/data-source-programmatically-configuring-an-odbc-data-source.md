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
ms.openlocfilehash: 3d02a19d6c61e79fffd31b67ef1b8f7ea9007fcb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677366"
---
# <a name="data-source-programmatically-configuring-an-odbc-data-source"></a>資料來源：以程式設計方式設定 ODBC 資料來源

本主題說明如何以程式設計方式設定開放式資料庫連接 (ODBC) 資料來源名稱。 這可讓您彈性來存取資料無須強制使用者明確使用 ODBC 管理員或其他程式，以指定的資料來源的名稱。

一般而言，使用者會執行 ODBC 管理員來建立資料來源，如果相關聯的資料庫管理系統 (DBMS) 支援此作業。

當建立 Microsoft Access ODBC 資料來源透過 ODBC 管理員，您會有兩種選擇： 您可以選取現有的.mdb 檔，或您可以建立新的.mdb 檔。 沒有任何以程式設計方式建立從 MFC ODBC 應用程式的.mdb 檔。 因此，如果您的應用程式需要您將資料放入 Microsoft Access 資料來源 （.mdb 檔），您很可能會想要有空白.mdb 檔案，您可以使用或複製您在需要時。

不過，有許多 Dbms 允許以程式設計方式的資料來源建立。 某些資料來源維護一個目錄規格的資料庫。 也就是說，目錄就是資料來源和資料來源中的每個資料表會儲存在個別的檔案 （若為 dBASE，每個資料表是一個.dbf 檔）。 其他 ODBC 資料庫，例如 Microsoft Access 和 SQL Server 的驅動程式需要可以建立資料來源之前，先滿足一些特定準則。 例如，當 SQL Server ODBC 驅動程式，您需要已建立的 SQL Server 電腦。

##  <a name="_core_sqlconfigdatasource_example"></a> SQLConfigDataSource 範例

下列範例會使用`::SQLConfigDataSource`來建立新的 Excel 資料來源的 ODBC API 函式呼叫新的 Excel 資料來源：

```
SQLConfigDataSource(NULL,ODBC_ADD_DSN, "Excel Files (*.xls)",
                   "DSN=New Excel Data Source\0"
                   "Description=New Excel Data Source\0"
                   "FileType=Excel\0"
                   "DataDirectory=C:\\EXCELDIR\0"
                   "MaxScanRows=20\0");
```

請注意，資料來源實際上是一個目錄 (C:\EXCELDIR);此目錄必須存在。 Excel 驅動程式會使用目錄作為它的資料來源和檔案做為個別的資料表 （一個資料表，每個.xls 檔案）。

如需建立資料表的詳細資訊，請參閱 <<c0> [ 資料來源： 以程式設計方式建立 ODBC 資料來源中的資料表](../../data/odbc/data-source-programmatically-creating-a-table-in-an-odbc-data-source.md)。

下面資訊討論需要傳遞至參數`::SQLConfigDataSource`ODBC API 函式。 若要使用`::SQLConfigDataSource`，您必須包含 Odbcinst.h 標頭檔，並使用 Odbcinst.lib 匯入程式庫。 此外，Odbccp32.dll 必須在執行的階段 （或 16 位元的 Odbcinst.dll） 是在路徑中。

您可以建立使用 ODBC 管理員或類似的公用程式的 ODBC 資料來源名稱。 不過，有時候最好直接從您的應用程式取得的存取，而不需要使用者執行不同的公用程式中建立資料來源名稱。

ODBC 管理員 （通常安裝在控制台中） 會將項目放在 Windows 登錄中 （若是 16 位元，在 Odbc.ini 檔案） 建立新的資料來源。 ODBC 驅動程式管理員會查詢此檔，以取得有關資料來源的必要的資訊。 請務必知道哪些資訊必須放置在登錄中，因為您需要提供呼叫`::SQLConfigDataSource`。

雖然這項資訊可以直接寫入登錄而不需使用`::SQLConfigDataSource`，這麼做的任何應用程式信賴憑證者上的目前的技巧，驅動程式管理員用以維持其資料。 如果不同的方式保留資料來源的 ODBC 驅動程式管理員會實作記錄有較新版本，任何使用這項技術的應用程式將會中斷。 它是一般建議使用 API 函式，如果有提供。 比方說，您的程式碼可以從 16 位元移植至 32 位元如果您使用是`::SQLConfigDataSource`函式，因為函式正確寫入 Odbc.ini 檔案或登錄。

##  <a name="_core_sqlconfigdatasource_parameters"></a> SQLConfigDataSource 參數

下面將說明的參數`::SQLConfigDataSource`函式。 大部分的資訊取自 ODBC API*程式設計人員參考*提供 Visual c + + 1.5 版及更新版本。

###  <a name="_core_function_prototype"></a> 函式原型

```
BOOL SQLConfigDataSource(HWND hwndParent,UINT fRequest, LPCSTR lpszDriver, LPCSTR lpszAttributes);
```

### <a name="remarks"></a>備註

####  <a name="_core_parameters_and_usage"></a> 參數和使用方式

*hwndParent*<br/>
指定為擁有者的任何 ODBC 驅動程式管理員或特定的 ODBC 驅動程式會建立新的資料來源的相關使用者從取得其他資訊的對話方塊視窗。 如果*lpszAttributes*參數未提供足夠的資訊，會出現一個對話方塊。 *HwndParent*參數可能為 NULL。

*lpszDriver*<br/>
驅動程式說明。 這是呈現給使用者，而不是實體的驅動程式名稱 (DLL) 的名稱。

*lpszAttributes*<br/>
在表單中的屬性清單"keyname = value"。 這些字串是以與兩個連續的 null 結束字元，在清單結尾的 null 結束字元分隔。 這些屬性是主要預設驅動程式專屬的項目，其將會成為新的資料來源的登錄。 此函式的 ODBC API 參考中未提及的一個重要關鍵是"DSN"（「 資料來源名稱 」），這會指定新的資料來源的名稱。 其餘項目是新的資料來源的驅動程式特有的。 通常不需要提供所有的項目，因為驅動程式可以將新值的對話方塊使用者提示。 (設定*hwndParent*為 NULL，會造成這。)您可能想要明確地提供預設值，因此不會提示使用者。

#### <a name="to-determine-the-description-of-a-driver-for-the-lpszdriver-parameter-using-odbc-administrator"></a>若要決定使用 ODBC 管理員的 lpszDriver 參數驅動程式

1. 執行 ODBC 管理員。

1. 按一下 [加入] 。

這可讓您安裝的驅動程式及其描述的清單。 將這個說明當成*lpszDriver*參數。 請注意，您會使用整個說明，例如"Excel Files (*.xls)"，包括檔案名稱副檔名和括號，如果它們存在於描述。

或者，您可以檢查登錄 （若是 16 位元，Odbcinst.ini 檔案），其中包含一份驅動程式的所有項目和"ODBC Drivers"登錄機碼下的描述 （或在 Odbcinst.ini 中的 [ODBC 驅動程式] 區段）。

若要尋找的關鍵名稱和值單向*lpszAttributes*參數是要檢查已設定的資料來源 （可能是由 ODBC 管理員已設定） 的 Odbc.ini 檔案。

#### <a name="to-find-keynames-and-values-for-the-lpszattributes-parameter"></a>若要尋找 lpszAttributes 參數的關鍵名稱和值

1. 執行 Windows 登錄編輯程式 （或者，為 16 位元，請開啟 Odbc.ini 檔案）。

1. 尋找 ODBC 資料來源資訊使用下列其中一項：

   - 32 位元，尋找 金鑰**HKEY_CURRENT_USER\Software\ODBC\ODBC。Zdroje dat INI\ODBC**的左窗格中。

      右窗格會列出格式項目: 「 pub: REG_SZ:*<data source name>*"，其中*<data source name>* 是已設定您想要的驅動程式所需的設定與資料來源若要使用。 選取您想，資料來源，例如 SQL Server。 字串後的項目"pub:"都是，順序、 關鍵名稱和值將用於在您*lpszAttributes*參數。

   - 16 位元，找到一節所標記的 Odbc.ini 檔案中 [*\<資料來源名稱 >*]。

      下列這一行的行屬於表單"keyname = value"。 這些都是完全的項目中要用於您*lpszAttributes*參數。

您也可以檢查您要使用的特定驅動程式的文件。 您可以在驅動程式，您可以執行 ODBC 管理員來存取線上說明中找到有用的資訊。 這些說明檔是通常用來放置在 WINDOWS\SYSTEM 目錄中的 Windows NT、 Windows 3.1 或 Windows 95。

#### <a name="to-obtain-online-help-for-your-odbc-driver"></a>若要取得 ODBC 驅動程式的線上說明

1. 執行 ODBC 管理員。

1. 按一下 [加入] 。

1. 選取的驅動程式名稱。

1. 按一下 [確定 **Deploying Office Solutions**]。

當 ODBC 管理員顯示建立新的資料來源，該特定的驅動程式的資訊時，請按一下**協助**。 這會開啟該特定的驅動程式，通常包含了使用驅動程式的重要資訊的說明檔。

## <a name="see-also"></a>另請參閱

[資料來源 (ODBC)](../../data/odbc/data-source-odbc.md)
