---
title: "資料來源：以程式設計方式設定 ODBC 資料來源 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SQLConfigDataSource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "設定 ODBC 資料來源"
  - "ODBC 連接, 設定"
  - "ODBC 資料來源, 設定"
  - "SQLConfigDataSource 方法範例"
ms.assetid: b8cabe9b-9e12-4d73-ae36-7cb12dee3213
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 資料來源：以程式設計方式設定 ODBC 資料來源
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個主題會說明如何以程式設計方式設定開放式資料庫連接 \(ODBC\) 資料來源名稱。  這個功能將提供您無須強制使用者明確使用 ODBC 管理員 \(ODBC 管理員\) 或其他程式以指定資料來源名稱，就可存取資料的彈性。  
  
 通常，使用者會在相關的資料庫管理系統 \(DBMS\) 支援這個作業的情況下，執行 ODBC 管理員來建立資料來源。  
  
 您在透過 ODBC 管理員建立 Microsoft Access ODBC 資料來源時，會有兩種選擇：您可以選取現有的 .mdb 檔，或建立新的 .mdb 檔。  您無法以程式設計方式建立 MFC ODBC 應用程式的 .mdb 檔。  因此，如果應用程式需要您將資料放置在 Microsoft Access 資料來源 \(.mdb 檔\)，您可能會很想擁有可以在任何需要情況下使用或複製的空白 .mdb 檔。  
  
 但是有許多 DBMS 允許以程式設計方式建立資料來源。  某些資料來源會為資料庫維護一個目錄規格。  也就是說，目錄便是資料來源，而資料來源中的每個資料表則儲存為個別的檔案 \(若為 dBASE，每個資料表就是一個 .dbf 檔\)。  其他 ODBC 資料庫適用的驅動程式，例如 Microsoft Access 和 SQL Server，則需要在建立資料來源之前先滿足某些特定條件。  例如，您必須在使用 SQL Server ODBC 驅動程式之前，就先建立 SQL Server 電腦。  
  
##  <a name="_core_sqlconfigdatasource_example"></a> SQLConfigDataSource 範例  
 下列範例會使用 **::SQLConfigDataSource** ODBC API 函式，建立名為 New Excel Data Source 的新 Excel 資料來源：  
  
```  
SQLConfigDataSource(NULL,ODBC_ADD_DSN, "Excel Files (*.xls)",   
                   "DSN=New Excel Data Source\0"   
                   "Description=New Excel Data Source\0"   
                   "FileType=Excel\0"   
                   "DataDirectory=C:\\EXCELDIR\0"   
                   "MaxScanRows=20\0");  
```  
  
 請注意，該資料來源實際上是一個目錄 \(C:\\EXCELDIR\)；因此必須存在這個目錄。  Excel 驅動程式會把目錄當成資料來源，並且將檔案當成個別資料表來使用 \(每個 .xls 檔為一個資料表\)。  
  
 如需建立資料表的詳細資訊，請參閱[資料來源：以程式設計方式建立 ODBC 資料來源資料表](../../data/odbc/data-source-programmatically-creating-a-table-in-an-odbc-data-source.md)。  
  
 下面資訊討論需要傳遞至 **::SQLConfigDataSource** ODBC API 函式的參數。  若要使用 **::SQLConfigDataSource**，您必須包含 Odbcinst.h 標頭檔 \(Header File\)，並使用 Odbcinst.lib 匯入程式庫。  在執行階段，Odbccp32.dll \(或 16 位元的 Odbcinst.dll\) 也必須在路徑中。  
  
 您可以使用 ODBC 管理員或類似的公用程式，建立 ODBC 資料來源名稱。  但是有時為了取得存取權限，您最好直接從應用程式建立一個資料來源，而不需讓使用者執行一個單獨的公用程式。  
  
 ODBC 管理員 \(通常安裝在 \[控制台\]\) 藉由在 Windows 登錄 \(若為 16 位元，則在 Odbc.ini 檔案中\) 放置項目來建立新的資料來源。  ODBC 驅動程式管理員會查詢這個檔案來取得資料來源的必要資訊。  知道登錄內需放置何種資訊是非常重要的，因為您需要在對 **::SQLConfigDataSource** 呼叫時提供這份資訊。  
  
 儘管這份資訊可以不經 **::SQLConfigDataSource** 就直接寫入登錄，但任何如此處理的應用程式仍需使用目前驅動程式管理員用以維持其資料的技術。  如果有較新版本的 ODBC 驅動程式管理員，使用不同的方式實作保留資料來源的資料錄，則任何使用這項技術的應用程式都會中斷。  如果有提供較新版本，通常會建議使用一個 API 函式的做法。  例如，如果您使用 **::SQLConfigDataSource** 函式，程式碼就可以從 16 位元移植成 32 位元程式碼，因為該函式正確寫入 Odbc.ini 檔案或登錄。  
  
##  <a name="_core_sqlconfigdatasource_parameters"></a> SQLConfigDataSource 參數  
 下面將說明 **::SQLConfigDataSource** 函式的參數。  如需詳細資訊，請參閱 1.5 版和更新版本的 Visual C\+\+ 所提供的《ODBC API 程式設計人員參考》。  
  
###  <a name="_core_function_prototype"></a> 函式原型  
  
```  
BOOL SQLConfigDataSource(HWND hwndParent,UINT fRequest, LPCSTR lpszDriver, LPCSTR lpszAttributes);  
```  
  
### 備註  
  
####  <a name="_core_parameters_and_usage"></a> 參數和用法  
 *hwndParent*  
 此視窗會被指定成任何由 ODBC 驅動程式管理員或特定 ODBC 驅動程式所建，用來從使用者取得其他新資料來源的相關資訊之對話方塊。  如果 `lpszAttributes` 參數未提供足夠資訊，將會出現一個對話方塊。  *hwndParent* 參數可能是 **NULL**。  
  
 `lpszDriver`  
 驅動程式說明。  這是呈現給使用者的名稱，而非實體的驅動程式名稱 \(即 DLL\)。  
  
 `lpszAttributes`  
 以 "keyname\=value" 格式表示的屬性清單。  這些字串會 null 結束字元分隔，在清單結尾會以連續兩個 null 結束字元表示。  這些屬性主要是預設的驅動程式特定項目，其將會成為新資料來源的登錄資料。  ODBC API 參考函式有一個尚未提及的重要關鍵，即可以指定新資料來源名稱的 "DSN" \(即，資料來源名稱\)。  項目的其他部分則專屬於新資料來源的驅動程式。  由於驅動程式會在對話方塊向使用者要求新值，因此通常並不需要提供所有的項目 \(將 *hwndParent* 設為 **NULL** 即可完成\)。您可以明確地提供預設值，如此一來，使用者就不會收到這種提示。  
  
###### 若要決定使用 ODBC 管理員的 lpszDriver 參數驅動程式的說明  
  
1.  執行 ODBC 管理員。  
  
2.  按一下 \[**加入**\]。  
  
 您會取得已安裝的驅動程式清單和驅動程式的說明。  將這個說明當成 `lpszDriver` 參數使用。  請注意，您需要使用整個說明，例如 "Excel Files \(\*.xls\)"，其中包括了副檔名和可能出現在說明中的括弧。  
  
 另一種做法是，您可以檢查登錄 \(若為 16 位元，則是在 Odbcinst.ini 檔案中\)，其中包含所有驅動程式項目的清單，和 "ODBC Drivers" 登錄機碼 \(Registry Key\) 下的說明 \(或是 Odbcinst.ini 檔案中的 \[ODBC 驅動程式\] 區段\)。  
  
 尋找 `lpszAttributes` 參數的關鍵名稱和值的一種方式，是檢查已完成設定的資料來源 \(可能是由 ODBC 管理員所設定\) 的 Odbc.ini 檔案：  
  
###### 若要尋找 lpszAttributes 參數的關鍵名稱和值  
  
1.  執行 Windows 登錄編輯程式 \(若是 16 位元，請開啟 Odbc.ini 檔案\)。  
  
2.  使用下列任一方式尋找 ODBC 資料來源資訊：  
  
    -   若是 32 位元，請尋找左窗格中的 **HKEY\_CURRENT\_USER\\Software\\ODBC\\ODBC.INI\\ODBC Data Sources** 機碼。  
  
         右窗格則列出形式項目：pub: REG\_SZ:*\<資料來源名稱\>*，其中 *\<資料來源名稱\>* 是一個以您希望使用的驅動程式之所需設定完成設定的資料來源。  選取您希望使用的資料來源，例如 SQL Server。  接在 pub: 字串後的項目依照順序是，關鍵名稱和用在您的 `lpszAttributes` 參數中的值。  
  
    -   若是 16 位元，請在 Odbc.ini 檔案中尋找由 \[*\<資料來源名稱\>*\] 所標記的區段。  
  
         跟隨在這行之後的行，格式是 "keyname\=value"。  這些是實際上將用於您的 `lpszAttributes` 參數中的項目。  
  
 您可能也需要查閱您將使用的特定驅動程式文件。  線上說明中可以找到驅動程式的有用資訊，只要執行 ODBC 管理員即可存取此線上說明。  這些說明檔案在 Windows NT、Windows 3.1 或 Windows 95 上通常是放置在 WINDOWS\\SYSTEM 目錄中。  
  
###### 若要取得 ODBC 驅動程式的線上說明  
  
1.  執行 ODBC 管理員。  
  
2.  按一下 \[**加入**\]。  
  
3.  選取驅動程式名稱。  
  
4.  按一下 \[**確定**\]。  
  
 請在 ODBC 管理員為建立一個新的資料來源而顯示該特定驅動程式資訊時，按一下 \[說明\]。  如此會開啟特定驅動程式的說明檔案，內容通常包含了使用驅動程式的重要資訊。  
  
## 請參閱  
 [資料來源 \(ODBC\)](../../data/odbc/data-source-odbc.md)