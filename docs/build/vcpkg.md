---
title: vcpkg:Windows、Linux 和MacOS的C++包管理器
description: vcpkg 是一個命令行包管理器,它極大地簡化了在 Windows、MacOS 和 Linux 上獲取和安裝開源C++庫。
ms.date: 01/10/2020
ms.technology: cpp-ide
ms.assetid: f50d459a-e18f-4b4e-814b-913e444cedd6
ms.openlocfilehash: 9dbeba1f55164ace01fb8bb26155dd9319ba62db
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335400"
---
# <a name="vcpkg-a-c-package-manager-for-windows-linux-and-macos"></a>vcpkg:Windows、Linux 和MacOS的C++包管理器

vcpkg 是C++的命令行包管理器。 它極大地簡化了 Windows、Linux 和 MacOS 上第三方庫的獲取和安裝。 如果您的專案使用協力廠商程式庫，我們建議您使用 vcpkg 加以安裝。 vcpkg 支援開放原始碼和專屬程式庫。 vcpkg Windows 目錄中的所有程式庫皆已通過 Visual Studio 2015、Visual Studio 2017 和 Visual Studio 2019 的相容性測試。 在 Windows 和 Linux/MacOS 目錄之間,vcpkg 現在支援 1900 多個庫。 C++ 社群正持續不斷地在兩個目錄中新增更多程式庫。

## <a name="simple-yet-flexible"></a>簡單卻有彈性

您可使用單一命令下載來源並建置程式庫。 vcpkg 本身是開放原始碼專案，可於 GitHub 取得。 可以自定義您的私有 vcpkg 克隆,以任何你喜歡的方式。 例如,指定與公共目錄中的庫不同的庫或不同版本的庫。 您可以在一台電腦上有多個 vcpkg 複製。 每個庫都可以設置為使用首選的編譯開關生成自定義庫集合。 每個複製品都是完全獨立的環境，並具有只會在其本身階層執行的專屬 vcpkg.exe 複本。 vcpkg不會添加到任何環境變數中,並且不依賴於 Windows 註冊表或可視化工作室。

## <a name="sources-not-binaries"></a>來源,而不是二進位檔案

對於 Windows 目錄中的庫,vcpkg 下載來源而不是二進位檔案<sup>1</sup>。 它會使用所能找到的最新版 Visual Studio 來編譯這些來源。 在C++中,應用程式代碼和您使用的任何庫都由同一編譯器和編譯器版本編譯非常重要。 使用 vcpkg 可排除或至少大幅降低二進位不符的可能性，及其引發的問題。 在編譯器的特定版本的標準化團隊中,一個團隊成員可以使用 vcpkg 下載源並編譯一組二進位檔案。 然後,他們可以使用匯出命令壓縮其他團隊成員的二進位檔和標頭。 如需詳細資訊，請參閱下面的[匯出編譯的二進位檔和標頭](#export_binaries_per_project)。

您還可以創建在埠集合中具有專用庫的 vcpkg 克隆。 添加下載預構建二進位檔和標頭的埠。 然後,編寫一個 portfile.cmake 檔,該檔只需將這些檔案複製到首選位置即可。

<sup>1</sup> *注意:某些專有庫的源不可用。在這些情況下,vcpkg 下載相容的預構建二進位檔。*

## <a name="installation"></a>安裝

從 GitHub 克隆[https://github.com/Microsoft/vcpkg](https://github.com/Microsoft/vcpkg)vcpkg 儲存庫: 。 您可以下載到您偏好的任何資料夾位置。

在根資料夾中執行啟動載入器：

- **bootstrap-vcpkg.bat** (Windows)
- **./bootstrap-vcpkg.sh** (Linux、MacOS)

## <a name="search-the-list-of-available-libraries"></a>搜尋可用的程式庫清單

若要查看有哪些套件可用，請在命令提示字元中鍵入：**vcpkg search**

此命令會列舉 vcpkg/ports 子資料夾中的控制檔案。 您將看到以下的清單:

```cmd
ace       6.4.3   The ADAPTIVE Communication Environment
anax      2.1.0-1 An open source C++ entity system. \<https://github...
antlr4    4.6-1   ANother Tool for Language Recognition
apr       1.5.2   The Apache Portable Runtime (APR) is a C library ...
asio      1.10.8  Asio is a cross-platform C++ library for network ...
assimp    3.3.1   The Open Asset import library
atk       2.24.0  GNOME Accessibility Toolkit
...
```

您可以針對模式篩選，例如 **vcpkg search ta**：

```cmd
botan       2.0.1      A cryptography library written in C++11
portaudio   19.0.6.00  PortAudio Portable Cross-platform Audio I/O API P...
taglib      1.11.1-2   TagLib Audio Meta-Data Library
```

### <a name="install-a-library-on-your-local-machine"></a>在本機電腦上安裝程式庫

使用 **vcpkg search** 取得程式庫名稱之後，則用 **vcpkg install** 下載並編譯程式庫。 vcpkg 在連接埠目錄中使用程式庫的 portfile。 如果未指定任何三元組，則 vcpkg 會針對目標平台的預設三元組進行安裝和編譯：x86-windows、x64-linux.cmake 或 x64-osx.cmake。

如果是 Linux 程式庫，vcpkg 取決於本機電腦上安裝的 gcc。 在 MacOS 上，vcpkg 使用 Clang。

當 portfile 指定依賴項時,vcpkg 也會下載並安裝它們。 下載后,vcpkg使用庫使用的相同生成系統生成庫。 CMake 和(在 Windows 上)MSBuild 專案是首選,但支援 MAKE 以及任何其他生成系統。 如果 vcpkg 在本地電腦上找不到指定的生成系統,它將下載並安裝它。

```cmd
> vcpkg install boost:x86-windows

The following packages will be built and installed:
    boost:x86-windows
  * bzip2:x86-windows
  * zlib:x86-windows
Additional packages (*) will be installed to complete this operation.
```

若為 CMAKE 專案，請使用 CMAKE_TOOLCHAIN_FILE，以利用 `find_package()` 提供程式庫。 例如：

```cmd
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg/scripts/buildsystems/vcpkg.cmake (Linux/MacOS)
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg\scripts\buildsystems\vcpkg.cmake (Windows)
```

## <a name="list-the-libraries-already-installed"></a>列出已安裝的程式庫

安裝某些庫後,可以使用**vcpkg 列表**檢視具有的內容:

```cmd
> vcpkg list

boost:x86-windows       1.64-3   Peer-reviewed portable C++ source libraries
bzip2:x86-windows       1.0.6-1  High-quality data compressor.
cpprestsdk:x86-windows  2.9.0-2  C++11 JSON, REST, and OAuth library The C++ REST ...
openssl:x86-windows     1.0.2k-2 OpenSSL is an open source project that provides a...
websocketpp:x86-windows 0.7.0    Library that implements RFC6455 The WebSocket Pro...
zlib:x86-windows        1.2.11   A compression library
```

## <a name="integrate-with-visual-studio-windows"></a>與 Visual Studio 整合 (Windows)

### <a name="per-user"></a>每個使用者

運行**vcpkg 整合安裝**以設定 Visual Studio 以按使用者查找所有 vcpkg 頭檔和二進位檔案。 無需手動編輯 VC++ 目錄路徑。 如果有多個複製,則運行此命令的複製將成為新的預設位置。

現在,只需鍵入資料夾/標頭即可#include標頭,並且自動完成即可為您提供説明。 不需要任何其他步驟即可連結至程式庫或新增專案參考。 下圖顯示 Visual Studio 如何找到 azure-storage-cpp 標頭。 vcpkg 會將其標頭放在 **/installed** 子資料夾中，依目標平台分割資料。 下圖顯示程式庫 **/was** 子資料夾中的 Include 檔清單：

![vcpkg 和 IntelliSense](media/vcpkg-intellisense.png "vcpkg 和 IntelliSense")

### <a name="per-project"></a>每個專案

如果需要使用不同於活動 vcpkg 實例中版本的特定版本的庫,請按照以下步驟操作:

1. 建立新的 vcpkg 複製品
1. 修改程式庫的連接埠檔案以取得您需要的版本
1. 執行 **vcpkg install \<library>**。
1. 使用 **vcpkg integrate project** 依每個專案建立參考該程式庫的 NuGet 套件。

## <a name="integrate-with-visual-studio-code-linuxmacos"></a>與 Visual Studio Code 整合 (Linux/MacOS)

運行**vcpkg 整合安裝**,在 Linux/MacOS 上配置可視化工作室代碼。 此命令設定 vcpkg 登記的位置,並在源檔上啟用 IntelliSense。

## <a name="target-linux-from-windows-via-wsl"></a>透過 WSL 從 Windows 將 Linux 設為目標

您可以使用適用於 Linux 的 Windows 子系統或 WSL 在 Windows 電腦上生成 Linux 二進位檔案。 請遵循指示[在 Windows 10 上安裝 WSL](/windows/wsl/install-win10)，並使用[適用於 Linux 的 Visual Studio 延伸模組](https://blogs.msdn.microsoft.com/vcblog/2017/02/08/targeting-windows-subsystem-for-linux-from-visual-studio/)進行設定。 可以將所有為 Windows 和 Linux 構建的庫放入同一資料夾中。 它們可從 Windows 和 WSL 訪問。

## <a name="export-compiled-binaries-and-headers"></a><a name="export_binaries_per_project"></a> 匯出編譯的二進位檔和標頭

讓團隊中的每個人都下載並構建公共庫是低效的。 單個團隊成員可以使用**vcpkg 匯出**命令建立二進位檔案和標頭的通用 zip 檔或 NuGet 包。 然後,很容易與其他團隊成員共用它。

## <a name="updateupgrade-installed-libraries"></a>更新/升級安裝的程式庫

公共目錄與最新版本的庫保持最新。 若要判斷哪些本機程式庫已過期，請使用 **vcpkg update**。 準備好將埠集合更新到最新版本的公共目錄時,請運行**vcpkg 升級**命令。 它會自動下載和重建任何或所有已安裝的過期庫。

默認情況下,**升級**命令僅列出過期的庫;因此,升級命令僅列出過期的庫。它不升級它們。 要實際升級庫,請使用 **「無幹運行」** 選項。

```cmd
  vcpkg upgrade --no-dry-run
```

### <a name="upgrade-options"></a>升級選項

- **--no-dry-run**  執行升級；若未指定，命令只列出過期的套件。
- **--keep-going**  即使其中一個套件失敗仍繼續安裝。
- **--triplet \<t>**  設定不合格套件的預設 triplet。
- **--vcpkg-root \<path>**  指定要使用的 vcpkg 目錄，而不是目前目錄或工具目錄。

### <a name="upgrade-example"></a>升級範例

下列範例示範如何只升級指定的程式庫。 必要時,vcpkg會自動拉入依賴項。

```cmd
c:\users\satyan\vcpkg> vcpkg upgrade tiny-dnn:x86-windows zlib
The following packages are up-to-date:
   tiny-dnn:x86-windows

The following packages will be rebuilt:
    * libpng[core]:x86-windows
    * tiff[core]:x86-windows
      zlib[core]:x86-windows
Additional packages (*) will be modified to complete this operation.
If you are sure you want to rebuild the above packages, run this command with the --no-dry-run option.
```

## <a name="contribute-new-libraries"></a>提供新的程式庫

您可以在私人連接埠集合中包含喜歡的任何程式庫。 若要為公用類別目錄建議新的程式庫，請前往 [GitHub vcpkg 問題頁面](https://github.com/Microsoft/vcpkg/issues)提出問題。

## <a name="remove-a-library"></a>移除程式庫

鍵入 **vcpkg remove** 可移除安裝的程式庫。 如果任何其他庫依賴於它,系統將要求您使用 **--recurse**重新執行該命令,這將導致刪除所有下游庫。

## <a name="customize-vcpkg"></a>自訂 vcpkg

您可以用任何喜歡的方式修改您的 vcpkg 複製品。 您甚至可以創建多個 vcpkg 克隆,然後修改每個複製中的埠檔。 這是獲取特定庫版本或指定特定命令列參數的簡單方法。 例如,在企業中,單個開發人員組可能處理具有一組特定於其組的依賴項的軟體。 解決方案是為每個團隊設置 vcpkg 的克隆。 然後,修改複製以下載庫版本並設置每個團隊所需的編譯開關。

## <a name="uninstall-vcpkg"></a>將 vcpkg 解除安裝

只需刪除 vcpkg 目錄。 刪除此目錄將卸載 vcpkg 分發,以及 vcpkg 已安裝的所有庫。

## <a name="send-feedback-about-vcpkg"></a>傳送 vcpkg 的相關意見反應

使用 **vcpkg contact --survey** 命令可向 Microsoft 傳送 vcpkg 的相關意見反應，包括功能的 Bug 回報與建議。

## <a name="the-vcpkg-folder-hierarchy"></a>vcpkg 資料夾階層

所有 vcpkg 功能與資料皆完全獨立於單一目錄階層中，稱為「執行個體」。 沒有登錄設定或環境變數。 計算機上可以具有任意數量的 vcpkg 實例,並且它們不會相互干擾。

vcpkg 執行個體的內容如下：

- 組建樹狀結構 -包含每個程式庫建置來源的子資料夾
- 文件 - 文件和範例
- 下載 - 任何已下載工具或來源的快取複本。 運行安裝命令時,vcpkg 首先會搜索此處。
- 已安裝 - 包含每個已安裝程式庫的標頭和二進位檔。 當您與 Visual Studio 整合時,您實際上是在告訴它將此資料夾添加到其搜尋路徑中。
- 套件 - 各安裝階段間的內部資料夾。
- 連接埠 - 描述目錄中各程式庫、其版本及下載位置的檔案。 如有需要可新增自己的連接埠。
- 指令碼 - vcpkg 使用的指令碼 (cmake、powershell)。
- toolsrc - vcpkg 和相關元件的 C++ 原始程式碼
- triplet -- 包含每個受支援目標平台的設定 (例如 x86-windows 或 x64-uwp)。

## <a name="command-line-reference"></a>命令列參考

|Command|描述|
|---------|---------|
|**vcpkg\[搜索拍拍***|搜尋可安裝的套件|
|**vcpkg install \<pkg>...**|安裝套件|
|**vcpkg remove \<pkg>...**|解除安裝套件|
|**vcpkg remove --outdated**|將過期的套件解除安裝|
|**vcpkg list**|列出安裝的套件|
|**vcpkg update**|顯示要更新的套件清單|
|**vcpkg upgrade**|重建所有過期的套件|
|**vcpkg 哈\<希 檔案> \[alg]**|依特定演算法雜湊檔案，預設為 SHA512|
|**vcpkg integrate install**|讓所有使用者皆可使用安裝的套件。 第一次使用需要有管理員權限|
|**vcpkg integrate remove**|移除全使用者整合|
|**vcpkg integrate project**|產生參考 NuGet 套件供個別 VS 專案使用|
|**vcpkg\<出口 pkg>...\[選擇*...**|匯出套件|
|**vcpkg edit \<pkg>**|開啟連接埠以進行編輯 (使用 %EDITOR%，預設為 'code')|
|**vcpkg\<建立\<\[pkg> url>存档名称***|建立新套件|
|**vcpkg cache**|列出快取的已編譯套件|
|**vcpkg version**|顯示版本資訊|
|**vcpkg contact --survey**|顯示要傳送意見反應的連絡人資訊。|

### <a name="options"></a>選項。

|選項|描述|
|---------|---------|
|**--triplet \<t>**|指定目標架構 triplet。 (預設：`%VCPKG_DEFAULT_TRIPLET%`，另請參閱 **vcpkg help triplet**)|
|**--vcpkg-root \<path>**|指定 vcpkg 根目錄 (預設：`%VCPKG_ROOT%`)|
