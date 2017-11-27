---
title: "將程式碼升級至通用 CRT | Microsoft Docs"
ms.custom: 
ms.date: 03/31/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eaf34c1b-da98-4058-a059-a10db693a5ce
caps.latest.revision: "1"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0f8742396a9ebe3780cb2c235238c9ce63986dc4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="upgrade-your-code-to-the-universal-crt"></a>將程式碼升級至通用 CRT

在 Visual Studio 2015 中，已重構 Microsoft C 執行階段程式庫 (CRT)。 標準 C 程式庫、POSIX 延伸模組以及 Microsoft 特定函式、巨集和全域變數都已移至新的程式庫：通用 C 執行階段程式庫 (通用 CRT 或 UCRT)。 CRT 的編譯器特有元件已移至新的 vcruntime 程式庫。  
  
UCRT 現在是 Windows 元件，而且隨附於 Windows 10。 UCRT 根據 C 呼叫慣例來支援穩定 ABI，並且緊密符合 ISO C99 標準，而且只有幾個例外狀況。 它不再繫結至特定編譯器版本。 您可以在 Visual Studio 2015 或 Visual Studio 2017 支援的任何 Windows 版本上使用 UCRT。 優點是每次升級 Visual Studio 時，您不再需要更新組建以將目標設為 CRT 的新版本。  
  
使用這項重構，許多 CRT 標頭檔、程式庫檔案和可轉散發套件的名稱和位置以及您程式碼所需的部署方法都已變更。 此外，UCRT 中的許多函式和巨集都已新增或變更，以改善標準一致性。 若要利用這些變更，必須更新您現有的程式碼和專案建置系統。  
  
## <a name="where-to-find-the-universal-crt-files"></a>找到通用 CRT 檔案的位置

作為 Windows 元件，UCRT 程式庫檔案和標頭現在是 Windows 軟體開發套件 (SDK) 的一部分。 當您安裝 Visual Studio 時，也會安裝使用 UCRT 所需的一部分 Windows SDK。 Visual Studio 安裝程式會將 UCRT 標頭、程式庫和 DLL 檔案的位置新增至 Visual Studio 專案建置系統所使用的預設路徑。 當您更新 Visual C++ 專案時，如果它們使用預設專案設定，則 IDE 會自動尋找標頭檔的新位置，而且連結器會自動使用新的預設 UCRT 和 vcruntime 程式庫。 同樣地，如果您使用開發人員命令提示字元執行命令列建置，則會更新包含標頭和程式庫路徑的環境變數，同時自動運作。  
  
標準 C 程式庫標頭檔現在位於 Windows SDK 之 include 資料夾的 SDK 版本特定目錄中。 標頭檔的一般位置是在 Windows Kits\\10\\Include\\_sdk 版本_\\ucrt 的 Program Files 或 Program Files (x86) 目錄中，其中 _sdk 版本_對應至 Windows 版本或更新，例如，10.0.14393.0 表示 Windows 10 年度更新版。   
  
UCRT 靜態程式庫和動態連結虛設常式程式庫位於 Windows Kits\\10\\Lib\\_sdk 版本_\\ucrt\\_architecture_ 的 Program Files 或 Program Files (x86) 目錄中，其中 _architecture_ 是 ARM、x86 或 X64。 零售和偵錯靜態程式庫是 libucrt.lib 和 libucrtd.lib，而 UCRT DLL 的程式庫是 ucrt.lib 和 ucrtd.lib。  
  
零售和偵錯 UCRT DLL 位於不同的位置中。 零售 DLL 是可轉散發套件，可在 Program Files 或 Program Files (x86) 目錄中的 Windows Kits\\10\\Redist\\ucrt\\DLLs\\_architecture_\. 下找到 偵錯 UCRT 程式庫不是可轉散發套件，可在 Program Files 或 Program Files (x86) 目錄中的 Windows Kits\\10\\bin\\_architecture_\\ucrt 資料夾下找到。   

C 和 C++ 編譯器特定執行階段支援程式庫 **vcruntime**包含支援程式啟動所需的程式碼以及例外狀況處理和內建函式這類功能。 程式庫和其標頭檔仍然位於 Program Files 或 Program files (x86) 目錄的版本特定 Microsoft Visual Studio 資料夾中。 在 Visual Studio 2017 中，標頭位於 Microsoft Visual Studio\\2017\\_版本_\\VC\\Tools\\MSVC\\_lib 版本_\\include 下，而且連結程式庫位於 Microsoft Visual Studio\\2017\\_版本_\\VC\\Tools\\MSVC\\_li b版本_\\lib\\_architecture_ 下，其中_版本_是已安裝的 Visual Studio 版本、_lib 版本_是程式庫的版本，而 _architecture_ 是處理器架構。 OneCore 和 Store 的連結程式庫也可以位於 libraries 資料夾中。 靜態程式庫的零售和偵錯版本是 libvcruntime.lib 和 libvcruntimed.lib。 動態連結零售和偵錯虛設常式程式庫分別是 vcruntime.lib 和 vcruntimed.lib。  
  
當您更新 Visual C++ 專案時，如果您已將專案的 [連結器] 屬性 [忽略所有預設程式庫] 設定為 [是]，或在命令列上使用 /NODEFAULTLIB 連結器選項，則必須更新要包含新已重構程式庫的程式庫清單。 請將舊的 CRT 程式庫 (例如，libcmt.lib、libcmtd.lib、msvcrt.lib 或 msvcrtd.lib) 取代為對等的重構程式庫。 如需要使用之特定程式庫的相關資訊，請參閱 [CRT 程式庫功能](../c-runtime-library/crt-library-features.md)。  
  
## <a name="deployment-and-redistribution-of-the-universal-crt"></a>通用 CRT 的部署和轉散發
  
因為 UCRT 現在是 Microsoft Windows 作業系統元件，所以是 Windows 10 中作業系統的一部分，並可透過 Windows Vista 到 Windows 8.1 的較舊作業系統的 Windows Update 取得。 Windows XP 具有可轉散發版本。 作為作業系統元件，不管 Visual Studio 和 Visual C++ 編譯器版本為何，Windows Update 都會管理 UCRT 更新和服務。 因為 UCRT 是 Windows 元件，所以基於更新的安全性和簡易性，以及較小的影像大小，強烈建議集中部署您應用程式的 UCRT。  
  
您可以在 Visual Studio 2015 或 Visual Studio 2017 支援的任何 Windows 版本上使用 UCRT。 您可以針對 Windows 10 以外的 Windows 支援版本，使用 vcredist 套件進行轉散發。 vcredist 套件包括 UCRT 元件，並將它們自動安裝在預設未安裝它們的 Windows 作業系統上。 如需詳細資訊，請參閱[轉散發 Visual C++ 檔案](../ide/redistributing-visual-cpp-files.md)。  
  
支援 UCRT 的應用程式本機部署，但基於效能和安全性原因不建議使用。 進行應用程式本機部署的 DLL 隨附為 Windows SDK 的一部分，且位於 **redist** 子目錄下。 所需的 DLL 包括 ucrtbase.dll 和一組名為 api-ms-win-_subset_.dll 的 **APISet forwarder** DLL。 每個作業系統上所需的這組 DLL 都會不同，因此建議您在使用應用程式本機部署時包括所有 DLL。 如需應用程式本機部署的其他詳細資料和注意事項，請參閱 [Visual C++ 中的部署](../ide/deployment-in-visual-cpp.md)。  
  
## <a name="changes-to-the-universal-crt-functions-and-macros"></a>通用 CRT 函式和巨集的變更  

已在 UCRT 中新增或更新許多函式，可改善 ISO C99 一致性，以及解決程式碼品質和安全性問題。 在某些情況下，這需要程式庫的重大變更。 如果您的程式碼在使用舊版 CRT 時能夠正確編譯，但在使用 UCRT 編譯時中斷，則必須變更程式碼才能利用這些更新和功能。 如需通用 CRT 中找到之 CRT 的詳細重大變更和更新清單，請參閱 Visual C++ 變更歷程記錄的 [C 執行階段程式庫 (CRT)](visual-cpp-change-history-2003-2015.md#BK_CRT) 區段。 它包括受影響標頭和函式的清單，可用來識別您程式碼中所需的變更。  
  
## <a name="see-also"></a>另請參閱  

[Visual C++ 移植和升級指南](visual-cpp-porting-and-upgrading-guide.md)  
[潛在升級問題概觀 (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)  
[從舊版的 Visual C++ 升級專案](upgrading-projects-from-earlier-versions-of-visual-cpp.md)  
[Visual C++ 變更歷程記錄 2003 - 2015](visual-cpp-change-history-2003-2015.md)  
[Visual Studio 2017 中的 C++ 一致性改善](../cpp-conformance-improvements-2017.md)  
