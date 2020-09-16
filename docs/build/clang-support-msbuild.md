---
title: Visual Studio Visual Studio 專案中的 Clang/LLVM 支援
ms.date: 06/02/2020
ms.description: Configure a Visual Studio MSBuild project to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ MSBuild projects
ms.openlocfilehash: a34b8931fa344071d319770ef1c55fc46d27e1e2
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686341"
---
# <a name="clangllvm-support-in-visual-studio-projects"></a>Visual Studio 專案中的 Clang/LLVM 支援

::: moniker range="<=vs-2017"

Visual Studio 2019 提供 CMake 和 MSBuild 專案的 Clang 支援。

::: moniker-end

::: moniker range="vs-2019"

您可以使用 Visual Studio 2019 16.2 版搭配 Clang，來編輯、建立及偵測以 Windows 或 Linux 為目標 (MSBuild) 的 c + + Visual Studio 專案。

## <a name="install"></a>安裝

為了 Visual Studio 中的最佳 IDE 支援，我們建議使用適用于 Windows 的最新 Clang 編譯器工具。 如果您還沒有這些專案，可以開啟 Visual Studio 安裝程式，然後選擇 [**使用 c + +** 選擇性元件的桌面開發] 下的 [**適用于 Windows 的 c + + Clang 工具**] 來安裝它們。 如果您想要在電腦上使用現有的 Clang 安裝，請選擇 [ **c + + Clang-cl for 適用于 v142 build tools]。** 選用元件。 Microsoft c + + 標準程式庫目前至少需要 Clang 8.0.0;Clang 的配套版本將會自動更新，以在 Microsoft 的標準程式庫實施中保持最新的更新。

![已選取 [個別元件] 索引標籤的 Visual Studio 安裝程式的螢幕擷取畫面，並顯示 C + + 加號 Clang 元件。](media/clang-install-vs2019.png)

## <a name="configure-a-windows-project-to-use-clang-tools"></a>設定 Windows 專案以使用 Clang 工具

若要設定 Visual Studio 專案以使用 Clang，請在 **方案總管** 的專案節點上按一下滑鼠右鍵，然後選擇 [ **屬性**]。 一般而言，您應該先選擇對話方塊頂端的 **所有** 設定。 然後，在 **[一般**  >  **平臺工具**組] 下，選擇 [ **LLVM () clang** ]，然後選擇 **[確定]**。

![[屬性頁] 對話方塊的螢幕擷取畫面，其中已選取 [一般] > [一般]，並已醒目提示 [平臺工具組] 和 [L V] (clang c L) 選項。](media/clang-msbuild-prop-page.png)

如果您使用 Visual Studio 隨附的 Clang 工具，則不需要其他步驟。 在 Windows 專案中，Visual Studio 預設會以 [Clang-cl](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf) 模式叫用 Clang，並使用標準程式庫的 Microsoft 實作為連結。 根據預設， **clang-cl.exe**位於 *% VCINSTALLDIR% \\ tools \\ Llvm \\ bin \\ *和 *% VCINSTALLDIR% \\ tools \\ Llvm \\ x64 \\ bin \\ *中。

如果您使用自訂的 Clang 安裝，您可以修改**專案**  >  **屬性**  >  **VC + + 目錄**設定  >  **屬性**  >  **可執行檔目錄**，方法是新增自訂 Clang 安裝根目錄作為第一個目錄，或變更屬性的值 `LLVMInstallDir` 。 如需詳細資訊，請參閱 [設定自訂的 LLVM 位置](#custom_llvm_location) 。

## <a name="configure-a-linux-project-to-use-clang-tools"></a>設定 Linux 專案以使用 Clang 工具

針對 Linux 專案，Visual Studio 使用 Clang GCC 相容前端。 專案屬性和幾乎所有編譯器旗標都相同

若要將 Visual Studio Linux 專案設定為使用 Clang：

1. 在 **方案總管** 中的專案節點上按一下滑鼠右鍵，然後選擇 [ **屬性**]。
1. 一般而言，您應該先選擇對話方塊頂端的 **所有** 設定。
1. 在 **[一般** > **平臺工具**組] 下，如果您使用 Windows 子系統 Linux 版，請選擇 **WSL_Clang_1_0** ，如果您使用的是遠端電腦或 VM，請選擇 **Remote_Clang_1_0** 。
1. 按下 **[確定]**。

![主控台應用程式 clang Visual Studio 2019 [屬性頁] 對話方塊的螢幕擷取畫面，其中已選取 [一般] > 的設定屬性，以及反白顯示 [平臺工具組] 和 [L V] (clang c L) 選項。](media/clang-msbuild-prop-page.png)

在 Linux 上，Visual Studio 預設會使用它在 PATH 環境屬性中遇到的第一個 Clang 位置。 如果您使用自訂的 Clang 安裝，則必須變更屬性的值， `LLVMInstallDir` 否則請在 [**專案**屬性] 的 [  >  **Properties**  >  **VC + + 目錄**設定  >  **屬性**  >  **可執行檔] 目錄**下替代路徑。 如需詳細資訊，請參閱 [設定自訂的 LLVM 位置](#custom_llvm_location) 。

## <a name="set-a-custom-llvm-location"></a><a name="custom_llvm_location"></a> 設定自訂 LLVM 位置

您可以建立 *.props* 檔案，並將該檔案新增至任何專案的根資料夾，以針對一或多個專案設定 LLVM 的自訂路徑。 您可以將它加入至 [根方案] 資料夾，以將它套用至方案中的所有專案。 檔案看起來應該像這樣 (但要將實際的路徑取代) ：

```xml
<Project>
  <PropertyGroup>
    <LLVMInstallDir>c:\MyLLVMRootDir</LLVMInstallDir>
  </PropertyGroup>
</Project>
```

## <a name="set-additional-properties-edit-build-and-debug"></a>設定其他屬性、編輯、建立和調試

設定 Clang 設定之後，請在專案節點上再次以滑鼠右鍵按一下，然後選擇 [ **重載專案**]。 您現在可以使用 Clang 工具來建立和調試專案。 Visual Studio 會偵測到您正在使用 Clang 編譯器，並提供 IntelliSense、醒目提示、導覽和其他編輯功能。 錯誤和警告會顯示在 **輸出視窗**中。 Clang 設定的專案屬性頁面與 MSVC 的專案屬性頁面非常類似，不過有些與編譯器相依的功能（例如 [編輯後繼續]）無法用於 Clang 設定。 若要設定屬性頁中無法使用的 Clang 編譯器或連結器選項，您可以在 [設定**屬性**  >  **C/c + + (或連結器) **  >  **命令列**  >  **額外選項**] 下，以手動方式將它加入屬性頁。

在進行調試時，您可以使用中斷點、記憶體和資料視覺效果，以及大部分的其他調試功能。  

![Clang 調試](media/clang-debug-msbuild.png)

::: moniker-end
