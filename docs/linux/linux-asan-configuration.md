---
title: 將 Linux 專案設定為使用 Address Sanitizer
description: 描述如何將 Visual Studio 中的 C++ Linux 專案設定為使用 Address Sanitizer。
ms.date: 06/07/2019
ms.openlocfilehash: da7197981a431becfc1231dae96f7542062de675
ms.sourcegitcommit: b3d19b5f59f3a5d90c24f9f16c73bad4c5eb6944
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71195904"
---
# <a name="configure-linux-projects-to-use-address-sanitizer"></a>將 Linux 專案設定為使用 Address Sanitizer

在 Visual Studio 2019 16.1 版中，AddressSanitizer (ASan) 支援已整合到 Linux 專案。 您可以針對以 MSBuild 為基礎的 Linux 專案和 CMake 專案啟用 ASan。 它可在遠端 Linux 系統和適用於 Linux 的 Windows 子系統 (WSL) 上運作。

## <a name="about-asan"></a>關於 ASan

ASan 是 C/C++ 的執行階段記憶體錯誤偵測器，可捕捉下列錯誤：

- 釋放後使用 (懸置指標參考)
- 堆積緩衝區溢位
- 堆疊緩衝區溢位
- 傳回後使用
- 設定範圍後使用
- 初始化順序錯誤

當 ASan 偵測到錯誤時，它會立即停止執行。 如果您在偵錯工具中執行已啟用 ASan 的程式，您會看到一則訊息，其中描述錯誤類型、記憶體位址，以及原始程式檔中發生錯誤的位置：

   ![ASan 錯誤訊息](media/asan-error.png)

您也可以在輸出視窗的 [偵錯] 窗格中檢視完整的 ASan 輸出 (包括已配置/解除配置損毀記憶體的位置)。

## <a name="enable-asan-for-msbuild-based-linux-projects"></a>針對以 MSBuild 為基礎的 Linux 專案啟用 ASan

> [!NOTE]
> 從 Visual Studio 2019 16.4 版開始，您可以透過設定**屬性** >   >  **C/C++** **Enable Address Sanitizer**來啟用 Linux 專案的 AddressSanitizer。

若要針對以 MSBuild 為基礎的 Linux 專案啟用 ASan，請以滑鼠右鍵按一下 [方案總管] 中的專案，然後選取 [屬性]。 接下來，巡覽至 [組態屬性] > [C/C++] > [Sanitizer]。 ASan 會透過編譯器和連結器旗標來啟用，且需要重新編譯您的專案才能運作。

![針對 MSBuild 專案啟用 ASan](media/msbuild-asan-prop-page.png)

您可以巡覽至 [組態屬性] > [偵錯] > [AddressSanitizer 執行階段旗標] 來來傳遞選擇性 ASan 執行階段旗標。 請按一下向下箭號來新增或移除旗標。

![設定 ASan 執行階段旗標](media/msbuild-asan-runtime-flags.png)

## <a name="enable-asan-for-visual-studio-cmake-projects"></a>針對 Visual Studio 的 CMake 專案中啟用 ASan

若要針對 CMake 啟用 ASan，請以滑鼠右鍵按一下 [方案總管] 中的 CMakeLists.txt 檔案，然後選擇 [專案的 CMake 設定]。

請確定您已在該對話方塊的左窗格中選取了 Linux 組態 (例如 **Linux-Debug**)：

![Linux 偵錯組態](media/linux-debug-configuration.png)

ASan 選項位於 [一般] 下方。 請以分號分隔的 "flag=value" 格式輸入 ASan 執行階段旗標。

![Linux 偵錯組態](media/cmake-settings-asan-options.png)

## <a name="install-the-asan-debug-symbols"></a>安裝 ASan 偵錯符號

若要啟用 ASan 診斷，您必須在遠端 Linux 電腦或 WSL 安裝上安裝其偵錯符號 (libasan-dbg)。 您載入的 libasan-dbg 版本取決於 Linux 機器上所安裝 GCC 版本：

|**ASan 版本**|**GCC 版本**|
| --- | --- |
|libasan0|gcc-4.8|
|libasan2|gcc-5|
|libasan3|gcc-6|
|libasan4|gcc-7|
|libasan5|gcc-8|

您可以使用此命令來判斷您擁有哪一個版本的 GCC：

```bash
gcc --version
```

若要檢視您需要的 libasan-dbg 版本，請執行您的程式，然後查看 [輸出] 視窗的 [偵錯] 窗格。 已載入的 ASan 版本對應於 Linux 電腦上所需的 libasan-dbg 版本。 您可以在該視窗中使用 **Ctrl + F** 來搜尋 "libasan"。 例如，如果有 libasan4，您會看到下列這行：

```Output
Loaded '/usr/lib/x86_64-linux-gnu/libasan.so.4'. Symbols loaded.
```

您可以利用下列命令，在使用 apt 的 Linux 發行版本上安裝 ASan 偵錯位元。 此命令會安裝第 4 版：

```bash
sudo apt-get install libasan4-dbg
```

如果啟用了 ASan，Visual Studio 就會在 [輸出] 視窗的 [偵錯] 窗格頂端提示您安裝 ASan 偵錯符號。
