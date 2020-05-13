---
title: 逐步解說：在命令列上編譯 C++/CLI 程式
ms.date: 04/23/2019
ms.assetid: cef41c88-faf9-439d-8423-25aa3f5674dd
ms.openlocfilehash: 8a5c5659367350a80725b365ef9c431bbec209d1
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877459"
---
# <a name="walkthrough-compiling-a-ccli-program-on-the-command-line"></a>逐步解說：在命令列上編譯 C++/CLI 程式

您可以建立以通用語言執行階段 (CLR) 為目標且使用 .NET Framework 的 Visual C++ 程式，並在命令列上建置它們。 Visual C++ 支援 C++/CLI 程式設計語言，其具有其他類型及運算子，以將 .NET 程式設計模型設定為目標。 如需 c + +/CLI 語言的一般資訊，請參閱[使用 c + +/cli 進行 .net 程式設計（Visual C++）](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)。

在此逐步解說中，您可以使用文字編輯器來建立基本的 C++/CLI 程式，然後在命令列上進行編譯。 (您可以使用自己的 C++/CLI 程式，而不是輸入所顯示的程式，或者您可以使用其他說明文章中的 C++/CLI 程式碼範例。 這項技術適用于建立和測試沒有 UI 元素的小型模組）。

## <a name="prerequisites"></a>必要條件

您已瞭解 c + + 語言的基本概念。

## <a name="compiling-a-ccli-program"></a>編譯 C++/CLI 程式

下列步驟顯示如何編譯使用 .NET Framework 類別的 C++/CLI 主控台應用程式。

若要啟用 c + +/CLI 的編譯，您必須使用[/clr](reference/clr-common-language-runtime-compilation.md)編譯器選項。 MSVC 編譯器會產生包含 MSIL 程式碼（或混合的 MSIL 和機器碼）的 .exe 檔案，並連結至所需的 .NET Framework 程式庫。

### <a name="to-compile-a-ccli-application-on-the-command-line"></a>在命令列上編譯 C++/CLI 應用程式

1. 開啟**開發人員命令提示字元**視窗。 如需特定指示，請參閱[以開啟開發人員命令提示字元視窗](building-on-the-command-line.md#developer_command_prompt)。

   若要成功編譯程式碼，需要系統管理員認證，具體取決於電腦的作業系統及組態。 若要以系統管理員身分執行 [命令提示字元] 視窗，請以滑鼠右鍵按一下開啟命令提示字元的快捷方式功能表，然後選擇 [**更多** > 以**系統管理員身分執行**]。

1. 在命令提示字元處，輸入 `notepad basicclr.cpp`。

   當系統提示您建立檔案時，請選擇 [**是]** 。

1. 在 [記事本] 中，輸入下列行：

   ```cpp
   int main()
   {
       System::Console::WriteLine("This is a C++/CLI program.");
   }
   ```

1. 在功能表列上 **，選擇 [** > 檔案] [**儲存**]。

   您已建立在<xref:System.Console> <xref:System>命名空間中使用 .NET Framework 類別（）的 Visual C++ 原始程式檔。

1. 在命令提示字元處，輸入 `cl /clr basicclr.cpp`。 cl.exe 編譯器會將原始程式碼編譯為包含 MSIL 的 .obj 檔案，然後執行連結器，以產生名為 basicclr.exe 的可執行程式 

1. 若要執行 basicclr.exe 程式，請在命令提示字元下，輸入 `basicclr`。

   程式會顯示下列文字並結束：

   ```Output
   This is a C++/CLI program.
   ```

## <a name="see-also"></a>請參閱

[C + + 語言參考](../cpp/cpp-language-reference.md)<br/>
[專案和建置系統](projects-and-build-systems-cpp.md)<br/>
[MSVC 編譯器選項](reference/compiler-options.md)
