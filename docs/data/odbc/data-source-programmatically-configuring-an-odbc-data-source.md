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
ms.openlocfilehash: ba0224d166795b34d636ace610265e115209e49c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358865"
---
# <a name="data-source-programmatically-configuring-an-odbc-data-source"></a>資料來源：以程式設計方式設定 ODBC 資料來源

本主題介紹如何以程式設計方式配置開放資料庫連接 (ODBC) 資料來源名稱。 這樣,您可以靈活地訪問數據,而無需強制用戶顯式使用 ODBC 管理員或其他程式來指定數據源的名稱。

通常,如果關聯的資料庫管理系統 (DBMS) 支援此操作,則使用者運行 ODBC 管理員以創建數據來源。

以 ODBC 管理員創建 Microsoft 存取 ODBC 資料來源時,您有兩種選擇:您可以選擇現有的 .mdb 檔案,也可以創建新的 .mdb 檔。 沒有從 MFC ODBC 應用程式建立 .mdb 檔的程式設計方法。 因此,如果應用程式要求將數據放入 Microsoft Access 資料來源 (.mdb 檔),則很可能希望有一個空的 .mdb 檔,您可以隨時使用或複製該檔。

但是,許多 DBMS 允許創建程式設計數據來源。 某些數據源維護資料庫的目錄規範。 也就是說,目錄是數據源,數據源中的每個表都存儲在單獨的檔中(在 dBASE 中,每個表都是 .dbf 檔)。 其他 ODBC 資料庫(如 Microsoft Access 和 SQL Server)的驅動程式要求在建立數據來源之前滿足某些特定條件。 例如,使用 SQL Server ODBC 驅動程式時,需要建立 SQL Server 電腦。

## <a name="sqlconfigdatasource-example"></a><a name="_core_sqlconfigdatasource_example"></a>SQLConfigData來源範例

以下範例使用`::SQLConfigDataSource`ODBC API 函數建立新的 Excel 資料來源,稱為新 Excel 資料來源:

```
SQLConfigDataSource(NULL,ODBC_ADD_DSN, "Excel Files (*.xls)",
                   "DSN=New Excel Data Source\0"
                   "Description=New Excel Data Source\0"
                   "FileType=Excel\0"
                   "DataDirectory=C:\\EXCELDIR\0"
                   "MaxScanRows=20\0");
```

請注意,數據源實際上是一個目錄 (C:_EXCELDIR);此目錄必須存在。 Excel 驅動程式使用目錄作為其資料來源,並將檔案用作單個表(每個 .xls 檔一個表)。

有關建立表的詳細資訊,請參考[資料來源:在 ODBC 資料來源中以編程方式建立表](../../data/odbc/data-source-programmatically-creating-a-table-in-an-odbc-data-source.md)。

以下資訊討論了需要傳遞給 ODBC API`::SQLConfigDataSource`函數的 參數。 要使用`::SQLConfigDataSource`,必須包括 Odbcinst.h 標頭檔並使用 Odbcinst.lib 匯入庫。 此外,Odbccp32.dll 必須在運行時的路徑中(或 Odbcinst.dll 為 16 位元)。

您可以使用 ODBC 管理員或類似實用程式創建 ODBC 資料來源名稱。 但是,有時最好直接從應用程式創建數據源名稱以獲取訪問許可權,而無需使用者運行單獨的實用程式。

ODBC 管理員(通常安裝在控制面板中)通過將條目放入 Windows 註冊表(或對於 16 位)中的 Odbc.ini 檔中來創建新的數據來源。 ODBC 驅動程式管理員查詢此檔以獲取有關數據來源所需的資訊。 請務必瞭解需要將哪些資訊放置在註冊表中,因為您需要向 它提供呼`::SQLConfigDataSource`叫 。

儘管此資訊可以直接寫入註冊表而不使用`::SQLConfigDataSource`,但這樣做的任何應用程式都依賴於驅動程式管理器用於維護其數據的當前技術。 如果更高版本的 ODBC 驅動程式管理器以不同的方式實現有關數據源的記錄保存,則使用此技術的任何應用程式都將中斷。 通常建議在提供 API 函數時使用 API 函數。 例如,如果使用`::SQLConfigDataSource`函數,代碼從 16 位元可移植到 32 位元,因為函數正確寫入 Odbc.ini 檔或註冊表。

## <a name="sqlconfigdatasource-parameters"></a><a name="_core_sqlconfigdatasource_parameters"></a>SQLConfigData源參數

下面介紹了`::SQLConfigDataSource`函數的參數。 大部分資訊來自 VisualC++ 版本 1.5 及更高版本中提供的 ODBC API*程式師參考*。

### <a name="function-prototype"></a><a name="_core_function_prototype"></a>功能原型

```
BOOL SQLConfigDataSource(HWND hwndParent,UINT fRequest, LPCSTR lpszDriver, LPCSTR lpszAttributes);
```

### <a name="remarks"></a>備註

#### <a name="parameters-and-usage"></a><a name="_core_parameters_and_usage"></a>參數和用法

*hwnd 家長*<br/>
指定為 ODBC 驅動程式管理器或特定 ODBC 驅動程式創建的任何對話方塊的所有者的視窗,以便從使用者處獲取有關新資料來源的其他資訊。 如果*lpszAttributes*參數未提供足夠的資訊,則會出現一個對話方塊。 *hwnd 父參數*可能為 NULL。

*lpszDriver*<br/>
驅動程序說明。 這是向使用者顯示的名稱,而不是物理驅動程式名稱 (DLL)。

*lpsz屬性*<br/>
表單中的屬性清單 keyname_value。 這些字串由空終止符分隔,在清單末尾有兩個連續的空終止符。 這些屬性主要是預設的特定於驅動程式的條目,這些條目進入新數據源的註冊表。 此函數的 ODBC API 引用中未提及的一個重要鍵是"DSN"(「數據源名稱」),它指定新資料源的名稱。 其餘條目特定於新數據源的驅動程式。 通常不需要提供所有條目,因為驅動程式可以提示使用者為新值的對話方塊。 (將 *「父級設置為 NULL」* 會導致這種情況。您可能希望顯式提供預設值,以便不會提示使用者。

#### <a name="to-determine-the-description-of-a-driver-for-the-lpszdriver-parameter-using-odbc-administrator"></a>使用 ODBC 管理員確定 lpszDriver 參數的驅動程式描述

1. 運行ODBC管理員。

1. 按一下 **[新增]**。

這為您提供了已安裝驅動程式的清單及其說明。 使用此說明作為*lpszDriver*參數。 請注意,您可以使用整個說明,例如"Excel 檔 (*.xls)"),包括檔名副檔名和括弧(如果它們存在於說明中)。

作為替代方法,您可以檢查註冊表(或,對於 16 位元,檔 Odbcinst.ini),其中包含註冊表鍵"ODBC 驅動程式"(或 Odbcinst.ini 中的部分 [ODBC 驅動程式]下的所有驅動程式條目和說明的清單)。

尋找*lpszAttributes*參數的鍵名稱和值的一種方法是檢查已設定的資料來源(可能是由 ODBC 管理員配置的數據來源)的 Odbc.ini 檔。

#### <a name="to-find-keynames-and-values-for-the-lpszattributes-parameter"></a>尋找 lpszAttributes 參數的鍵名稱和值

1. 執行 Windows 註冊表編輯器(或者,對於 16 位元,打開 Odbc.ini 檔案)。

1. 使用以下的一尋找 ODBC 資料來源資訊:

   - 對於 32 位元,找到**HKEY_CURRENT_USER\軟體_ODBC_ODBC 的關鍵。左邊窗格中的 INI_ODBC資料來源**。

      右側窗格列出了窗體的條目:「pub:REG_SZ:*\<資料源名稱>」,* 其中*\<資料源名稱>* 已配置了要使用的驅動程式所需的設置。 選擇所需的資料來源,例如 SQL Server。 字串"pub:「之後的項按順序排列,是要在*lpszAttributes*參數中使用的鍵名和值。

   - 對於 16 位元,在 Odbc.ini 檔中找到該部分,該檔由 [*\<資料源名稱>*] 標記。

      此行的行是"keyname_value"窗體。 這些正是要在*lpszAttributes*參數中使用的條目。

您可能還需要檢查要使用的特定驅動程式的文檔。 您可以在驅動程式的線上説明中找到有用的資訊,您可以通過運行 ODBC 管理員來訪問這些資訊。 這些説明檔通常放置在 Windows NT、Windows 3.1 或 Windows 95 的 WINDOWS_SYSTEM 目錄中。

#### <a name="to-obtain-online-help-for-your-odbc-driver"></a>取得 ODBC 驅動程式的線上說明

1. 運行ODBC管理員。

1. 按一下 **[新增]**。

1. 選擇驅動程式名稱。

1. 按一下 [確定]  。

當 ODBC 管理員顯示為該特定驅動程式創建新資料來源的資訊時,按下「**説明**」。。 這將打開該特定驅動程式的幫助檔,該檔通常包含有關驅動程式使用的重要資訊。

## <a name="see-also"></a>另請參閱

[資料來源](../../data/odbc/data-source-odbc.md)
