---
title: vcpkg：適用于 Windows、Linux 和 macOS 的 c + + 套件管理員
description: vcpkg 是命令列套件管理員，可大幅簡化 Windows、macOS 和 Linux 上的開放原始碼 c + + 程式庫的取得和安裝。
ms.date: 07/06/2020
ms.technology: cpp-ide
ms.assetid: f50d459a-e18f-4b4e-814b-913e444cedd6
ms.openlocfilehash: 2a179a25a7332a93486d42750f06f18658991b30
ms.sourcegitcommit: 85d96eeb1ce41d9e1dea947f65ded672e146238b
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "86058642"
---
# <a name="vcpkg-a-c-package-manager-for-windows-linux-and-macos"></a>vcpkg：適用于 Windows、Linux 和 macOS 的 c + + 套件管理員

vcpkg 是 c + + 的命令列套件管理員。 它可大幅簡化在 Windows、Linux 和 macOS 上取得和安裝協力廠商程式庫的過程。 如果您的專案使用協力廠商程式庫，我們建議您使用 vcpkg 加以安裝。 vcpkg 支援開放原始碼和專屬程式庫。 vcpkg Windows 目錄中的所有程式庫皆已通過 Visual Studio 2015、Visual Studio 2017 和 Visual Studio 2019 的相容性測試。 在 Windows 和 Linux/macOS 目錄之間，vcpkg 現在支援超過1900的程式庫。 C++ 社群正持續不斷地在兩個目錄中新增更多程式庫。

## <a name="simple-yet-flexible"></a>簡單卻有彈性

您可使用單一命令下載來源並建置程式庫。 vcpkg 本身是開放原始碼專案，可於 GitHub 取得。 您可以用您喜歡的任何方式自訂您的私用 vcpkg 複製。 例如，指定不同的程式庫，或不同于公用目錄中找到的程式庫版本。 您可以在單一電腦上有多個 vcpkg 的複本。 您可以使用慣用的編譯參數，設定每一個程式庫的自訂集合。 每個複製品都是完全獨立的環境，並具有只會在其本身階層執行的專屬 vcpkg.exe 複本。 vcpkg 不會新增至任何環境變數，也不會相依于 Windows 登錄或 Visual Studio。

## <a name="sources-not-binaries"></a>來源，而不是二進位檔

對於 Windows 目錄中的程式庫，vcpkg 會下載來源，而不是二進位檔<sup>1</sup>。 它會使用所能找到的最新版 Visual Studio 來編譯這些來源。 在 c + + 中，很重要的是，您的應用程式程式碼和您使用的任何程式庫都是由相同的編譯器和編譯器版本所編譯。 使用 vcpkg 可排除或至少大幅降低二進位不符的可能性，及其引發的問題。 在以特定編譯器版本為標準的小組中，一個小組成員可以使用 vcpkg 來下載來源並編譯一組二進位檔。 然後他們可以使用 export 命令來壓縮其他小組成員的二進位檔和標頭。 如需詳細資訊，請參閱下面的[匯出編譯的二進位檔和標頭](#export_binaries_per_project)。

您也可以在埠集合中建立具有私用程式庫的 vcpkg 複製品。 新增埠來下載預先建立的二進位檔和標頭。 然後，撰寫只將這些檔案複製到慣用位置的*portfile cmake*檔案。

<sup>1</sup> *注意：某些專屬程式庫無法使用來源。在這些情況下，vcpkg 會下載相容的預建二進位檔。*

## <a name="installation"></a>安裝

從 GitHub 複製 vcpkg 存放庫： [https://github.com/Microsoft/vcpkg](https://github.com/Microsoft/vcpkg) 。 您可以下載到您偏好的任何資料夾位置。 這個位置是 vcpkg*根目錄*。 下載完成後，請在命令介面中變更為該目錄。

在 vcpkg 根目錄中，執行 vcpkg 啟動載入器：

- **`bootstrap-vcpkg.bat`** 時段
- **`./bootstrap-vcpkg.sh`**（Linux、macOS）

在 Linux 或 macOS 上，您可能需要 **`./`** 在接下來的範例中使用，在 vcpkg 命令前面加上前置詞。 請記得從 vcpkg 根目錄執行這些命令。

## <a name="search-the-list-of-available-libraries"></a>搜尋可用的程式庫清單

若要查看有哪些可用的套件，請 **`vcpkg search`** 在命令提示字元中輸入。

此命令會列舉*vcpkg/埠*子資料夾中的控制檔案。 您會看到如下所示的清單：

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

您可以根據模式篩選，例如 **`vcpkg search ta`** ：

```cmd
botan       2.0.1      A cryptography library written in C++11
portaudio   19.0.6.00  PortAudio Portable Cross-platform Audio I/O API P...
taglib      1.11.1-2   TagLib Audio Meta-Data Library
```

### <a name="install-a-library-on-your-local-machine"></a>在本機電腦上安裝程式庫

使用取得程式庫名稱之後 **`vcpkg search`** ，您可以使用 **`vcpkg install`** 來下載並編譯程式庫。 vcpkg 會在*埠*目錄中使用程式庫的 portfile。 如果未指定三元，vcpkg 會針對目標平臺的預設三方安裝和編譯： x86-windows、x64-linux cmake 或 x64-osx cmake。

如果是 Linux 程式庫，vcpkg 取決於本機電腦上安裝的 gcc。 在 macOS 上，vcpkg 會使用 Clang。

當 portfile 指定相依性時，vcpkg 也會下載並安裝它們。 下載之後，vcpkg 會使用程式庫所使用的相同組建系統來建立程式庫。 建議使用 CMake 和 (在 Windows 上) MSBuild 專案，但也支援 MAKE 和任何其他組建系統。 如果 vcpkg 在本機電腦上找不到指定的組建系統，它會下載並安裝它。

```cmd
> vcpkg install boost:x86-windows

The following packages will be built and installed:
    boost:x86-windows
  * bzip2:x86-windows
  * zlib:x86-windows
Additional packages (*) will be installed to complete this operation.
```

若為 CMake 專案，請使用 `CMAKE_TOOLCHAIN_FILE` 讓程式庫可供使用 `find_package()` 。 例如，在 Linux 或 macOS 上：

```cmd
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg/scripts/buildsystems/vcpkg.cmake
```

在 Windows 上：

```cmd
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg\scripts\buildsystems\vcpkg.cmake
```

某些程式庫包括可安裝的選項。 例如，當您搜尋捲曲程式庫時，您也會在方括弧中看到支援的選項清單：

```cmd
> vcpkg search curl
curl                 7.68.0-3         A library for transferring data with URLs
curl[tool]                            Builds curl executable
curl[non-http]                        Enables protocols beyond HTTP/HTTPS/HTTP2
curl[http2]                           HTTP2 support
curl[ssl]                             Default SSL backend
curl[ssh]                             SSH support via libssh2
curl[openssl]                         SSL support (OpenSSL)
curl[winssl]                          SSL support (Secure Channel / "WinSSL")
curl[mbedtls]                         SSL support (mbedTLS)
curl[sectransp]                       SSL support (sectransp)
curl[c-ares]                          c-ares support
curl[sspi]                            SSPI support
curl[brotli]                          brotli support (brotli)
curlpp               2018-06-15-3     C++ wrapper around libcURL
```

在此情況下，方括弧 **`[`** 和 **`]`** 是常值，而不是元字元。

您可以指定要在命令列上安裝的特定選項。 例如，若要使用 Windows 的預設 SSL 後端安裝捲曲的程式庫，請使用 **`vcpkg install curl[ssl]:x86-windows`** 命令。 如有需要，此命令會安裝任何必要的必要條件，包括核心程式庫：

```cmd
> vcpkg list
curl:x86-windows            7.68.0-3   A library for transferring data with URLs
curl[non-http]:x86-windows             Enables protocols beyond HTTP/HTTPS/HTTP2
curl[ssl]:x86-windows                  Default SSL backend
curl[sspi]:x86-windows                 SSPI support
curl[winssl]:x86-windows               SSL support (Secure Channel / "WinSSL")
zlib:x86-windows            1.2.11-6   A compression library
```

## <a name="list-the-libraries-already-installed"></a>列出已安裝的程式庫

安裝一些程式庫之後，您可以使用 **`vcpkg list`** 來查看您擁有的內容：

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

執行 **`vcpkg integrate install`** 以設定 Visual Studio，以每個使用者為基礎來尋找所有 vcpkg 標頭檔和二進位檔。 不需要手動編輯 VC + + 目錄路徑。 如果您有多個 vcpkg 的複製，則執行此命令的複製會變成新的預設位置。

現在您只要輸入資料夾/標頭，就可以 #include 標頭，而自動完成可協助您。 不需要任何其他步驟即可連結至程式庫或新增專案參考。 下圖顯示 Visual Studio 如何找到 azure-storage-cpp 標頭。 vcpkg 會將其標頭放在 */installed* 子資料夾中，依目標平台分割資料。 下圖顯示程式庫 */was* 子資料夾中的 Include 檔清單：

![vcpkg 和 IntelliSense](media/vcpkg-intellisense.png "vcpkg 和 IntelliSense")

### <a name="per-project"></a>每個專案

如果您需要使用的程式庫版本與 active vcpkg 實例中的版本不同，請遵循下列步驟：

1. 建立新的 vcpkg 複製品
1. 修改程式庫的連接埠檔案以取得您需要的版本
1. 執行 **`vcpkg install <library>`** 。
1. 使用 **`vcpkg integrate project`** 建立以每個專案為基礎參考該程式庫的 NuGet 套件。

## <a name="integrate-with-visual-studio-code-linuxmacos"></a>與 Visual Studio Code 整合（Linux/macOS）

執行 **`vcpkg integrate install`** 以在 Linux/macOS 上設定 Visual Studio Code。 此命令會設定 vcpkg 登記的位置，並在原始檔上啟用 IntelliSense。

## <a name="target-linux-from-windows-via-wsl"></a>透過 WSL 從 Windows 將 Linux 設為目標

您可以使用適用于 Linux 的 Windows 子系統或 WSL，在 Windows 電腦上產生 Linux 二進位檔。 依照指示[在 Windows 10 上設定 WSL](/windows/wsl/install-win10)。 然後，使用[適用于 Linux 的 Visual Studio 擴充](https://blogs.msdn.microsoft.com/vcblog/2017/02/08/targeting-windows-subsystem-for-linux-from-visual-studio/)功能進行設定。 您可以將適用于 Windows 和 Linux 的所有建立程式庫放入相同的資料夾中。 它們可以從 Windows 和 WSL 存取。

## <a name="export-compiled-binaries-and-headers"></a><a name="export_binaries_per_project"></a> 匯出編譯的二進位檔和標頭

讓小組中的每個人都能下載並建立通用程式庫是沒有效率的。 單一小組成員可以使用 **`vcpkg export`** 命令來建立二進位檔和標頭的一般 zip 檔案，或 NuGet 套件。 然後，很容易就能與其他小組成員共用。

## <a name="updateupgrade-installed-libraries"></a>更新/升級安裝的程式庫

公用目錄會與最新版本的程式庫保持在最新狀態。 若要判斷哪些本機程式庫已過期，請使用 **`vcpkg update`** 。 當您準備好要將埠集合更新為最新版本的公用目錄時，請執行 **`vcpkg upgrade`** 命令。 它會自動下載並重建任何或所有已安裝的程式庫（已過期）。

根據預設，此 **`vcpkg upgrade`** 命令只會列出已過期的程式庫，不會將它們升級。 若要實際升級程式庫，請使用 **`--no-dry-run`** 選項。

```cmd
> vcpkg upgrade --no-dry-run
```

### <a name="upgrade-options"></a>升級選項

- **`--no-dry-run`** 執行升級;當未指定時，命令只會列出過期的封裝。
- **`--keep-going`** 繼續安裝套件，即使其中一個失敗。
- **`--triplet <t>`** 為不合格的封裝設定預設的三個。
- **`--vcpkg-root <path>`** 請指定要使用的 vcpkg 目錄，而不是目前的目錄或工具目錄。

### <a name="upgrade-example"></a>升級範例

下列範例示範如何只升級指定的程式庫。 vcpkg 會視需要自動提取相依性。

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

輸入 **`vcpkg remove`** 以移除已安裝的媒體櫃。 如果有任何其他程式庫相依于此，系統會要求您使用重新執行命令 **`--recurse`** ，這會導致移除所有下游程式庫。

## <a name="customize-vcpkg"></a>自訂 vcpkg

您可以用任何喜歡的方式修改您的 vcpkg 複製品。 您甚至可以建立多個 vcpkg 複製品，然後修改每個複本中的 portfile。 這是取得特定程式庫版本或指定特定命令列參數的簡單方式。 例如，企業中的個別開發人員群組可能會處理具有其群組特有相依性的軟體。 解決的方法是為每個小組設定 vcpkg 的複本。 然後，修改複本以下載程式庫版本，並設定每個小組所需的編譯參數。

## <a name="update-vcpkg"></a>更新 vcpkg

GitHub 上的 vcpkg 套件管理員會定期更新。 若要將 vcpkg 的複製更新為最新版本，請從 vcpkg 根目錄執行 **`git pull`** 。 此命令會將您的 vcpkg 複本與 GitHub 上的版本同步。 下載完成之後，請再次執行啟動載入器。 啟動載入器會重建 vcpkg 程式，但會將已安裝的程式庫保留在原處。

## <a name="uninstall-vcpkg"></a>將 vcpkg 解除安裝

若要卸載 vcpkg，只要刪除 vcpkg 目錄即可。 刪除此目錄會卸載 vcpkg 散發，以及 vcpkg 已安裝的所有程式庫。

## <a name="send-feedback-about-vcpkg"></a>傳送 vcpkg 的相關意見反應

使用 **`vcpkg contact --survey`** 命令將關於 vcpkg 的意見反應傳送給 Microsoft，包括功能的錯誤報表和建議。

## <a name="the-vcpkg-folder-hierarchy"></a>vcpkg 資料夾階層

所有 vcpkg 功能與資料皆完全獨立於單一目錄階層中，稱為「執行個體」。 沒有登錄設定或環境變數。 您可以在一部電腦上擁有任意數目的 vcpkg 實例，而且它們不會互相干擾。

vcpkg 執行個體的內容如下：

- buildtrees-包含用來建立每個程式庫之來源的子資料夾
- 檔-檔和範例
- 下載-任何已下載工具或來源的快取複本。 當您執行 install 命令時，vcpkg 會先在這裡進行搜尋。
- 已安裝-包含每個已安裝程式庫的標頭和二進位檔。 當您與 Visual Studio 整合時，基本上就是告訴它將此資料夾新增至其搜尋路徑。
- 封裝-安裝之間暫存的內部資料夾。
- 埠-描述目錄中每個程式庫、其版本，以及下載位置的檔案。 如有需要可新增自己的連接埠。
- 腳本-vcpkg 使用的腳本（CMake、PowerShell）。
- toolsrc-vcpkg 和相關元件的 c + + 原始程式碼
- triplet-包含每個支援的目標平臺（例如，x86-windows 或 x64-uwp）的設定。

## <a name="command-line-reference"></a>命令列參考

|Command|說明|
|---------|---------|
|**`vcpkg search [pat]`**|搜尋可安裝的套件|
|**`vcpkg install <pkg>...`**|安裝套件|
|**`vcpkg remove <pkg>...`**|解除安裝套件|
|**`vcpkg remove --outdated`**|將過期的套件解除安裝|
|**`vcpkg list`**|列出安裝的套件|
|**`vcpkg update`**|顯示要更新的套件清單|
|**`vcpkg upgrade`**|重建所有過期的套件|
|**`vcpkg hash <file> [alg]`**|依特定演算法雜湊檔案，預設為 SHA512|
|**`vcpkg integrate install`**|讓所有使用者皆可使用安裝的套件。 第一次使用需要有管理員權限|
|**`vcpkg integrate remove`**|移除全使用者整合|
|**`vcpkg integrate project`**|產生參考 NuGet 套件供個別 VS 專案使用|
|**`vcpkg export <pkg>... [opt]...`**|匯出套件|
|**`vcpkg edit <pkg>`**|開啟連接埠以進行編輯 (使用 %EDITOR%，預設為 'code')|
|**`vcpkg create <pkg> <url> [archivename]`**|建立新套件|
|**`vcpkg cache`**|列出快取的已編譯套件|
|**`vcpkg version`**|顯示版本資訊|
|**`vcpkg contact --survey`**|顯示要傳送意見反應的連絡人資訊。|

### <a name="options"></a>選項

|選項|Description|
|---------|---------|
|**`--triplet <t>`**|指定目標架構 triplet。 （預設值： `%VCPKG_DEFAULT_TRIPLET%` ，另請參閱 **`vcpkg help triplet`** ）|
|**`--vcpkg-root <path>`**|指定 vcpkg 根目錄 (預設：`%VCPKG_ROOT%`)|
