---
title: 視覺化工作室視覺工作室專案中的 Clang/LLVM 支援
ms.date: 08/30/2019
ms.description: Configure a Visual Studio MSBuild project to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ MSBuild projects
ms.openlocfilehash: 8d7d7fec979d3e7b8f665e56094ee1c309e3b686
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323113"
---
# <a name="clangllvm-support-in-visual-studio-projects"></a>視覺化工作室專案中的 Clang/LLVM 支援

::: moniker range="<=vs-2017"

在 Visual Studio 2019 中提供了對 CMake 和 MSBuild 專案的 Clang 支援。

::: moniker-end

::: moniker range="vs-2019"

您可以將 Visual Studio 2019 版本 16.2 與 Clang 一起用於編輯、構建和調試面向 Windows 或 Linux 的C++可視化工作室專案 (MSBuild)。

## <a name="install"></a>安裝

為了在 Visual Studio 中獲得最佳 IDE 支援,我們建議使用 Windows 的最新 Clang 編譯器工具。 如果還沒有這些,則可以通過打開 Visual Studio 安裝程式並選擇**C++ Clang 工具來安裝這些這些工具,用於****桌面開發下的 Windows,C++** 可選元件。 如果您希望在電腦上使用現有的 Clang 安裝,請選擇**v142 生成工具的clang-clC++。** 可選元件。 微軟C++標準庫目前至少需要Clang 8.0.0;Clang 的捆綁版本將自動更新,以在標準庫的 Microsoft 實現中保持最新更新。

![Clang 元件安裝](media/clang-install-vs2019.png)

## <a name="configure-a-windows-project-to-use-clang-tools"></a>將 Windows 專案設定為使用 Clang 工具

要將 Visual Studio 專案配置為使用 Clang,請右鍵單擊**解決方案資源管理器**中的專案節點並選擇 **「屬性**」。 通常,應首先選擇對話框頂部**的所有設定**。 然後,在**一般** > **平台工具集**下,選擇**LLVM (clang-cl),** 然後**確定**。

![Clang 元件安裝](media/clang-msbuild-prop-page.png)

如果您使用的是與 Visual Studio 捆綁的 Clang 工具,則無需執行其他步驟。 對於 Windows 專案,Visual Studio 預設情況下以[clang-cl](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf)模式調用 Clang,並與標準庫的 Microsoft 實現連結。 默認情況下 **,clang-cl.exe**位於`C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`中。

如果使用自訂 Clang 安裝,則可以透過新增自訂 Clang 安裝根作為第一個目錄來修改**專案** > **屬性** > **VC++ DIrectories** > **配置屬性** > **可執行目錄**,或者更改`LLVMInstallDir`屬性的值。 關於詳細資訊[,請參閱設定自訂 LLVM 位置](#custom_llvm_location)。

## <a name="configure-a-linux-project-to-use-clang-tools"></a>將 Linux 專案設定為使用 Clang 工具

對於 Linux 專案,Visual Studio 使用 Clang GCC 相容的前端。 專案屬性和幾乎所有編譯器標誌都相同

要將視覺化工作室 Linux 專案設定為使用 Clang:

1. 右鍵按下**解決方案資源管理員**中的項目節點並選擇**屬性**。
1. 通常,應首先選擇對話框頂部**的所有設定**。
1. 在 **「一般**>**平臺工具集**」下,選擇**WSL_Clang_1_0**是否正在使用適用於 Linux 的 Windows 子系統,或者選擇**Remote_Clang_1_0**是否使用遠端電腦或 VM。
1. 按下 **[確定]**。

![Clang 元件安裝](media/clang-msbuild-prop-page.png)

在 Linux 上,Visual Studio 預設情況下使用它在 PATH 環境屬性中遇到的第一個 Clang 位置。 如果使用自訂 Clang 安裝,`LLVMInstallDir`則必須更改屬性的值,否則替換**項目** > **屬性** > **VC++ DIrecres** > **配置屬性** > **可執行目錄**下的路徑。 關於詳細資訊[,請參閱設定自訂 LLVM 位置](#custom_llvm_location)。

## <a name="set-a-custom-llvm-location"></a><a name="custom_llvm_location"></a>設定自訂 LLVM 位置

您可以通過創建*Directory.build.props*檔並將該檔添加到任何專案的根資料夾,為一個或多個專案設置 LLVM 的自訂路徑。 您可以將其添加到根解決方案資料夾中,將其應用於解決方案中的所有專案。 該檔應如下所示(但取代實際路徑):

```xml
<Project>
  <PropertyGroup>
    <LLVMInstallDir>c:\MyLLVMRootDir</LLVMInstallDir>
  </PropertyGroup>
</Project>
```

## <a name="set-additional-properties-edit-build-and-debug"></a>設定其他屬性、編輯、產生和除錯

設置 Clang 設定後,右鍵單擊專案節點並選擇 **「重新載入專案**」。 現在,您可以使用 Clang 工具生成和除錯專案。 Visual Studio 檢測到您正在使用 Clang 編譯器,並提供 IntelliSense、突出顯示、導航和其他編輯功能。 錯誤與警告顯示在**輸出視窗中**。 Clang 配置的項目屬性頁與 MSVC 的專案屬性頁非常相似,儘管某些與編譯器相關的功能(如"編輯"和"繼續")不適用於 Clang 配置。 要設置屬性頁中不可用的 Clang 編譯器或連結器選項,可以在**配置屬性** > **C/C++(或連結器)** > **命令列** > **附加選項**下的屬性頁中手動添加該選項。

調試時,可以使用斷點、記憶體和數據可視化以及大多數其他調試功能。  

![Clang 除錯](media/clang-debug-msbuild.png)

::: moniker-end
