---
title: "轉散發 MFC 程式庫 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC, redistributing
- redistributing MFC library
ms.assetid: 72714ce1-385e-4c1c-afa5-96b03e873866
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9ca153ec9ca079bf13b1c1c1dcedd6e41497307f
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="redistributing-the-mfc-library"></a>轉散發 MFC 程式庫
如果您以動態方式連結 MFC 程式庫的應用程式，您必須重新發佈比對 MFC DLL。 例如，如果使用 Visual Studio 2015 使用 MFC 所隨附的版本建置 MFC 應用程式，您必須重新發佈 mfc140.dll 或 mfc140u.dll，根據您的應用程式編譯窄字元或 Unicode 支援。  
  
> [!NOTE]
>  在 Visual Studio 2015 RTM 中的可轉散發檔案目錄已省略 mfc140.dll 檔案。 您可以使用安裝 Visual Studio 2015 的 Windows\system32 和 Windows\syswow64 目錄中的版本。  
  
 因為所有的 MFC Dll 會使用共用的版本的 C 執行階段程式庫 (CRT)，則您可能需要重新發佈 CRT。 使用 Visual Studio 2015 的 MFC 所隨附的版本會使用通用的 CRT 程式庫，這以 Windows 10 的一部分散發。 若要執行舊版 Windows 上使用 Visual Studio 2015 建置 MFC 應用程式，您必須重新發佈通用 CRT。 如需如何轉散發通用的 CRT，做為作業系統元件或使用本機部署資訊，請參閱[簡介： 通用 CRT](http://go.microsoft.com/fwlink/p/?linkid=617977)。 若要下載通用 CRT 支援的 Windows 版本上的中央部署，請參閱[Windows 10 通用 C 執行階段](http://go.microsoft.com/fwlink/p/?LinkId=619489)。 Windows SDK 中找到可轉散發套件的架構特定版本的 ucrtbase.dll 進行本機部署。 根據預設，Visual Studio 會安裝在 C:\Program Files (x86) \Windows Kits\10\Redist\ucrt\DLLs\ 架構特定子目錄中。  
  
 如果您的應用程式使用舊版的 MFC 程式庫所建置，您必須重新發佈相符 CRT DLL 從可轉散發檔案的目錄。 例如，如果使用 Visual Studio 2013 (vc120) 工具組建置 MFC 應用程式，您必須重新發佈 msvcr120.dll。 您也需要重新發佈的比對 mfc`<version>`u.dll 或 mfc`<version>`.dll。  
  
 如果您以靜態方式連結至 MFC 的應用程式 (亦即，如果您指定**使用 MFC 靜態程式庫**上**一般**索引標籤中**屬性頁**對話方塊)，您不需要若要轉散發 MFC DLL。 不過，雖然靜態連結可能適用於測試，因此內部部署應用程式，建議您不要使用它來轉散發 MFC。 如需建議的策略可用來部署 Visual c + + 程式庫的詳細資訊，請參閱[選擇部署方法](../ide/choosing-a-deployment-method.md)。  
  
 如果您的應用程式會使用實作 WebBrowser 控制項的 MFC 類別 (例如， [CHtmlView 類別](../mfc/reference/chtmlview-class.md)或[CHtmlEditView 類別](../mfc/reference/chtmleditview-class.md))，我們建議您也安裝最新版本Microsoft Internet Explorer，讓目標電腦會有最新的通用控制項檔案。 （最少，Internet Explorer 4.0 是必要）。如何安裝 Internet Explorer 元件的相關資訊是"發行項 185375:: 方式來建立單一 EXE 安裝的 Internet Explorer 提供 「 Microsoft 支援網站上。  
  
 如果您的應用程式使用之 MFC 資料庫類別 (例如， [CRecordset 類別](../mfc/reference/crecordset-class.md)和[CRecordView 類別](../mfc/reference/crecordview-class.md))，您必須轉散發 ODBC 和應用程式所使用的任何 ODBC 驅動程式。 如需詳細資訊，請參閱[轉散發資料庫支援檔案](../ide/redistributing-database-support-files.md)。  
  
 如果您的 MFC 應用程式使用 Windows Form 控制項，您必須重新 mfcmifc80.dll 發佈您的應用程式。 這個 DLL 是可轉散發的應用程式在其應用程式本機資料夾或部署到全域組件快取 (GAC) 中使用強式名稱簽署.NET 組件[Gacutil.exe （全域組件快取工具）](/dotnet/framework/tools/gacutil-exe-gac-tool)。  
  
 如果您轉散發 MFC DLL，請確定重新發佈的零售版而不偵錯版本。 偵錯版本的 Dll 不是可轉散發套件。 MFC Dll 的偵錯版本的名稱結尾"d"，例如 Mfc140d.dll。  
  
 您可以使用任一 VCRedist_ 轉散發 MFC*架構*.exe、 可由 MFC DLL 部署到您的應用程式相同的資料夾或使用 Visual Studio 安裝的合併模組。 如需如何轉散發 MFC 的詳細資訊，請參閱[轉散發 Visual c + + 檔案](../ide/redistributing-visual-cpp-files.md)。  
  
## <a name="installation-of-localized-mfc-components"></a>當地語系化的 MFC 元件的安裝  
 如果您決定要當地語系化您的應用程式藉由安裝 MFC 當地語系化 DLL，您必須使用可轉散發合併檔案 (.msm)。 比方說，如果您想要當地語系化您的應用程式，在 x86 電腦，您必須合併 Microsoft_VC`<version>`_MFCLOC_x86.msm x86 的安裝封裝的電腦。  
  
 可轉散發套件.msm 檔案包含可用來當地語系化的 Dll。 沒有一個 DLL，針對每個支援的語言。 安裝程序會將這些 Dll 安裝在目標電腦上在 %windir%\system32\ 資料夾中。  
  
 如需如何當地語系化 MFC 應用程式的詳細資訊，請參閱[TN057: MFC 元件的當地語系化](../mfc/tn057-localization-of-mfc-components.md)，以及[文章 208983： 如何使用 MFC LOC Dll](http://go.microsoft.com/fwlink/p/?linkid=198025) Microsoft 技術支援網站上。  
  
 您可以藉由部署應用程式本機資料夾中的 MFC DLL 轉散發 MFC 當地語系化 Dll。 如需如何轉散發 Visual c + + 程式庫的詳細資訊，請參閱[轉散發 Visual c + + 檔案](../ide/redistributing-visual-cpp-files.md)。  
  
## <a name="see-also"></a>請參閱  
 [轉散發 Visual C++ 檔案](../ide/redistributing-visual-cpp-files.md)