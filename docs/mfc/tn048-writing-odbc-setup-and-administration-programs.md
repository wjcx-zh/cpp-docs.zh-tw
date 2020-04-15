---
title: TN048：撰寫 MFC 資料庫應用程式的 ODBC 安裝和管理程式
ms.date: 11/04/2016
helpviewer_keywords:
- installing ODBC
- ODBC, installing
- setup, ODBC setup programs
- TN048
- ODBC, and MFC
- MFC, database applications
ms.assetid: d456cdd4-0513-4a51-80c0-9132b66115ce
ms.openlocfilehash: d25520c4ffc805701dfe6b51192f8078e2fa300f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365474"
---
# <a name="tn048-writing-odbc-setup-and-administration-programs-for-mfc-database-applications"></a>TN048：撰寫 MFC 資料庫應用程式的 ODBC 安裝和管理程式

> [!NOTE]
> 下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

使用 MFC 資料庫類別將需要安裝 ODBC 元件的安裝程式。 他們可能需要一個 ODBC 管理程式,它將檢索有關可用驅動程式的資訊,指定預設驅動程式和配置數據來源。 本說明介紹了使用 ODBC 安裝程式 API 編寫這些程式。

## <a name="writing-an-odbc-setup-program"></a><a name="_mfcnotes_writing_an_odbc_setup_program"></a>編寫 ODBC 安裝程式

MFC 資料庫應用程式需要 ODBC 驅動程式管理員 (ODBC)。DLL) 和 ODBC 驅動程式能夠存取資料來源。 許多 ODBC 驅動程式還需要額外的網路和通信 DLL。 大多數 ODBC 驅動程式附帶一個安裝程式,將安裝所需的 ODBC 元件。 使用 MFC 資料庫類別的應用程式開發人員可以:

- 使用特定於驅動程式的安裝程式來安裝 ODBC 元件。 這將不需要開發人員的進一步工作 - 您可以重新分發驅動程式的安裝程式。

- 或者,您可以編寫自己的安裝程式,這將安裝驅動程式管理器和驅動程式。

ODBC 安裝程式 API 可用於編寫特定於應用程式的安裝程式。 安裝程式 API 中的函數由 ODBC 安裝程式 DLL 和 ODBCINST 實現。16 位元 Windows 和 ODBCCP32 上的 DLL。DLL 上 Win32。 應用程式可以呼叫`SQLInstallODBC`安裝程式 DLL,它將安裝 ODBC 驅動程式管理員、ODBC 驅動程式和任何必需的轉換器。 然後,它會在 ODBCINST 中記錄已安裝的驅動程式和譯師。INI 檔案(或註冊表,在NT上)。 `SQLInstallODBC`需要到 ODBC 的完整路徑。INF 檔,其中包含要安裝的驅動程式清單,並描述構成每個驅動程式的檔。 它還包含有關驅動程式管理員和譯員的類似資訊。 Odbc。INF 檔案通常由驅動程式開發人員提供。

程式還可以安裝單個 ODBC 元件。 要安裝驅動程式管理員,程式首先在安裝程式`SQLInstallDriverManager`DLL 中調用以獲取驅動程式管理器的目標目錄。 這通常是 Windows DLL 所在的目錄。 然後,程式使用 ODBC [ODBC 驅動程式管理員] 部分中的資訊。INF 檔案將驅動程式管理員和相關檔案從安裝磁碟複製到此目錄。 要安裝單個驅動程式,程式首先調用`SQLInstallDriver`安裝程式 DLL 中,將驅動程式規範添加到 ODBCINST。INI 檔案(或註冊表,在NT上)。 `SQLInstallDriver`傳回驅動程式的目標目錄 ─通常是 Windows DLL 所在的目錄。 然後,程式使用ODBC驅動程式部分中的資訊。INF 檔案將驅動程式 DLL 和相關檔案從安裝磁碟複製到此目錄。

有關ODBC的更多資訊。INF,藥點。INI 和使用安裝程式 API,請參閱 ODBC SDK*程式師參考,* 第 19 章,安裝 ODBC 軟體。

## <a name="writing-an-odbc-administrator"></a><a name="_mfcnotes_writing_an_odbc_administrator"></a>編寫 ODBC 管理員

MFC 資料庫應用程式可以透過以下兩種方式之一設定和設定 ODBC 資料來源:

- 使用 ODBC 管理員(作為程式或控制面板專案提供)。

- 建立您自己的程式來配置資料來源。

設定數據源的程式對安裝程式 DLL 進行函數調用。 安裝程式 DLL 呼叫安裝程式 DLL 來設定資料來源。 每個驅動程式有一個設置 DLL;它可能是驅動程式 DLL 本身,或單獨的 DLL。 安裝程式 DLL 會提示使用者獲取驅動程式需要連接到資料源和預設轉換器(如果受支援)的資訊。 然後,它調用安裝程式 DLL 和 Windows API 以在 ODBC 中記錄此資訊。INI 檔(或註冊表)。

要顯示使用者以您對話盒新增、修改與移除資料來源,安裝程式 DLL 中的程式`SQLManageDataSources`呼叫 。 當從控制面板調用安裝程式 DLL 時,將調用此功能。 要新增、修改或刪除資料來源,`SQLManageDataSources``ConfigDSN`請呼叫與該資料來源關聯的驅動程式的安裝程式 DLL。 要直接添加、修改或刪除資料源,安裝程式 DLL`SQLConfigDataSource`中的程式呼叫。 程序傳遞數據來源的名稱和指定要執行的操作的選項。 `SQLConfigDataSource`在`ConfigDSN`設定 DLL 中呼叫,並從`SQLConfigDataSource`傳遞參數 。

有關詳細資訊,請參閱 ODBC SDK*程式師的參考、* 第 23 章、設置 DLL 函數參考和第 24 章安裝程式 DLL 函數參考。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
