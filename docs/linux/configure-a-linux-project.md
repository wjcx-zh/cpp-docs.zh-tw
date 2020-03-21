---
title: 在 Visual Studio 中設定 C++ Linux 專案
ms.date: 06/11/2019
ms.assetid: 4d7c6adf-54b9-4b23-bd23-5de0c825b768
ms.openlocfilehash: 853afc39412ecd07f3ec6c9ad42d0ab599bfe17e
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077731"
---
# <a name="configure-a-linux-project"></a>設定 Linux 專案

::: moniker range="vs-2015"

Visual Studio 2017 及更新版本支援 Linux。

::: moniker-end

本主題描述如何設定 C++ Linux 專案，如[在 Visual Studio 中建立新的 C++ Linux 專案](create-a-new-linux-project.md)所述。 針對 CMake Linux 專案，請參閱[設定 Linux CMake 專案](cmake-linux-project.md)。

您可以設定 Linux 專案，以實體 Linux 機器、虛擬機器，或[適用於 Linux 的 Windows 子系統](/windows/wsl/about) (WSL) 為目標。

::: moniker range="vs-2019"

**Visual Studio 2019 16.1 版**：

- 以 WSL 為目標時，可避免以遠端 Linux 系統為目標時，建置和 IntelliSense 所需的複製作業。

- 您可以指定不同的 Linux 目標來進行建置和偵錯。

::: moniker-end

## <a name="general-settings"></a>一般設定

若要檢視組態選項，請選取 [專案] > [屬性] 功能表，或在 [方案總管] 中以滑鼠右鍵按一下專案，然後從操作功能表中選取 [屬性]。 [一般] 設定隨即出現。

![一般設定](media/settings_general.png)

預設會建置可執行檔 (.out)。 若要建置靜態或動態程式庫，或使用現有 Makefile，請使用 [組態類型] 設定。

如需屬性頁中設定的詳細資訊，請參閱 [Linux 專案屬性頁參考](prop-pages-linux.md)。

## <a name="remote-settings"></a>遠端設定

若要變更與遠端 Linux 電腦有關的設定，請設定出現在 [[一般](prop-pages/general-linux.md)] 下的遠端設定。

- 若要指定遠端目標 Linux 電腦，請使用 [遠端組建電腦] 項目。 這可讓您選取其中一個先前建立的連線。 若要建立新的項目，請參閱[連線到遠端 Linux 電腦](connect-to-your-remote-linux-computer.md)一節。

   ![組建電腦](media/remote-build-machine-vs2019.png)

   ::: moniker range="vs-2019"

   **Visual Studio 2019 16.1 版**：目標為適用于 Linux 的 Windows 子系統，按一下**平臺工具**組的向下箭號，然後選擇 [ **WSL_1_0**]。 其他遠端選項會消失，預設 WSL 殼層的路徑便會出現在其位置：

   ![WSL 組建電腦](media/wsl-remote-vs2019.png)

   如果您有並存的 WSL 安裝，則可以在此處指定不同的路徑。 如需管理多個發行版本的詳細資訊，請參閱[管理和設定適用於 Linux 的 Windows 子系統](/windows/wsl/wsl-config#set-a-default-distribution)。

   您可以在 [設定**屬性**] > [**調試**程式] 頁面上，指定不同的偵錯工具目標。

   ::: moniker-end

- [遠端組建根目錄] 決定在遠端 Linux 電腦上建置專案的根目錄位置。 除非進行變更，否則這會預設為 **~/projects**。

- [遠端組建專案目錄] 是在遠端 Linux 電腦上建置這個特定專案的位置。 這會預設為上面所設定之根目錄下的 **$(RemoteRootDir)/$(ProjectName)** ，其會擴充到目前專案後命名的目錄。

> [!NOTE]
> 若要變更預設 C 和 C++ 編譯器，或是用來建置專案的連結器和封存工具，請使用 [C/C++] > [一般] 區段和 [連結器] > [一般] 區段中的適當項目。 例如，您可以指定特定版本的 GCC 或 Clang。 如需詳細資訊，請參閱 [C/C++ 屬性 (Linux C++) ](prop-pages/c-cpp-linux.md)和[連結器屬性 (Linux C++)](prop-pages/linker-linux.md)。

## <a name="copy-sources-remote-systems-only"></a>複製來源 (僅限遠端系統)

::: moniker range="vs-2019"

本節不適用於以 WSL 為目標時。

::: moniker-end

在遠端系統上建置時，會將開發電腦上的來源檔案複製到 Linux 電腦，並在該處進行編譯。 根據預設，Visual Studio 專案中的所有來源都會複製到上方設定中所設定的位置。 不過，也可以在清單中新增其他來源，或者完全關閉複製來源，後者是 Makefile 專案的預設值。

- [要複製的來源] 決定將哪些來源複製到遠端電腦。 根據預設， **\@(SourcesToCopyRemotely)** 預設為專案中所有的原始程式碼檔案，但不包括任何資產/資源檔案，例如影像。

- [複製來源] 可以開啟和關閉，以啟用和停用將原始程式檔複製到遠端電腦。

- [要複製的其他來源] 可讓您新增將複製到遠端系統的其他原始程式檔。 您可以指定分號分隔清單，也可以使用 **:=** 語法來指定要使用的本機和遠端名稱︰

`C:\Projects\ConsoleApplication1\MyFile.cpp:=~/projects/ConsoleApplication1/ADifferentName.cpp;C:\Projects\ConsoleApplication1\MyFile2.cpp:=~/projects/ConsoleApplication1/ADifferentName2.cpp;`

## <a name="build-events"></a>建置事件

因為所有編譯都是在遠端電腦 (或 WSL) 上進行，所以已在 [專案屬性] 的 [建置事件] 區段中新增數個額外建置事件。 這些是 [遠端建置前事件]、[遠端連結前事件] 和 [遠端建置後事件]，並且在程序中的個別步驟之前或之後發生於遠端電腦上。

![建置事件](media/settings_buildevents.png)

## <a name="intellisense-for-headers-on-remote-systems"></a><a name="remote_intellisense"></a> 適用於遠端系統標頭的 IntelliSense

當您在 [連線管理員] 中新增連線時，Visual Studio 會自動偵測遠端系統上編譯器的 Include 目錄。 Visual Studio 接著會壓縮這些檔案，並將其複製到本機 Windows 電腦上的目錄中。 之後，每當您在 Visual Studio 或 CMake 專案中使用該連線時，這些目錄中的標頭就會用來提供 IntelliSense。

> [!NOTE]
> 在 Visual Studio 2019 16.5 版和更新版本中，遠端標頭複本已經過優化。 在開啟 Linux 專案或為 Linux 目標設定 CMake 時，現在會視需要複製標頭。 複製會根據專案的指定編譯器，以每個專案為基礎發生在背景中。 如需詳細資訊，請參閱[Linux IntelliSense 的正確性和效能改進](https://devblogs.microsoft.com/cppblog/improvements-to-accuracy-and-performance-of-linux-intellisense/)。

這項功能取決於已安裝 ZIP 的 Linux 電腦。 您可以使用這個 apt-get 命令來安裝 ZIP：

```cmd
sudo apt install zip
```

若要管理標頭快取，請巡覽至 [工具] > [選項]、[跨平台] > [連線管理員] > [遠端標頭 IntelliSense 管理員]。 若要在 Linux 電腦上進行變更後更新標頭快取，請選取遠端連線，然後選取 [更新]。 選取 [刪除] 來移除標頭，但不刪除連線本身。 選取 [探索]，在**檔案總管**中開啟本機目錄。 將此資料夾視為唯讀。 若要針對 Visual Studio 2017 15.3 版之前建立的現有連線下載標頭，請選取連線，然後選取 [下載]。

::: moniker range="vs-2017"

![遠端標頭 IntelliSense](media/remote-header-intellisense.png)

::: moniker-end

::: moniker range="vs-2019"

![遠端標頭 IntelliSense](media/connection-manager-vs2019.png)

您可以啟用記錄來協助針對問題進行疑難排解：

![遠端記錄](media/remote-logging-vs2019.png)

::: moniker-end

## <a name="see-also"></a>另請參閱

[Set compiler and build properties](../build/working-with-project-properties.md) (設定編譯器及組建屬性)<br/>
[C++ 一般屬性 (Linux C++)](../linux/prop-pages/general-linux.md)<br/>
[VC++ 目錄 (Linux C++)](../linux/prop-pages/directories-linux.md)<br/>
[複製來源專案屬性 (Linux C++)](../linux/prop-pages/copy-sources-project.md)<br/>
[建置事件屬性 (Linux C++)](../linux/prop-pages/build-events-linux.md)
