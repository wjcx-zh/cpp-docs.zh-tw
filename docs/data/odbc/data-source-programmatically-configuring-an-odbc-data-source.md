---
title: "資料來源： 以程式設計方式設定 ODBC 資料來源 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SQLConfigDataSource
dev_langs: C++
helpviewer_keywords:
- ODBC data sources, configuring
- SQLConfigDataSource method example
- ODBC connections, configuring
- configuring ODBC data sources
ms.assetid: b8cabe9b-9e12-4d73-ae36-7cb12dee3213
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ac5756452a8b1c2d5dbf2f27ac7d3e1a8b069ca2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="data-source-programmatically-configuring-an-odbc-data-source"></a>資料來源：以程式設計方式設定 ODBC 資料來源
本主題說明如何以程式設計方式設定開放式資料庫連接 (ODBC) 資料來源名稱。 這可讓您彈性來存取資料而不未強制使用者明確使用 ODBC 管理員或其他程式來指定資料來源的名稱。  
  
 一般而言，使用者執行 ODBC 管理員，才能建立資料來源，如果相關聯的資料庫管理系統 (DBMS) 支援這項作業。  
  
 建立 Microsoft 存取 ODBC 資料來源透過 ODBC 管理員，當您有兩個選擇： 您可以選取現有的.mdb 檔案，或您可以建立新的.mdb 檔案。 沒有任何程式設計的方式建立的.mdb 檔案從 MFC ODBC 應用程式。 因此，如果您的應用程式需要將資料放入 Microsoft Access 資料來源 （.mdb 檔案），您很可能會想要有空白的.mdb 檔案，您可以使用或複製需要時。  
  
 不過，有許多 Dbms 允許以程式設計方式的資料來源建立。 某些資料來源會維護資料庫的目錄規格。 也就是目錄的資料來源，而且每個資料來源中的資料表儲存在個別的檔案 （若為 dBASE，每個資料表就是.dbf 檔案）。 其他的 ODBC 資料庫，例如 Microsoft Access 和 SQL Server 驅動程式需要在建立資料來源之前，無法滿足某個特定準則。 例如，當 SQL Server ODBC 驅動程式，您需要建立 SQL Server 電腦。  
  
##  <a name="_core_sqlconfigdatasource_example"></a>SQLConfigDataSource 範例  
 下列範例會使用**:: SQLConfigDataSource**呼叫新的 Excel 資料來源建立新的 Excel 資料來源的 ODBC API 函式：  
  
```  
SQLConfigDataSource(NULL,ODBC_ADD_DSN, "Excel Files (*.xls)",   
                   "DSN=New Excel Data Source\0"   
                   "Description=New Excel Data Source\0"   
                   "FileType=Excel\0"   
                   "DataDirectory=C:\\EXCELDIR\0"   
                   "MaxScanRows=20\0");  
```  
  
 請注意，資料來源是實際的目錄 (C:\EXCELDIR);此目錄必須存在。 Excel 驅動程式會使用當做其資料來源和檔案當做個別的資料表 （一個資料表，每個.xls 檔案） 目錄。  
  
 如需有關建立資料表的詳細資訊，請參閱[資料來源： 以程式設計方式建立 ODBC 資料來源中的資料表](../../data/odbc/data-source-programmatically-creating-a-table-in-an-odbc-data-source.md)。  
  
 下列資訊將討論所要傳遞至所需的參數**:: SQLConfigDataSource** ODBC API 函式。 若要使用**:: SQLConfigDataSource**，您必須包含 Odbcinst.h 標頭檔，並使用 Odbcinst.lib 匯入程式庫。 此外，Odbccp32.dll 必須在執行的階段 （或 Odbcinst.dll 的 16 位元） 是在路徑中。  
  
 您可以建立使用 ODBC 管理員或類似的公用程式的 ODBC 資料來源名稱。 不過，有時候很想要直接從您的應用程式，以取得存取權，而不需要使用者執行不同的公用程式中建立資料來源名稱。  
  
 ODBC （通常安裝於控制台） 的系統管理員會建立新的資料來源，方法是將項目放置在 Windows 登錄中 （或的 Odbc.ini 檔案中的 16 位元）。 ODBC 驅動程式管理員會查詢此檔案以取得有關資料來源的必要的資訊。 請務必知道哪些資訊必須放在登錄中，因為您需要提供呼叫**:: SQLConfigDataSource**。  
  
 雖然此資訊無法直接寫入登錄而不使用**:: SQLConfigDataSource**，這樣做的任何應用程式依賴驅動程式管理員會使用來維護其資料的目前技巧。 如果不同的方式保留資料來源的 ODBC 驅動程式管理員實作記錄有較新版本，任何使用這項技術的應用程式已中斷。 時，通常建議使用 API 函數時所提供。 比方說，您的程式碼時從 16 位元移植至 32 位元您使用**:: SQLConfigDataSource**函式，因為函式會正確地寫入至 Odbc.ini 檔案或登錄。  
  
##  <a name="_core_sqlconfigdatasource_parameters"></a>SQLConfigDataSource 參數  
 以下說明的參數**:: SQLConfigDataSource**函式。 大部分的資訊取自 ODBC API*程式設計人員參考*提供 Visual c + + 1.5 版及更新版本。  
  
###  <a name="_core_function_prototype"></a>函式原型  
  
```  
BOOL SQLConfigDataSource(HWND hwndParent,UINT fRequest, LPCSTR lpszDriver, LPCSTR lpszAttributes);  
```  
  
### <a name="remarks"></a>備註  
  
####  <a name="_core_parameters_and_usage"></a>參數和使用方式  
 *hwndParent*  
 指定為擁有者的任何 ODBC 驅動程式管理員或特定的 ODBC 驅動程式會建立新的資料來源的相關使用者從取得其他資訊的對話方塊視窗。 如果`lpszAttributes`參數沒有提供足夠的資訊，會出現一個對話方塊。 *HwndParent*參數可能為**NULL**。  
  
 `lpszDriver`  
 驅動程式的描述。 這是提供給使用者，而不是實體的驅動程式名稱 (DLL) 名稱。  
  
 `lpszAttributes`  
 中表單的屬性清單 」 keyname = 值 」。 這些字串分隔兩個連續的 null 結束字元，清單結尾的 null 結束字元。 這些屬性是主要預設驅動程式特定項目，請移到新的資料來源登錄。 ODBC API 參考，這個函式中未提及的一個重要金鑰是 「 DSN 」 （「 資料來源名稱 」），指定新的資料來源的名稱。 其餘的項目僅適用於新的資料來源的驅動程式。 通常不需要提供所有的項目，因為驅動程式可以提示使用者將新值的對話方塊。 (設定*hwndParent*至**NULL**會造成這。)您可以明確提供預設值，因此不會提示使用者。  
  
###### <a name="to-determine-the-description-of-a-driver-for-the-lpszdriver-parameter-using-odbc-administrator"></a>若要判斷驅動程式使用 ODBC 管理員 lpszDriver 參數的描述  
  
1.  執行 ODBC 系統管理員。  
  
2.  按一下 [加入] 。  
  
 這可讓您安裝的驅動程式及其描述的清單。 使用這項描述為`lpszDriver`參數。 請注意，您會使用整個描述，例如 「 Excel 檔案 (*.xls) 」，包括檔案的副檔名和括號，如果有的話描述中。  
  
 或者，您可以檢查登錄 （或 16 位元，Odbcinst.ini 檔案），其中包含驅動程式的所有項目和下登錄機碼 」 的 ODBC 驅動程式 」 的說明 （或在 Odbcinst.ini 中的區段 [ODBC 驅動程式]） 的清單。  
  
 其中一種方式來尋找 keynames 和值`lpszAttributes`參數是要檢查已設定的資料來源 （也許是一個由 ODBC 系統管理員已設定） 的 Odbc.ini 檔案。  
  
###### <a name="to-find-keynames-and-values-for-the-lpszattributes-parameter"></a>若要尋找 keynames 和 lpszAttributes 參數的值  
  
1.  執行 Windows 登錄編輯程式 （或者，16 位元，如開啟 Odbc.ini 檔案）。  
  
2.  尋找 ODBC 資料來源資訊使用下列其中一項：  
  
    -   32 位元，找到此金鑰**HKEY_CURRENT_USER\Software\ODBC\ODBC。INI\ODBC 資料來源**的左窗格中。  
  
         右窗格會列出的項目: 「 pub: REG_SZ:*<data source name>*"，其中 *<data source name>* 與您想要的驅動程式所需的設定已設定為資料來源若要使用。 選取您想，資料來源，例如 SQL Server。 下列字串的項目 」 pub:"都是，順序、 keyname 及值可以使用您`lpszAttributes`參數。  
  
    -   16 位元，找出區段，來標記的 Odbc.ini 檔案中 [*\<資料來源名稱 >*]。  
  
         下列這一行的行屬於表單"keyname = 值 」。 這些是完全使用中的項目您`lpszAttributes`參數。  
  
 您也可以檢查您要使用的特定驅動程式文件。 您可以在驅動程式，您可以藉由執行 ODBC 管理員來存取線上說明中找到有用的資訊。 這些檔案通常位於 WINDOWS\SYSTEM 目錄 Windows NT、 Windows 3.1 或 Windows 95。  
  
###### <a name="to-obtain-online-help-for-your-odbc-driver"></a>若要取得的 ODBC 驅動程式的線上說明  
  
1.  執行 ODBC 系統管理員。  
  
2.  按一下 [加入] 。  
  
3.  選取的驅動程式名稱。  
  
4.  按一下 [確定 **Deploying Office Solutions**]。  
  
 當 ODBC 管理員顯示建立新的資料來源，該特定驅動程式的資訊時，請按一下**協助**。 這會開啟該特定的驅動程式，通常包含有關使用驅動程式的重要資訊的說明檔。  
  
## <a name="see-also"></a>請參閱  
 [資料來源 (ODBC)](../../data/odbc/data-source-odbc.md)