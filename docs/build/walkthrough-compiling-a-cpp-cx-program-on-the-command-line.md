---
title: 逐步解說： 編譯 C + + /CX 程式命令列上的 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 626f5544-69ed-4736-83a9-f11389b371b2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0963f70047ea42893b1169c5da7c614766406280
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32384801"
---
# <a name="walkthrough-compiling-a-ccx-program-on-the-command-line"></a>逐步解說：在命令列上編譯 C++/CX 程式
您可以建立以 Windows 執行階段為目標的 Visual C++ 程式，並在命令列上建置它們。 Visual C++ 支援 Visual C++ 元件擴充功能 (C++/CX)，其具有以 WinRT 執行階段程式設計模型為目標的其他類型及運算子。 您可以使用 C + + /CX，以建置通用 Windows 平台 (UWP)、 Windows Phone 8.1 和 Windows 桌面應用程式。 如需詳細資訊，請參閱[教學課程的 C + /CX](http://msdn.microsoft.com/magazine/dn166929.aspx)和[執行階段平台的元件擴充功能](../windows/component-extensions-for-runtime-platforms.md)。  
  
 在此逐步解說中，您可以使用文字編輯器來建立基本的 C++/CX 程式，然後在命令列上進行編譯。 (您可以使用自己的 C++/CX 程式，而不是輸入所顯示的程式，或者您可以使用其他說明文章中的 C++/CX 程式碼範例。 這項技術對於建置和測試不包含 UI 項目的小模組非常有用)。  
  
> [!NOTE]
>  您還可以使用 Visual Studio IDE，來編譯 C++/CX 程式。 因為這個 IDE 包括設計、 偵錯、 模擬，以及命令列沒有可用的部署支援，我們建議您使用 IDE 建置通用 Windows 平台 (UWP) 應用程式。 如需詳細資訊，請參閱[在 c + + 中建立的 UWP 應用程式](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)。  
  
## <a name="prerequisites"></a>必要條件  
 您必須了解 C++ 語言的基本概念。  
  
## <a name="compiling-a-ccx-program"></a>編譯 C++/CX 程式  
 若要啟用編譯 C + /CX 中，您必須使用[/ZW](../build/reference/zw-windows-runtime-compilation.md)編譯器選項。 Visual C++ 編譯器會產生以 Windows 執行階段為目標的 .exe 檔案，並會連結至所需的程式庫。  
  
#### <a name="to-compile-a-ccx-application-on-the-command-line"></a>在命令列上編譯 C++/CX 應用程式  
  
1.  開啟**開發人員命令提示字元**視窗。 (在**啟動**視窗中，開啟**應用程式**。 開啟**Visual Studio Tools**下您版本的資料夾[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]，然後選擇 **開發人員命令提示字元**快顯。)如需如何開啟 [開發人員命令提示字元] 視窗的詳細資訊，請參閱[命令列上的建置 C/c + + 程式碼](../build/building-on-the-command-line.md)。  
  
     若要成功編譯程式碼，需要系統管理員認證，具體取決於電腦的作業系統及組態。 若要以系統管理員身分執行命令提示字元視窗，開啟捷徑功能表**開發人員命令提示字元**，然後選擇 **系統管理員身分執行**。  
  
2.  在命令提示字元中，輸入**記事本 basiccx.cpp**。  
  
     選擇**是**提示您時建立檔案。  
  
3.  在 [記事本] 中，輸入下列行：  
  
    ```cpp  
    using namespace Platform;  
  
    int main(Platform::Array<Platform::String^>^ args)  
    {  
        Platform::Details::Console::WriteLine("This is a C++/CX program.");  
    }  
  
    ```  
  
4.  在功能表列上選擇 **檔案**，**儲存**。  
  
     您已建立 Windows 執行階段會使用 Visual c + + 原始程式檔[Platform 命名空間](../cppcx/platform-namespace-c-cx.md)命名空間。  
  
5.  在命令提示字元中，輸入**cl /EHsc /ZW basiccx.cpp /link /subsystem: console**。 cl.exe 編譯器會將原始程式碼編譯為 .obj 檔案，然後執行連結器，以產生名為 basiccx.exe 的可執行程式  ( [/EHsc](../build/reference/eh-exception-handling-model.md)編譯器選項指定 c + + 例外狀況處理模型，而[/link> >](../build/reference/link-pass-options-to-linker.md)旗標會指定主控台應用程式。)  
  
6.  若要執行 basiccx.exe 程式，請在命令提示字元中，輸入**basiccx**。  
  
     程式會顯示下列文字並結束：  
  
    ```Output  
    This is a C++/CX program.  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [C + + 語言參考](../cpp/cpp-language-reference.md)   
 [建置 C/C++ 程式](../build/building-c-cpp-programs.md)   
 [編譯器選項](../build/reference/compiler-options.md)