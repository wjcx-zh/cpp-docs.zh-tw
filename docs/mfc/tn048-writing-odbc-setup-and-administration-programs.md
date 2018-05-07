---
title: TN048： 撰寫 MFC 資料庫應用程式的 ODBC 安裝和管理程式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.odbc
dev_langs:
- C++
helpviewer_keywords:
- installing ODBC
- ODBC, installing
- setup, ODBC setup programs
- TN048
- ODBC, and MFC
- MFC, database applications
ms.assetid: d456cdd4-0513-4a51-80c0-9132b66115ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c08366f995c1ecb4182fff04a88ac37fe7334bc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="tn048-writing-odbc-setup-and-administration-programs-for-mfc-database-applications"></a>TN048：撰寫 MFC 資料庫應用程式的 ODBC 安裝和管理程式
> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 使用 MFC 資料庫類別應用程式需要安裝 ODBC 元件的安裝程式。 它們也可能需要 ODBC 管理程式中，將會擷取可用的驅動程式，來指定預設驅動程式，以及設定資料來源的相關資訊。 此提示描述使用 ODBC 安裝程式 API，來撰寫這些程式。  
  
##  <a name="_mfcnotes_writing_an_odbc_setup_program"></a> 寫入的 ODBC 安裝程式  
 MFC 資料庫應用程式需要的 ODBC 驅動程式管理員連接 (ODBC。DLL)，若要能夠取得資料來源的 ODBC 驅動程式。 許多 ODBC 驅動程式也需要額外的網路及通訊 Dll。 大部分的 ODBC 驅動程式隨附於安裝程式，將會安裝必要的 ODBC 元件。 使用 MFC 資料庫類別應用程式開發人員可以：  
  
-   依賴 ODBC 元件安裝的特定驅動程式安裝程式。 這需要進行任何開發人員的組件上的工作，您就可以重新發佈的驅動程式安裝程式。  
  
-   或者，您可以撰寫您自己的安裝程式，將會安裝驅動程式管理員和驅動程式。  
  
 ODBC 安裝程式 API 可以用來寫入特定應用程式安裝程式。 安裝程式的應用程式開發介面中的函式由 ODBC 安裝程式的 DLL — ODBCINST。在 16 位元的視窗和 ODBCCP32 DLL。在 Win32 DLL。 應用程式可以呼叫**SQLInstallODBC**在安裝程式將會安裝 ODBC 驅動程式管理員、 ODBC 驅動程式，以及任何的 DLL 所需轉譯器。 它然後安裝的驅動程式和轉譯器中記錄 ODBCINST。INI 檔案 （或登錄中的 nt）。 **SQLInstallODBC**需要 ODBC 的完整路徑。INF 檔案，其中包含要安裝的驅動程式清單，描述構成每個驅動程式的檔案。 它也包含驅動程式管理員和轉譯器的類似資訊。 ODBC。驅動程式開發人員通常會提供的 INF 檔案。  
  
 程式也可以安裝個別的 ODBC 元件。 若要安裝驅動程式管理員，程式會先呼叫**SQLInstallDriverManager**安裝程式的 DLL，以便取得驅動程式管理員的目標目錄中。 這通常是位於 Windows Dll 的目錄。 接著程式會使用 ODBC 的 [ODBC 驅動程式管理員] 區段中的資訊。若要從安裝光碟的驅動程式管理員和相關的檔案複製到這個目錄的 INF 檔案。 若要安裝個別的驅動程式，程式會先呼叫**SQLInstallDriver**安裝程式將驅動程式規格 ODBCINST DLL 中。INI 檔案 （或登錄中的 nt）。 **SQLInstallDriver**傳回驅動程式的目標目錄，通常位於 Windows Dll 的目錄。 接著程式會使用 ODBC 驅動程式的一節中的資訊。若要從安裝光碟的驅動程式 DLL 和相關的檔案複製到這個目錄的 INF 檔案。  
  
 如需有關 ODBC 的詳細資訊。INF，ODBCINST。INI 及使用安裝程式 API，請參閱 ODBC SDK*程式設計人員參考*第 19 章、 安裝 ODBC 軟體。  
  
##  <a name="_mfcnotes_writing_an_odbc_administrator"></a> 撰寫 ODBC 管理員  
 MFC 資料庫應用程式可以安裝及設定 ODBC 資料來源中有兩種，，，如下所示：  
  
-   使用 ODBC 管理員 （使用程式為或控制台項目）。  
  
-   建立您自己的程式，設定資料來源。  
  
 設定資料來源的程式會安裝程式的 DLL 函式呼叫。 安裝程式的 DLL 呼叫的 DLL，以便設定資料來源的安裝。 沒有一個安裝 DLL，每個驅動程式。它可能是驅動程式 DLL 本身或個別的 DLL。 安裝程式 DLL 會提示使用者輸入的驅動程式必須連接到資料來源和預設轉譯程式中，如果支援的資訊。 DLL 和 Windows 應用程式開發介面，在 ODBC 中記錄這項資訊然後呼叫安裝程式。INI 檔案 （或登錄）。  
  
 若要顯示的使用者可以新增、 修改和刪除資料來源 對話方塊，程式會呼叫**SQLManageDataSources**安裝程式 DLL 中。 安裝程式從 控制台呼叫 DLL 時，會叫用此函式。 若要新增、 修改或刪除資料來源， **SQLManageDataSources**呼叫**ConfigDSN**與該資料來源相關聯的驅動程式安裝程式的 DLL 中。 若要直接新增、 修改或刪除資料來源，程式會呼叫**SQLConfigDataSource**安裝程式 DLL 中。 程式會將傳遞資料來源，這個選項可指定要採取的動作的名稱。 **SQLConfigDataSource**呼叫**ConfigDSN**中安裝 DLL 並將其傳遞的引數從**SQLConfigDataSource**。  
  
 如需詳細資訊，請參閱 ODBC SDK*程式設計人員參考*章 23、 安裝 DLL 函式參考和第 24，安裝程式的 DLL 函式參考。  
  
## <a name="see-also"></a>另請參閱  
 [依數字的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)

