---
title: Visual Studio Visual Studio 專案中的 Clang/LLVM 支援
ms.date: 08/30/2019
ms.description: Configure a Visual Studio MSBuild project to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ MSBuild projects
ms.openlocfilehash: f0142c2583eeef10f159cd83451e1f3866990b75
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222627"
---
# <a name="clangllvm-support-in-visual-studio-projects"></a>Visual Studio 專案中的 Clang/LLVM 支援

::: moniker range="<=vs-2017"

Visual Studio 2019 中提供 CMake 和 MSBuild 專案的 Clang 支援。

::: moniker-end

::: moniker range="vs-2019"

您可以使用 Visual Studio 2019 16.2 版搭配 Clang 來編輯、建立和 debug C++以 Windows 或 Linux 為目標的 Visual Studio 專案 (MSBuild)。

## <a name="install"></a>安裝

如需 Visual Studio 中的最佳 IDE 支援, 我們建議使用適用于 Windows 的最新 Clang 編譯器工具。 如果您還沒有這些專案, 您可以開啟 Visual Studio 安裝程式, 然後在 [**桌面開發C++**  ] 下選擇 [ **C++** 使用選用元件的 Clang 工具] 來安裝它們。 如果您想要在電腦上使用現有的 Clang 安裝, 請選擇 **C++ Clang-cl for 適用于 v142 build tools。** 選擇性元件。 Microsoft C++標準程式庫目前至少需要 Clang 8.0.0;配套的 Clang 版本將會自動更新, 以在標準程式庫的 Microsoft 實施中隨時更新。 

![Clang 元件安裝](media/clang-install-vs2019.png)

## <a name="configure-a-windows-project-to-use-clang-tools"></a>將 Windows 專案設定為使用 Clang 工具

若要將 Visual Studio 專案設定為使用 clang, 請以滑鼠右鍵按一下**方案總管**中的專案節點, 然後選擇 [**屬性**]。 一般來說, 您應該先選擇對話方塊頂端的 [**所有**設定]。 然後, 在 **[一般** > **平臺工具**組] 底下, 依序選擇 [ **LLVM] (clang-cl)** 和 **[確定]** 。

![Clang 元件安裝](media/clang-msbuild-prop-page.png)

如果您使用 Visual Studio 隨附的 Clang 工具, 則不需要任何額外的步驟。 對於 Windows 專案, Visual Studio 預設會在[Clang-cl](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf)模式中叫用 Clang, 並以標準程式庫的 Microsoft 實作為連結。 根據預設, **clang-cl**位於`C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`。

如果您使用自訂的 Clang 安裝, 您可以修改**專案** > **屬性** >  **VC + + 目錄** > 設定**屬性** > **可執行檔目錄**, 方法是新增自訂 Clang 安裝根目錄作為第一個目錄, 或變更`LLVMInstallDir`屬性的值。 如需詳細資訊, 請參閱[設定自訂 LLVM 位置](#custom_llvm_location)。

## <a name="configure-a-linux-project-to-use-clang-tools"></a>將 Linux 專案設定為使用 Clang 工具

針對 Linux 專案, Visual Studio 使用 Clang GCC 相容前端。 專案屬性和幾乎所有編譯器旗標都相同

若要將 Visual Studio Linux 專案設定為使用 Clang:

1. 以滑鼠右鍵按一下**方案總管**中的專案節點, 然後選擇 [**屬性**]。 
1. 一般來說, 您應該先選擇對話方塊頂端的 [**所有**設定]。 
1. 如果您使用適用于 Linux 的 Windows 子系統, 請在 **[一般** > **平臺工具**組] 底下選擇 [ **WSL_Clang_1_0** ], 如果您使用的是遠端電腦或 VM, 請選擇**Remote_Clang_1_0** 。
1. 按 [確定]。

![Clang 元件安裝](media/clang-msbuild-prop-page.png)

在 Linux 上, Visual Studio 預設會使用它在 PATH 環境屬性中遇到的第一個 Clang 位置。 如果您使用自訂的 Clang 安裝, `LLVMInstallDir`您必須變更屬性的值, 或者替代**專案** > **屬性** >  **VC + + 目錄** >  **底下的路徑設定屬性** > **可執行檔目錄**。 如需詳細資訊, 請參閱[設定自訂 LLVM 位置](#custom_llvm_location)。

## <a name="custom_llvm_location"></a>設定自訂 LLVM 位置

您可以藉由建立 *.props*檔案, 並將該檔案新增至任何專案的根資料夾, 為一個或多個專案設定 LLVM 的自訂路徑。 您可以將它新增至 [根方案] 資料夾, 以將它套用至方案中的所有專案。 檔案看起來應該像這樣 (但要替代您的實際路徑):

```xml
<Project>
  <PropertyGroup>
    <LLVMInstallDir>c:\MyLLVMRootDir</LLVMInstallDir>
  </PropertyGroup>
</Project>
```

## <a name="set-additional-properties-edit-build-and-debug"></a>設定其他屬性、編輯、建立和 debug

設定 Clang 設定之後, 請在專案節點上按一下滑鼠右鍵, 然後選擇 [**重載專案**]。 您現在可以使用 Clang 工具來建立和調試專案。 Visual Studio 偵測到您使用 Clang 編譯器, 並提供 IntelliSense、醒目提示、導覽和其他編輯功能。 錯誤和警告會顯示在**輸出視窗**中。 Clang 設定的專案屬性頁與 MSVC 非常類似, 雖然某些編譯器相依的功能 (例如 [編輯後繼續]) 不適用於 Clang 設定。 若要設定屬性頁中無法使用的 Clang 編譯器或連結器選項, 您可以在 [設定**屬性** > ]**C/C++ (或連結器)**  > **命令列**底下的屬性頁中手動新增它**其他選項**。  > 

在調試時, 您可以使用中斷點、記憶體和資料視覺效果, 以及大部分其他的調試功能。  

![Clang 調試](media/clang-debug-msbuild.png)

::: moniker-end
