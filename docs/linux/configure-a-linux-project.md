---
title: 在 Visual Studio 中設定 C++ Linux 專案 | Microsoft Docs
ms.custom: ''
ms.date: 09/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-linux
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 4d7c6adf-54b9-4b23-bd23-5de0c825b768
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: fbc0674a7659ffccd5ab5c655f74167acebdca97
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43895197"
---
# <a name="configure-a-linux-project"></a>設定 Linux 專案

本主題說明如何在 Visual Stuidio 中設定 C++ Linux 專案。 如需 Visual Studio 中 CMake Linux 專案的相關資訊，請參閱[設定 Linux CMake 專案](cmake-linux-project.md)。

## <a name="general-settings"></a>一般設定

使用 Visual Studio，可以設定 Linux 專案的各種選項。  若要檢視這些選項，請選取 [專案] > [屬性] 功能表，或在**方案總管**中以滑鼠右鍵按一下專案，然後從操作功能表中選取 [屬性]。 [一般] 設定隨即出現。

![一般組態](media/settings_general.png)

預設會使用此工具來建置可執行檔 (.out)。  若要建置靜態或動態程式庫，或使用現有 Makefile，請使用 [組態類型] 選項。

## <a name="remote-settings"></a>遠端設定

若要變更與遠端的 Linux 電腦有關的設定，請設定出現在 [一般] 設定中的遠端選項：

- 若要變更目標 Linux 電腦，請使用 [遠端組建電腦] 項目。  這可讓您選取其中一個先前建立的連線。  若要建立新的項目，請參閱[連線到遠端 Linux 電腦](connect-to-your-remote-linux-computer.md)小節。

- [遠端組建根目錄] 決定在遠端 Linux 電腦上建置專案的根目錄位置。  除非進行變更，否則這會預設為 **~/projects**。

- [遠端組建專案目錄] 是在遠端 Linux 電腦上建置這個特定專案的位置。  這會預設為上面所設定之根目錄下的 **$(RemoteRootDir)/$(ProjectName)**，其會擴充到目前專案後命名的目錄。

> [!NOTE]
> 若要變更預設 C 和 C++ 編譯器，或是用來建置專案的連結器和封存工具，請使用 [C/C++] > [一般] 區段和 [連結器] > [一般] 區段中的適當項目。  這些可以設定成使用特定版本的 GCC，甚至 Clang 編譯器 (舉例來說)。

## <a name="include-directories-and-intellisense-support"></a>Include 目錄和 IntelliSense 支援

**Visual Studio 2017 15.6 版和更早版本：** 根據預設，Visual Studio 不會包含 Linux 電腦中的任何系統層級包含檔案。  例如，Visual Studio 中沒有 **/usr/include** 目錄中的項目。
如需完整 [IntelliSense](/visualstudio/ide/using-intellisense) 支援，您必須將這些檔案複製到開發電腦上的某個位置，並將 Visual Studio 指向這個位置。  其中一個選項是使用 scp (安全複製) 來複製檔案。  在 Windows 10 上，您可以使用 [Bash on Windows](https://msdn.microsoft.com/commandline/wsl/about) 來執行 scp。  針對舊版 Windows，您將使用 [PSCP (PuTTY Secure Copy)](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) 這類項目。

使用與下列類似的命令，即可複製檔案：

`scp -r linux_username@remote_host:/usr/include .`

請務必取代上方適合您自己環境的 **linux_username** 和 **remote_host** 值。

複製檔案之後，請使用 [專案屬性] 中的 [VC++ 目錄] 項目，告訴 Visual Studio 在何處找到剛剛複製的其他包含檔案。

![VC++ 目錄](media/settings_directories.png)

**Visual Studio 2017 15.7 和更新版本：** 請參閱[管理 IntelliSense 的遠端標頭](#remote_intellisense)。

## <a name="copy-sources"></a>複製來源

建置時，會將開發電腦上的來源檔案複製到 Linux 電腦，並在該處進行編譯。  根據預設，Visual Studio 專案中的所有來源都會複製到上方設定中所設定的位置。  不過，也可以在清單中新增其他來源，或者完全關閉複製來源，後者是 Makefile 專案的預設值。

- [要複製的來源] 決定將哪些來源複製到遠端電腦。  根據預設，**\@(SourcesToCopyRemotely)** 預設為專案中所有的原始程式碼檔案，但不包括任何資產/資源檔案，例如影像。

- [複製來源] 可以開啟和關閉，以啟用和停用將原始程式檔複製到遠端電腦。

- [要複製的其他來源] 可讓您新增將複製到遠端系統的其他原始程式檔。  您可以指定分號分隔清單，也可以使用 **:=** 語法來指定要使用的本機和遠端名稱︰

`C:\Projects\ConsoleApplication1\MyFile.cpp:=~/projects/ConsoleApplication1/ADifferentName.cpp;C:\Projects\ConsoleApplication1\MyFile2.cpp:=~/projects/ConsoleApplication1/ADifferentName2.cpp;`

## <a name="build-events"></a>建置事件

因為所有編譯都是在遠端電腦上進行，所以已在 [專案屬性] 的 [建置事件] 區段中新增數個額外建置事件。  這些是 [遠端建置前事件]、[遠端連結前事件] 和 [遠端建置後事件]，並且在程序中的個別步驟之前或之後發生於遠端電腦上。

![建置事件](media/settings_buildevents.png)

## <a name="remote_intellisense"></a> 適用於遠端標頭的 IntelliSense (Visual Studio 2017 15.7 版和更新版本)

當您在 [連線管理員] 中新增連線時，Visual Studio 會自動偵測遠端系統上編譯器的 Include 目錄。 Visual Studio 接著會壓縮這些檔案，並將其複製到本機 Windows 電腦上的目錄中。 之後，每當您在 Visual Studio 或 CMake 專案中使用該連線時，這些目錄中的標頭就會用來提供 IntelliSense。

這項功能取決於已安裝 ZIP 的 Linux 電腦。 您可以使用這個 apt-get 命令來安裝 ZIP：

```cmd
apt install zip
```

若要管理標頭快取，請巡覽至 [工具] > [選項]、[跨平台] > [連線管理員] > [遠端標頭 IntelliSense 管理員]。 若要在 Linux 電腦上進行變更後更新標頭快取，請選取遠端連線，然後選取 [更新]。 選取 [刪除] 來移除標頭，但不刪除連線本身。 選取 [探索]，在**檔案總管**中開啟本機目錄。 將此資料夾視為唯讀。 若要針對 15.3 版之前建立的現有連線下載標頭，請選取連線，然後選取 [下載]。

![遠端標頭 IntelliSense](media/remote-header-intellisense.png)

## <a name="see-also"></a>另請參閱

[使用專案屬性](../ide/working-with-project-properties.md)  
[C++ 一般屬性 (Linux C++)](../linux/prop-pages/general-linux.md)  
[VC++ 目錄 (Linux C++)](../linux/prop-pages/directories-linux.md)  
[複製來源專案屬性 (Linux C++)](../linux/prop-pages/copy-sources-project.md)  
[建置事件屬性 (Linux C++)](../linux/prop-pages/build-events-linux.md)