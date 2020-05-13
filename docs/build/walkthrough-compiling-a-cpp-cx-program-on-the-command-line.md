---
title: 逐步解說：在命令列上編譯 C++/CX 程式
ms.date: 04/23/2019
ms.assetid: 626f5544-69ed-4736-83a9-f11389b371b2
ms.openlocfilehash: 83369fc7b458463ea1f44a347bbcd0ca4eb32224
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078199"
---
# <a name="walkthrough-compiling-a-ccx-program-on-the-command-line"></a>逐步解說：在命令列上編譯 C++/CX 程式

> [!NOTE]
> 針對新的 UWP 應用程式和元件，建議您使用[c + +/WinRT](/windows/uwp/cpp-and-winrt-apis/)，這是標準 c + + 17 語言投影，用於 Windows 執行階段 api。 從1803版開始，Windows 10 SDK 中提供 c + +/WinRT。 C + +/WinRT 完全實作為標頭檔，其設計目的是為您提供現代化 Windows API 的第一級存取。

Microsoft c + + 編譯器（MSVC）支援 c + + 元件延伸模組（c + +/CX），其具有以 Windows 執行階段程式設計模型為目標的其他類型和運算子。 您可以使用 c + +/CX 來建立適用于通用 Windows 平臺（UWP）和 Windows 桌面的應用程式。 如需詳細資訊，請參閱[c + +/cx](https://msdn.microsoft.com/magazine/dn166929.aspx)的教學課程和[執行時間平臺的元件延伸](../extensions/component-extensions-for-runtime-platforms.md)模組。

在此逐步解說中，您可以使用文字編輯器來建立基本的 C++/CX 程式，然後在命令列上進行編譯。 (您可以使用自己的 C++/CX 程式，而不是輸入所顯示的程式，或者您可以使用其他說明文章中的 C++/CX 程式碼範例。 這項技術適用于建立和測試沒有 UI 元素的小型模組）。

> [!NOTE]
> 您還可以使用 Visual Studio IDE，來編譯 C++/CX 程式。 由於 IDE 包含命令列上無法使用的設計、偵測、模擬和部署支援，因此建議您使用 IDE 來建立通用 Windows 平臺（UWP）應用程式。 如需詳細資訊，請參閱[在 c + + 中建立 UWP 應用程式](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)。

## <a name="prerequisites"></a>必要條件

您已瞭解 c + + 語言的基本概念。

## <a name="compiling-a-ccx-program"></a>編譯 C++/CX 程式

若要啟用 c + +/CX 的編譯，您必須使用[/ZW](reference/zw-windows-runtime-compilation.md)編譯器選項。 MSVC 編譯器會產生以 Windows 執行階段為目標的 .exe 檔案，並連結至所需的程式庫。

#### <a name="to-compile-a-ccx-application-on-the-command-line"></a>在命令列上編譯 C++/CX 應用程式

1. 開啟**開發人員命令提示字元**視窗。 （在 [**開始**] 視窗中，開啟 [**應用程式**]。 開啟您的 Visual Studio 版本底下的 [ **Visual Studio Tools** ] 資料夾，然後選擇**開發人員命令提示字元**快捷方式）。如需如何開啟開發人員命令提示字元視窗的詳細資訊，請參閱[從命令列使用 MSVC 工具](building-on-the-command-line.md)組。

   若要成功編譯程式碼，需要系統管理員認證，具體取決於電腦的作業系統及組態。 若要以系統管理員身分執行 [命令提示字元] 視窗，請開啟**開發人員命令提示字元**的快捷方式功能表，然後選擇 [**以系統管理員身分執行**]。

1. 在命令提示字元中，輸入**notepad basiccx.cpp**。

   當系統提示您建立檔案時，請選擇 [**是]** 。

1. 在 [記事本] 中，輸入下列行：

    ```cpp
    using namespace Platform;

    int main(Platform::Array<Platform::String^>^ args)
    {
        Platform::Details::Console::WriteLine("This is a C++/CX program.");
    }
    ```

1. 在功能表列上 **，選擇 [** > 檔案] [**儲存**]。

   您已經建立了 c + + 原始程式檔，該檔案會使用 Windows 執行階段[Platform 命名](../cppcx/platform-namespace-c-cx.md)空間命名空間。

1. 在命令提示字元中，輸入**cl/EHSC/ZW basiccx.cpp. .cpp/LINK/SUBSYSTEM： CONSOLE**。 cl.exe 編譯器會將原始程式碼編譯為 .obj 檔案，然後執行連結器，以產生名為 basiccx.exe 的可執行程式  （ [/Ehsc](reference/eh-exception-handling-model.md)編譯器選項會指定 c + + 例外狀況處理模型，而[/link](reference/link-pass-options-to-linker.md)旗標會指定主控台應用程式）。

1. 若要執行 basiccx.cpp 程式，請在命令提示字元中輸入**basiccx.cpp**。

   程式會顯示下列文字並結束：

    ```Output
    This is a C++/CX program.
    ```

## <a name="see-also"></a>請參閱

[專案和建置系統](projects-and-build-systems-cpp.md)<br/>
[MSVC 編譯器選項](reference/compiler-options.md)
