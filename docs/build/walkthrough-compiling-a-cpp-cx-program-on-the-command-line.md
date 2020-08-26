---
title: 逐步解說：在命令列上編譯 C++/CX 程式
ms.date: 04/23/2019
ms.assetid: 626f5544-69ed-4736-83a9-f11389b371b2
ms.openlocfilehash: 8dcd27ca8fff826f33ee8bd752cd32f2d44d3691
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836708"
---
# <a name="walkthrough-compiling-a-ccx-program-on-the-command-line"></a>逐步解說：在命令列上編譯 C++/CX 程式

> [!NOTE]
> 針對新的 UWP 應用程式和元件，建議您使用 [c + +/WinRT](/windows/uwp/cpp-and-winrt-apis/)（標準 c + + 17 語言投影）來 Windows 執行階段 api。 從1803版開始，Windows 10 SDK 提供 c + +/WinRT。 C + +/WinRT 完全在標頭檔中執行，其設計目的是要提供您最新的 Windows API 的第一級存取。

Microsoft c + + 編譯器 (MSVC) 支援 c + +/CX) ，該 (擴充功能具有其他類型和運算子，以 Windows 執行階段程式設計模型為目標。 您可以使用 c + +/CX 來建立應用程式，以通用 Windows 平臺 (UWP) 和 Windows 桌面。 如需詳細資訊，請參閱 [c + +/cx](/archive/msdn-magazine/2013/april/component-extensions-a-tour-of-c-cx) 和 [執行時間平臺的元件擴充](../extensions/component-extensions-for-runtime-platforms.md)功能教學課程。

在此逐步解說中，您可以使用文字編輯器來建立基本的 C++/CX 程式，然後在命令列上進行編譯。 (您可以使用自己的 C++/CX 程式，而不是輸入所顯示的程式，或者您可以使用其他說明文章中的 C++/CX 程式碼範例。 這項技術適用于建立及測試沒有 UI 元素的小型模組。 ) 

> [!NOTE]
> 您還可以使用 Visual Studio IDE，來編譯 C++/CX 程式。 由於 IDE 包含無法在命令列上使用的設計、偵錯工具、模擬及部署支援，因此建議您使用 IDE 來建立通用 Windows 平臺 (UWP) 應用程式。 如需詳細資訊，請參閱 [在 c + + 中建立 UWP 應用程式](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)。

## <a name="prerequisites"></a>先決條件

您瞭解 c + + 語言的基本概念。

## <a name="compiling-a-ccx-program"></a>編譯 C++/CX 程式

若要啟用 c + +/CX 的編譯，您必須使用 [/ZW](reference/zw-windows-runtime-compilation.md) 編譯器選項。 MSVC 編譯器會產生以 Windows 執行階段為目標的 .exe 檔案，並會連結至所需的程式庫。

#### <a name="to-compile-a-ccx-application-on-the-command-line"></a>在命令列上編譯 C++/CX 應用程式

1. 開啟 **開發人員命令提示字元** 視窗。  (在 [ **開始** ] 視窗上，開啟 [ **應用程式**]。 開啟您的 Visual Studio 版本下的 **Visual Studio Tools** 資料夾，然後選擇 [ **開發人員命令提示字元** ] 快捷方式 ) 。如需如何開啟開發人員命令提示字元視窗的詳細資訊，請參閱。如需如何開啟視窗的詳細資訊，請參閱 [從命令列使用 MSVC 工具](building-on-the-command-line.md)組。

   若要成功編譯程式碼，需要系統管理員認證，具體取決於電腦的作業系統及組態。 若要以系統管理員身分執行 [命令提示字元] 視窗，請開啟 **開發人員命令提示字元** 的快捷方式功能表，然後選擇 [以 **系統管理員身分執行**]。

1. 在命令提示字元中，輸入 **notepad basiccx.exe .cpp**。

   當系統提示您建立檔案時，請選擇 **[是]** 。

1. 在 [記事本] 中，輸入下列行：

    ```cpp
    using namespace Platform;

    int main(Platform::Array<Platform::String^>^ args)
    {
        Platform::Details::Console::WriteLine("This is a C++/CX program.");
    }
    ```

1. 在功能表列上 **，選擇 [**  >  **儲存**盤案]。

   您已建立使用 Windows 執行階段 [Platform namespace](../cppcx/platform-namespace-c-cx.md) 命名空間的 c + + 原始程式檔。

1. 在命令提示字元中，輸入 **cl/EHSC/ZW basiccx.exe .cpp/LINK/SUBSYSTEM： CONSOLE**。 cl.exe 編譯器會將原始程式碼編譯為 .obj 檔案，然後執行連結器，以產生名為 basiccx.exe 的可執行程式   ([/ehsc](reference/eh-exception-handling-model.md) 編譯器選項會指定 c + + 例外狀況處理模型，而 [/link](reference/link-pass-options-to-linker.md) 旗標會指定主控台應用程式。 ) 

1. 若要執行 basiccx.exe 程式，請在命令提示字元中，輸入 **basiccx.exe**。

   程式會顯示下列文字並結束：

    ```Output
    This is a C++/CX program.
    ```

## <a name="see-also"></a>另請參閱

[專案與建置系統](projects-and-build-systems-cpp.md)<br/>
[MSVC 編譯器選項](reference/compiler-options.md)
