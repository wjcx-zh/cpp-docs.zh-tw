---
title: "vcpkg -- 適用於 Windows 的 C++ 套件管理員 | Microsoft Docs"
description: "vcpkg 是命令列套件管理員，大幅簡化在 Windows 上取得和安裝開放原始碼 C++ 程式庫的流程。"
keywords: vcpkg
author: mikeblome
ms.author: mblome
ms.date: 05/30/2017
ms.technology: cpp-ide
ms.tgt_pltfrm: windows
ms.assetid: f50d459a-e18f-4b4e-814b-913e444cedd6
ms.topic: article
dev_langs: C++
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0728827cb2cd604ec4e7ff1ef58b68ed8fb64532
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="vcpkg-c-package-manager-for-windows"></a>vcpkg：適用於 Windows 的 C++ 套件管理員 
vcpkg 是命令列套件管理員，大幅簡化在 Windows 上取得和安裝協力廠商程式庫的流程。 如果您的專案使用協力廠商程式庫，我們建議您使用 vcpkg 加以安裝。 vcpkg 支援開放原始碼和專屬程式庫。 vcpkg 公用目錄中的所有程式庫皆已通過 Visual Studio 2015 和 Visual Studio 2017 的相容性測試。 截至 2017 年 5 月，目錄中有超過 238 個程式庫，而且 C++ 社群還持續不斷新增更多的程式庫。

## <a name="simple-yet-flexible"></a>簡單卻有彈性
您可使用單一命令下載來源並建置程式庫。 vcpkg 本身是開放原始碼專案，可於 GitHub 取得。 您可以用自己喜歡的方式自訂您的個人複製品，例如，指定和公用目錄中找到的程式庫不一樣的程式庫，或不同的程式庫版本。 一部電腦上可以有多個 vcpkg 複製品，每個複製品產生自訂程式庫集及 (或) 編譯參數等等。每個複製品都是完全獨立、無限複製的環境，有只在自己階層作業的專屬 vcpkg.exe 複本。 vcpkg 未新增至任何環境變數，和 Windows 登錄或 Visual Studio 沒有相依性。

## <a name="sources-not-binaries"></a>不是二進位檔的來源
針對公用目錄中的程式庫，vcpkg 會下載來源，不會下載二進位檔 [1]。 vcpkg 會使用 Visual Studio 2017 編譯這些來源，如未安裝 2017 則使用 Visual Studio 2015。 在 C++ 中，使用相同的編譯器及編譯器版本來編譯所用的任何程式庫十分重要，因為應用程式程式碼會與其建立連結。 使用 vcpkg，可排除或至少大幅降低出現不相符二進位的可能性，以及衍生問題。 在以特定 Visual C++ 編譯器版本為標準的小組中，某個小組成員可以使用 vcpkg 下載來源並編譯二進位檔集合，然後使用匯出命令壓縮二進位檔和標頭，供其他小組成員使用。 如需詳細資訊，請參閱下面的＜匯出編譯的二進位檔和標頭＞。 

如果您使用連接埠集合中的私人程式庫建立 vcpkg 複製品，您可以新增連接埠下載預先建置的二進位檔和標頭，並撰寫 portfile.cmake 檔案，只將這些檔案複製到想要的位置。

[1] *注意：部分專屬程式庫無法取得來源。在這些案例中，Vcpkg 會下載相容的預先建置二進位檔。*

## <a name="installation"></a>安裝
從 GitHub 複製 vcpkg 儲存機制：https://github.com/Microsoft/vcpkg。 您可以下載到您偏好的任何資料夾位置。

在根資料夾中執行啟動程序：bootstrap-vcpkg.bat。

## <a name="basic-tasks"></a>基本工作
  
### <a name="search-the-list-of-available-libraries"></a>搜尋可用的程式庫清單
若要查看有哪些套件可用，請在命令提示字元中鍵入：`vcpkg search`

此命令會列舉 vcpkg/ports 子資料夾中的控制檔案。 您會看到類似下面的清單內容：

```cmd
ace       6.4.3   The ADAPTIVE Communication Environment
anax      2.1.0-1 An open source C++ entity system. <https://github...
antlr4    4.6-1   ANother Tool for Language Recognition
apr       1.5.2   The Apache Portable Runtime (APR) is a C library ...
asio      1.10.8  Asio is a cross-platform C++ library for network ...
assimp    3.3.1   The Open Asset import library
atk       2.24.0  GNOME Accessibility Toolkit
...
```

  您可以針對模式篩選，例如 `vcpkg search ta`：

```cmd
botan       2.0.1      A cryptography library written in C++11
portaudio   19.0.6.00  PortAudio Portable Cross-platform Audio I/O API P...
taglib      1.11.1-2   TagLib Audio Meta-Data Library

```

### <a name="install-a-library-on-your-local-machine"></a>在本機電腦上安裝程式庫
使用 `vcpkg search` 取得程式庫名稱之後，您使用 `vcpkg install` 下載並編譯程式庫。 vcpkg 在連接埠目錄中使用程式庫的 portfile。 如果不指定任何 triplet，vcpkg 會安裝並編譯適用於 x86-windows 的版本。 如果 portfile 指定相依性，vcpkg 就也會下載並安裝相依性。 下載後，vcpkg 會使用程式庫使用的任何組建系統來建置程式庫。 建議使用 CMake 和 MSBuild 專案檔案，但也支援 MAKE 和任何其他組建系統。 如果 vcpkg 在本機電腦上找不到指定的組建系統，會將其下載並安裝。

```cmd
> vcpkg install boost:x86-windows

The following packages will be built and installed:
    boost:x86-windows
  * bzip2:x86-windows
  * zlib:x86-windows
Additional packages (*) will be installed to complete this operation.
```

### <a name="list-the-libraries-already-installed"></a>列出已安裝的程式庫
在您安裝了部分程式庫之後，就可以使用 `vcpkg list` 查看現有的內容：

```cmd
> vcpkg list

boost:x86-windows       1.64-3   Peer-reviewed portable C++ source libraries
bzip2:x86-windows       1.0.6-1  High-quality data compressor.
cpprestsdk:x86-windows  2.9.0-2  C++11 JSON, REST, and OAuth library The C++ REST ...
openssl:x86-windows     1.0.2k-2 OpenSSL is an open source project that provides a...
websocketpp:x86-windows 0.7.0    Library that implements RFC6455 The WebSocket Pro...
zlib:x86-windows        1.2.11   A compression library
```

### <a name="integrate-with-visual-studio"></a>與 Visual Studio 整合
#### <a name="per-user"></a>每個使用者
執行 `vcpkg integrate install` 以設定 Visual Studio 針對每個使用者一一尋找所有 vcpkg 標頭檔和二進位檔，不需要手動編輯 VC++ 目錄路徑。 如有多個複製品，此命令執行所在的複製品就會成為新的預設位置。

現在您只要鍵入資料夾/標頭就可以 #include 標頭，自動完成會協助您。 不需要任何其他步驟即可連結至程式庫或新增專案參考。 下圖顯示 Visual Studio 如何找到 azure-storage-cpp 標頭。 vcpkg 將其標頭放在 \installed 子資料夾中，依目標平台分割資料。 下圖顯示程式庫 `/was` 子資料夾中的 Include 檔清單：

 ![vcpkg Intellisense 整合](media/vcpkg-intellisense.png "vcpkg 與 Intellisense")  

#### <a name="per-project"></a>每個專案
如果您需要使用和使用中的 vcpkg 執行個體版本不同的特定程式庫版本，您可以建立新的 vcpkg 複製品，修改程式庫的 portfile 以取得所需版本，再執行 `vcpkg install <library>`。 在這之後，您可以使用 `vcpkg integrate project` 在每個專案中逐一建立參考該程式庫的 NuGet 套件。

### <a name="export-compiled-binaries-and-headers"></a>匯出編譯的二進位檔和標頭
要求小組所有人都下載及建置程式庫很沒效率。 一名小組成員就可以執行該工作，然後使用 `vcpkg export` 建立二進位檔和標頭的 zip 檔案，輕輕鬆鬆和其他小組成員共用。 

### <a name="update-installed-libraries"></a>更新已安裝的程式庫
公用目錄會隨程式庫最新版本保持在最新狀態。 若要判斷哪些本機程式庫已過期，請使用 `vcpkg update`。 當你準備將連接埠集合更新至公用目錄的最新版本時，請只對 github 儲存機制執行 git 提取作業，或建立新的複製品並保留舊的 (如仍需要)。

### <a name="contribute-new-libraries"></a>提供新的程式庫
您可以在私人連接埠集合中包含喜歡的任何程式庫。 若要為公用類別目錄建議新的程式庫，請前往 [GitHub vcpkg 問題頁面](https://github.com/Microsoft/vcpkg/issues)提出問題。

### <a name="remove-a-library"></a>移除程式庫
鍵入 `vcpkg remove` 可移除已安裝的程式庫。 如有任何其他程式庫與其相依，系統會要求您以 `--recurse` 重新執行命令，這會移除所有的下游程式庫。

### <a name="customize-vcpkg"></a>自訂 vcpkg
您可以用任何喜歡的方式修改您的 vcpkg 複製品。 您可以建立多個 vcpkg 複製品，並修改各複製品的 portfile 以取得特定的程式庫版本，或指定命令列參數。 例如，在企業中，一組開發人員可能正在處理有相依性集合的軟體，而另一組人馬則可能有其他集合。 您可以設定兩個 vcpkg 複製品，然後修改每個複製品，根據您的需求下載程式庫版本和編譯參數等等。 

### <a name="uninstall-vcpkg"></a>將 vcpkg 解除安裝
只要刪除目錄即完成。 

## <a name="the-vcpkg-folder-hierarchy"></a>vcpkg 資料夾階層
所有 vcpkg 功能和資料都是完全獨立在單一目錄階層中，稱之為「執行個體」。 沒有登錄設定或環境變數。 您可以在電腦上建立無數個執行個體，而不必擔心互相干擾的問題。 

vcpkg 執行個體的內容如下： 
- 組建樹狀結構 -包含每個程式庫建置來源的子資料夾
- 文件 - 文件和範例
- 下載 - 任何已下載工具或來源的快取複本。 當您執行安裝命令時，vcpkg 會優先搜尋此位置。
- 已安裝 - 包含每個已安裝程式庫的標頭和二進位檔。 當您與 VIsual Studio 整合時，即表示將此資料夾新增至其搜尋路徑。
- 套件 - 各安裝階段間的內部資料夾。
- 連接埠 - 描述目錄中各程式庫、其版本及下載位置的檔案。 如有需要可新增自己的連接埠。
- 指令碼 - vcpkg 使用的指令碼 (cmake、powershell)。
- toolsrc - vcpkg 和相關元件的 C++ 原始程式碼
- triplet - 包含每個受支援目標平台的設定 (例如 x86-windows 或 x64-uwp)。

## <a name="command-line-reference"></a>命令列參考
- vcpkg search [pat]        搜尋可建置的套件
- vcpkg install <pkg>...  安裝套件
- vcpkg remove <pkg>...解除安裝套件
- vcpkg remove --outdated   解除安裝所有過時的套件
- vcpkg list            列出已安裝的套件
- vcpkg update          顯示要更新的套件清單
- vcpkg hash <file> [alg]       依特定演算法雜湊檔案，預設為 SHA512
- vcpkg integrate install       讓所有使用者都能取用已安裝的套件。 第一次使用需要有管理員權限
- vcpkg integrate remove        移除所有使用者的整合
- vcpkg integrate project        產生參考 nuget 套件供個別 VS 專案使用
- vcpkg export <pkg>... [opt]...  匯出套件
- vcpkg edit <pkg>      開啟連接埠進行編輯 (使用 %EDITOR%，預設為 'code')
- vcpkg import <pkg>        匯入預先建置的程式庫
- vcpkg create <pkg> <url>   [archivename]        建立新套件
- vcpkg owns <pat>      在已安裝的套件中搜尋檔案
- vcpkg cache           列出已快取的編譯套件
- vcpkg version         顯示版本資訊
- vcpkg contact         顯示傳送意見反應的連絡人資訊

### <a name="options"></a>選項:
  **`--triplet <t>`**指定目標架構 triplet。 (預設：`%VCPKG_DEFAULT_TRIPLET%`，亦請參閱`vcpkg help triplet`)

  **`--vcpkg-root <path>`**指定 vcpkg 根目錄 (預設：`%VCPKG_ROOT%`)
