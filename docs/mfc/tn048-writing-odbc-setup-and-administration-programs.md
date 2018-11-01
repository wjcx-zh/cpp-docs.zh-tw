---
title: TN048：撰寫 MFC 資料庫應用程式的 ODBC 安裝和管理程式
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.odbc
helpviewer_keywords:
- installing ODBC
- ODBC, installing
- setup, ODBC setup programs
- TN048
- ODBC, and MFC
- MFC, database applications
ms.assetid: d456cdd4-0513-4a51-80c0-9132b66115ce
ms.openlocfilehash: b31ceb8bfc48decb5387d386ee8e8b64822f72ed
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584118"
---
# <a name="tn048-writing-odbc-setup-and-administration-programs-for-mfc-database-applications"></a>TN048：撰寫 MFC 資料庫應用程式的 ODBC 安裝和管理程式

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

使用 MFC 資料庫類別應用程式必須安裝 ODBC 元件的安裝程式。 他們也可能需要將擷取可用的驅動程式，來指定預設驅動程式，以及設定資料來源的相關資訊的 ODBC 管理程式。 此提示描述使用 ODBC 安裝程式 API，來撰寫這些程式。

##  <a name="_mfcnotes_writing_an_odbc_setup_program"></a> 撰寫 ODBC 安裝程式

MFC 資料庫應用程式需要 ODBC 驅動程式管理員連接 (ODBC。DLL) 和能夠以前往 資料來源的 ODBC 驅動程式。 許多 ODBC 驅動程式也需要額外的網路及通訊 Dll。 大部分的 ODBC 驅動程式隨附於安裝程式，將會安裝必要的 ODBC 元件。 使用 MFC 資料庫類別的應用程式開發人員可以：

- 依賴特定驅動程式安裝程式安裝 ODBC 元件。 這項作業需要任何進一步的開發人員的組件上的工作，您就可以重新發佈的驅動程式安裝程式。

- 或者，您可以撰寫您自己的安裝程式，將會安裝驅動程式管理員和驅動程式。

ODBC 安裝程式 API 可用來撰寫應用程式特定的安裝程式。 安裝程式 API 中的函式由 ODBC 安裝程式 DLL — ODBCINST。16 位元 Windows 和 ODBCCP32 DLL。在 Win32 DLL。 應用程式可以呼叫`SQLInstallODBC`在安裝程式 DLL，如此便會安裝 ODBC 驅動程式管理員、 ODBC 驅動程式，以及任何所需轉譯器。 它接著會記錄已安裝的驅動程式和轉譯器中 ODBCINST。INI 檔案 （或登錄，NT 上的）。 `SQLInstallODBC` 需要 ODBC 的完整路徑。INF 檔案，其中包含要安裝的驅動程式清單，並描述構成每個驅動程式的檔案。 它也會包含驅動程式管理員和轉譯器的類似資訊。 ODBC。INF 檔案通常是由驅動程式開發人員提供。

程式也可以安裝個別的 ODBC 元件。 若要安裝驅動程式管理員，程式會先呼叫`SQLInstallDriverManager`安裝程式 DLL，以取得驅動程式管理員的目標目錄中。 這通常是 Windows Dll 所在的目錄。 程式接著會使用 ODBC 的 [ODBC 驅動程式管理員] 區段中的資訊。若要將驅動程式管理員和相關的檔案從安裝光碟複製到這個目錄的 INF 檔案。 若要安裝個別的驅動程式，程式會先呼叫`SQLInstallDriver`安裝程式將驅動程式規格 ODBCINST 至 DLL 中。INI 檔案 （或登錄，NT 上的）。 `SQLInstallDriver` 傳回驅動程式的目標目錄 — 通常是 Windows Dll 所在的目錄。 程式接著會使用 ODBC 驅動程式的一節中的資訊。若要將驅動程式 DLL 和相關的檔案從安裝光碟複製到這個目錄的 INF 檔案。

如需有關 ODBC 的詳細資訊。INF，ODBCINST。INI 及使用安裝程式 API，請參閱 ODBC SDK*程式設計人員參考*第 19 章，安裝 ODBC 軟體。

##  <a name="_mfcnotes_writing_an_odbc_administrator"></a> 撰寫 ODBC 管理員

MFC 資料庫應用程式可以安裝及設定 ODBC 資料來源中有兩種，，，如下所示：

- 使用 ODBC 管理員 （可當做程式或控制台項目）。

- 建立您自己的程式來設定資料來源。

設定資料來源的程式會安裝程式 DLL 函式呼叫。 安裝程式 DLL 呼叫安裝程式來設定資料來源的 DLL。 沒有每個驅動程式; 一個安裝程式 DLL可能是驅動程式 DLL 本身或不同的 DLL。 安裝程式 DLL 會提示使用者輸入的驅動程式必須連接到資料來源和預設轉譯器，如果支援的資訊。 然後它會呼叫安裝程式 DLL 與 Windows Api 的 odbc 記錄這項資訊。INI 檔案 （或登錄）。

若要顯示的對話方塊中，使用者可以新增、 修改及刪除資料來源，程式會呼叫`SQLManageDataSources`安裝程式 DLL 中。 安裝程式 DLL 呼叫控制項台中時，會叫用此函式。 若要新增、 修改或刪除資料來源時，`SQLManageDataSources`呼叫`ConfigDSN`與該資料來源相關聯的驅動程式安裝程式的 DLL 中。 若要直接新增、 修改或刪除資料來源，程式會呼叫`SQLConfigDataSource`安裝程式 DLL 中。 程式會將傳遞資料來源，這個選項可指定要採取的動作的名稱。 `SQLConfigDataSource` 呼叫`ConfigDSN`中安裝 DLL 並將它傳遞的引數從`SQLConfigDataSource`。

如需詳細資訊，請參閱 ODBC SDK*程式設計人員參考*第 23 章，安裝程式 DLL 函式參考，第 24 章安裝程式 DLL 函式參考。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)

