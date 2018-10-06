---
title: 逐步解說： 編譯 C + + /cli 程式命令列 |Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cef41c88-faf9-439d-8423-25aa3f5674dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bdc09d5c1de2e74f7e24b72439910068fe9f6c1a
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/05/2018
ms.locfileid: "48820619"
---
# <a name="walkthrough-compiling-a-ccli-program-on-the-command-line"></a>逐步解說：在命令列上編譯 C++/CLI 程式

您可以建立以通用語言執行階段 (CLR) 為目標且使用 .NET Framework 的 Visual C++ 程式，並在命令列上建置它們。 Visual C++ 支援 C++/CLI 程式設計語言，其具有其他類型及運算子，以將 .NET 程式設計模型設定為目標。 取得的一般資訊的 C + + 語言，請參閱[.NET 程式設計使用 C + + /cli （Visual c + +）](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)。

在此逐步解說中，您可以使用文字編輯器來建立基本的 C++/CLI 程式，然後在命令列上進行編譯。 (您可以使用自己的 C++/CLI 程式，而不是輸入所顯示的程式，或者您可以使用其他說明文章中的 C++/CLI 程式碼範例。 這項技術可用於建置和測試沒有任何 UI 元素的小模組。）

> [!NOTE]
> 您還可以使用 Visual Studio IDE，來編譯 C++/CLI 程式。 如需詳細資訊，請參閱 <<c0> [ 逐步解說： 編譯 Visual Studio 中 Clr 的 c + + 程式](../ide/walkthrough-compiling-a-cpp-program-that-targets-the-clr-in-visual-studio.md)。

## <a name="prerequisites"></a>必要條件

您了解 c + + 語言的基本概念。

## <a name="compiling-a-ccli-program"></a>編譯 C++/CLI 程式

下列步驟顯示如何編譯使用 .NET Framework 類別的 C++/CLI 主控台應用程式。

若要啟用編譯 C + /cli，您必須使用[/clr](../build/reference/clr-common-language-runtime-compilation.md)編譯器選項。 Visual C++ 編譯器會產生包含 MSIL 程式碼或混合的 MSIL 和機器碼的 .exe 檔案，並會連結至所需的 .NET Framework 程式庫。

### <a name="to-compile-a-ccli-application-on-the-command-line"></a>在命令列上編譯 C++/CLI 應用程式

1. 開啟**開發人員命令提示字元**視窗。 特定的指示，請參閱[若要開啟 開發人員命令提示字元視窗](../build/building-on-the-command-line.md#developer_command_prompt)。

   若要成功編譯程式碼，需要系統管理員認證，具體取決於電腦的作業系統及組態。 若要以系統管理員身分執行命令提示字元視窗，以滑鼠右鍵按一下要開啟命令提示字元的捷徑功能表，然後選擇**更多** > **系統管理員身分執行**。

1. 在命令提示字元處，輸入 `notepad basicclr.cpp`。

   選擇**是**當系統提示您建立的檔案。

1. 在 [記事本] 中，輸入下列行：

   ```cpp
   int main()
   {
       System::Console::WriteLine("This is a C++/CLI program.");
   }
   ```

1. 在功能表列上選擇 **檔案** > **儲存**。

   您已建立 Visual c + + 原始程式檔，使用.NET Framework 類別 (<xref:System.Console>) 中<xref:System>命名空間。

1. 在命令提示字元處，輸入 `cl /clr basicclr.cpp`。 cl.exe 編譯器會將原始程式碼編譯為包含 MSIL 的 .obj 檔案，然後執行連結器，以產生名為 basicclr.exe 的可執行程式 

1. 若要執行 basicclr.exe 程式，請在命令提示字元下，輸入 `basicclr`。

   程式會顯示下列文字並結束：

   ```Output
   This is a C++/CLI program.
   ```

## <a name="see-also"></a>另請參閱

[C++ 語言參考](../cpp/cpp-language-reference.md)<br/>
[建置 C/C++ 程式](../build/building-c-cpp-programs.md)<br/>
[編譯器選項](../build/reference/compiler-options.md)
