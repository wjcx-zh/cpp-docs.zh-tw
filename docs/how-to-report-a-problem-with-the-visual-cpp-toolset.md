---
title: "如何回報 Visual C++ 工具組問題 | Microsoft Docs"
ms.custom: 
ms.date: 1/03/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b1a5cdb873d536702ecf8536d9a9e7c0205cc923
ms.sourcegitcommit: a5d8f5b92cb5e984d5d6c9d67fe8a1241f3fe184
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-report-a-problem-with-the-visual-c-toolset"></a>如何回報 Visual C++ 工具組問題

如果您遇到 Visual C++ 編譯器、連結器或其他工具問題，我們想要知道它們。

讓我們知道問題的最佳方式是將一份內含下列資訊的報表傳送給我們：所遇過問題的描述、如何建置程式的詳細資料，以及可用來在我們自己的電腦上重現問題的一些程式碼。 這項資訊可讓我們快速確認問題存在並且不是環境本機的問題、判斷是否影響其他版本的編譯器，以及診斷其原因。

您在本文件中將了解：

- [如何準備報表](#prepare)，以及什麼構成良好報表。

- [如何產生重現](#generate)，以及不同類型的重現。

- [報表傳送方式](#send)，以及什麼讓它們不同。

您的報表對我們和您這類其他開發人員而言十分重要。 感謝您協助我們改善 Visual C++！

## <a name="prepare"></a> 如何準備報表

因為沒有完整資訊很難在我們自己的電腦上重現您遇到的問題，所以建立高品質報表十分重要。 您的報表越好，我們就越能更有效率地重新建立並診斷問題。

您的報表最少應該包含：

- 所使用工具組的完整版本資訊。

- 用來建置您程式碼的完整 cl.exe 命令列。

- 所遇到問題的詳細描述。

- 「重現」：顯現問題的原始程式碼。

請閱讀以深入了解我們需要的特定資訊以及可以找到它的位置。

### <a name="the-toolset-version"></a>工具組版本

我們需要您所使用工具組的完整版本資訊，讓我們能夠在我們的電腦上針對相同的工具組測試您的重現。 如果我們可以重現問題，這項資訊也會提供一個起點，讓我們調查哪些其他版本的工具組展示相同的問題。

#### <a name="to-report-the-full-version-of-the-compiler-youre-using"></a>回報所使用編譯器的完整版本

1. 按下鍵盤上的 Windows 鍵，然後開始輸入 `Developer Command Prompt`。

1. [開發人員命令提示字元] 出現在相符項目清單時，請選擇符合所使用 Visual Studio 版本的 [開發人員命令提示字元] 版本。

1. 在 [開發人員命令提示字元] 主控台中，輸入 `cl /Bv /CLR` 命令。

輸出應該如下：

```Output
C:\Compiler>cl /Bv /CLR
Microsoft (R) C/C++ Optimizing Compiler Version 18.00.40209
for Microsoft (R) .NET Framework version 4.00.30319.34014
Copyright (C) Microsoft Corporation.  All rights reserved.

Compiler Passes:
 C:\WinCComp\binaries.x86chk\bin\i386\cl.exe:        Version 18.00.40209.0
 C:\WinCComp\binaries.x86chk\bin\i386\c1.dll:        Version 18.00.40209.0
 C:\WinCComp\binaries.x86chk\bin\i386\c1xx.dll:      Version 18.00.40209.0
 C:\WinCComp\binaries.x86chk\bin\i386\c2.dll:        Version 18.00.40209.0
 C:\WinCComp\binaries.x86chk\bin\i386\link.exe:      Version 12.00.40209.0
 C:\WinCComp\binaries.x86chk\bin\i386\mspdb120.dll:  Version 12.00.40209.0
 C:\WinCComp\binaries.x86chk\bin\i386\1033\clui.dll: Version 18.00.40209.0
 Common Language Runtime:                            Version  4.00.30319.34014

cl : Command line error D8003 : missing source filename
```

複製整個輸出，並將其貼入您的報表。

### <a name="the-command-line"></a>命令列

我們需要用來建置您程式碼的完整命令列 (cl.exe 和其引數)，以在我們的電腦上以完全相同的方式進行建置。 因為只有在使用特定引數或引數組合進行建置時才會發生您遇到的問題，所以這十分重要。

找到這項資訊的最佳位置是在遇到問題之後那時的組建記錄檔。 這確保命令列包含可能造成問題的完全相同引數。

#### <a name="to-report-the-contents-of-the-command-line"></a>回報命令列內容

1. 找到並開啟 **CL.command.1.tlog** 檔案。 根據預設，此檔案位於 \\...\Visual Studio *version*\Projects\\*SolutionName*\\*ProjectName*\Config\\*ProjectName*.tlog\CL.command.1.tlog。

   在此檔案內，您可以找到後接用來編譯原始程式碼檔之命令列引數的原始程式碼檔名稱，而且一行一個引數。

1. 找到包含發生問題之原始程式碼檔名稱的那一行；該行的下行會包含對應的 cl.exe 命令和其引數。

複製整個命令列，並將其貼入您的報表。

### <a name="a-description-of-the-problem"></a>問題描述

我們需要您所遇到問題的詳細描述，以確認看到您電腦上的相同效果；它有時也可讓我們知道您嘗試完成的作業以及預期發生的情況。

請提供工具組所提供的精確錯誤訊息、您嘗試完成之作業的簡短描述以協助我們了解您的重現程式碼，以及可能有助於診斷您所遇到問題的任何其他詳細資料，例如您可能發現的任何因應措施。 請避免在報表的其他位置出現找到的重複資訊。

### <a name="the-repro"></a>重現

我們需要「重現」(即示範您所遇到問題的獨立原始程式碼範例)，以在我們的電腦上重現錯誤。 您所遇到問題的類型將決定應該包含在報表中的重現類型。 如果沒有適當的重現，我們就無法進行調查。

簡短的獨立重現可以直接包含在您的報表文字中，但較大的原始程式碼重現則應該附加至報表。 應該封裝無法減少為單一原始程式碼檔的重現，方法是將包含所有檔案的目錄壓縮成 .zip 檔案或類似檔案，並附加至報表。 任何其他案例特定詳細資料都應該一律包含在報表文字中，但絕不會包含在原始程式碼中。

您可以提供給我們的最佳重現類型是「最少重現」。 這是單一的獨立原始程式碼檔 (不含使用者標頭的參考)，內含足夠示範問題的程式碼。 如果您可以提供這種形式的重現，則只需要將原始程式碼檔附加到您的報表；這就是我們所全部需要的。

如果您無法將問題濃縮為沒有相依性的最少重現，請參閱下列各節，以判斷您應該在報表中包含的重現類型。

#### <a name="frontend-parser-crash"></a>前端 (剖析器) 損毀

前端損毀是在編譯器的剖析階段期間發生。 編譯器通常會發出[嚴重錯誤 C1001](error-messages/compiler-errors-1/fatal-error-c1001.md)，並參考發生錯誤的原始程式碼檔和行號；它通常會提及 msc1.cpp 檔案，但您可以忽略此詳細資料。

針對這種損毀，請提供[前置處理過的重現](#preprocessed-repros)。

以下是這種損毀的範例編譯器輸出︰

```Output
SandBoxHost.cpp
d:\o\dev\search\foundation\common\tools\sandbox\managed\managed.h(929):
        fatal error C1001: An internal error has occurred in the compiler.
(compiler file 'msc1.cpp', line 1369)
To work around this problem, try simplifying or changing the program near the
        locations listed above.
Please choose the Technical Support command on the Visual C++
Help menu, or open the Technical Support help file for more information
d:\o\dev\search\foundation\common\tools\sandbox\managed\managed.h(929):
        note: This diagnostic occurred in the compiler generated function
        'void Microsoft::Ceres::Common::Tools::Sandbox::SandBoxedProcess::Dispose(bool)'
Internal Compiler Error in d:\o\dev\otools\bin\x64\cl.exe.  You will be prompted
        to send an error report to Microsoft later.
INTERNAL COMPILER ERROR in 'd:\o\dev\otools\bin\x64\cl.exe'
    Please choose the Technical Support command on the Visual C++
    Help menu, or open the Technical Support help file for more information
```

#### <a name="backend_crash"></a> 後端 (程式碼產生) 損毀

後端損毀是在編譯器的程式碼產生階段期間發生。 編譯器通常會發出[嚴重錯誤 C1001](error-messages/compiler-errors-1/fatal-error-c1001.md)，但可能未參考與問題相關聯的原始程式碼檔和行號；它通常會提及 compiler\utc\src\p2\main.c 檔案，但您可以忽略此詳細資料。

針對這種損毀，如果您正在使用連結時間產生程式碼 (LTCG)，請提供[連結重現](#link-repros)否則，請提供[前置處理過的重現](#preprocessed-repros)。 LTGC 是由 cl.exe 的 `/GL` 命令列引數所啟用。

以下是**未**使用 LTCG 這種損毀的範例編譯器輸出。 如果您的編譯器輸出看起來像這樣，則應該提供[前置處理過的重現](#preprocessed-repros)。

```Output
repro.cpp
\\officefile\public\tadg\vc14\comperror\repro.cpp(13) : fatal error C1001:
        An internal error has occurred in the compiler.
(compiler file 'f:\dd\vctools\compiler\utc\src\p2\main.c', line 230)
To work around this problem, try simplifying or changing the program near the
        locations listed above.
Please choose the Technical Support command on the Visual C++
Help menu, or open the Technical Support help file for more information
INTERNAL COMPILER ERROR in
        'C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\BIN\cl.exe'
    Please choose the Technical Support command on the Visual C++
    Help menu, or open the Technical Support help file for more information
```

如果開頭為**內部編譯器錯誤**的行提及 link.exe，而非 cl.exe，則已啟用 LTCG，而且您應該提供[連結重現](#link-repros)。 如果無法從編譯器錯誤訊息中了解是否已啟用 LTCG，您可能需要檢查從前一個步驟中 `/GL` 命令列引數之組建記錄複製的命令列引數。

#### <a name="linker-crash"></a>連結器損毀

連結器損毀是在執行編譯器後的連結階段期間發生。 連結器通常會發出[連結器工具錯誤 LNK1000](error-messages/tool-errors/linker-tools-error-lnk1000.md)。

> [!NOTE]
> 如果輸出提及 C1001，或涉及連結時產生程式碼，請參閱[後端 (程式碼產生) 損毀](#backend_crash)，而非詳細資訊。

針對這種損毀，請提供[連結重現](#link-repros)。

以下是這種損毀的範例編譯器輸出。

```Output
z:\foo.obj : error LNK1000: Internal error during IMAGE::Pass2

  Version 14.00.22816.0

  ExceptionCode            = C0000005
  ExceptionFlags           = 00000000
  ExceptionAddress         = 00007FF73C9ED0E6 (00007FF73C9E0000)
        "z:\tools\bin\x64\link.exe"
  NumberParameters         = 00000002
  ExceptionInformation[ 0] = 0000000000000000
  ExceptionInformation[ 1] = FFFFFFFFFFFFFFFF

CONTEXT:

  Rax    = 0000000000000400  R8     = 0000000000000000
  Rbx    = 000000655DF82580  R9     = 00007FF840D2E490
  Rcx    = 005C006B006F006F  R10    = 000000655F97E690
  Rdx    = 000000655F97E270  R11    = 0000000000000400
  Rsp    = 000000655F97E248  R12    = 0000000000000000
  Rbp    = 000000655F97EFB0  E13    = 0000000000000000
  Rsi    = 000000655DF82580  R14    = 000000655F97F390
  Rdi    = 0000000000000000  R15    = 0000000000000000
  Rip    = 00007FF73C9ED0E6  EFlags = 0000000000010206
  SegCs  = 0000000000000033  SegDs  = 000000000000002B
  SegSs  = 000000000000002B  SegEs  = 000000000000002B
  SegFs  = 0000000000000053  SegGs  = 000000000000002B
  Dr0    = 0000000000000000  Dr3    = 0000000000000000
  Dr1    = 0000000000000000  Dr6    = 0000000000000000
  Dr2    = 0000000000000000  Dr7    = 0000000000000000
```

如果已啟用累加連結，並且只有在初始連結之後才發生損毀 (也就是只有在後續累加連結所依據的第一個完整連結之後)，也請提供物件 (.obj) 和程式庫 (.lib) 檔案的複本，這些檔案必須對應到初始連結完成後經過修改的來源檔案。

#### <a name="bad-code-generation"></a>產生錯誤的程式碼

產生錯誤的程式碼十分罕見，但發生時機是編譯器錯誤地產生不正確程式碼讓您的應用程式在執行階段損毀，而不是在編譯時期偵測此問題。 如果您認為所遇到的問題會導致產生錯誤的程式碼，請使用與[後端 (程式碼產生) 損毀](#backend_crash)相同的方式來處理報表。

針對這種損毀，如果您正在使用連結時間產生程式碼 (LTCG)，請提供[連結重現](#link-repros)否則，請提供[前置處理過的重現](#preprocessed-repros)。 LTGC 是由 cl.exe 的 `/GL` 命令列引數所啟用。

## <a name="generate"></a> 產生重現

重現是一個完整獨立程式碼範例，可示範您要回報的問題。 重現**不**是程式碼片段，而必須是完整的建置加執行 (或先前的建置加執行，但您回報的問題所產生的錯誤除外) 範例。 它應該包含所有必要 #include 指示詞，即使針對標準標頭也是一樣。

甚至，好的重現為

- **最少**。 重現應該越小越好，但仍然確切地示範您所遇到的問題。 重現不需要很複雜或真實；簡單且準確的重現較佳。 它們不需要包含運作的計數器範例程式碼，但若為說明之用，則可能需要；只有造成問題的範例程式碼才是必要的。

- **獨立。** 重現應該避免不必要的相依性。 如果您可以重現問題，而不需要協力廠商程式庫，則請這樣做。 如果您可以重現問題，而不需要任何程式庫程式碼 (可以使用 `std::out`、`printf()`)，則請這樣做。 減少視為可能造成問題的程式碼數量十分有幫助。

- **針對最新編譯器版本。** 如果可能的話，重現應該使用最新版本的工具組。 在新版本中，已修正舊版工具組中仍然會遇到的問題。

- **針對其他編譯器檢查** (如果相關)。 涉及可攜式 C++ 程式碼的報表應該確認其他編譯器行為 (可能的話)。

   此步驟有助於判斷您的程式碼正確 (MSVC 不同意 Clang 和 GCC 時) 還是不正確 (MSVC、Clang 和 GCC 同意您的程式碼產生此錯誤時)。

以下是產生用來回報不同問題類型之各種重現類型的指示。

### <a name="preprocessed-repros"></a>前置處理過的重現

前置處理過的重現是單一原始程式檔，可示範問題，並透過處理原始程式檔以從 C 前置處理器輸出產生。 此程序內嵌包含的標頭來移除與其他來源和標頭檔的相依性，也會解析巨集、#ifdefs 以及其他取決於本機環境的前置處理器命令。

> [!NOTE]
> 請注意，因為我們通常會想要替代最新進行中的實作，以查看我們是否已修正問題，所以對於可能是標準程式庫實作中 Bug 所造成的問題，前置處理過的重現最不方便使用。 在此情況下，請不要前置處理重現，而且如果您無法將問題減少為單一原始程式檔，則請將程式碼封裝為 .zip 檔案或類似檔案，或考慮使用 IDE 專案重現 (請參閱下面的[其他重現](#other-repros))。

#### <a name="to-preprocess-a-source-code-file"></a>前置處理原始程式碼檔

1. 按下鍵盤上的 Windows 鍵，然後開始輸入 `Developer Command Prompt`。

1. [開發人員命令提示字元] 出現在相符項目清單時，請選擇符合所使用 Visual Studio 版本的 [開發人員命令提示字元] 版本。

1. 在 [開發人員命令提示字元] 主控台視窗中，輸入 `cl /P argumentsfilename.cpp` 命令。

具有前置處理過的檔案 (現在是 filename.i) 之後，最好確定仍然可以使用前置處理過的檔案重現問題。 您可以使用 `/TP` 命令列引數告訴 cl.exe 略過前置處理器步驟，並嘗試按照一般方式編譯。

#### <a name="to-confirm-that-the-error-still-repros-with-the-preprocessed-file"></a>確認仍然可以使用前置處理過的檔案重現錯誤

1. 按下鍵盤上的 Windows 鍵，然後開始輸入 `Developer Command Prompt`。

1. [開發人員命令提示字元] 出現在相符項目清單時，請選擇符合所使用 Visual Studio 版本的 [開發人員命令提示字元] 版本。

1. 在 [開發人員命令提示字元] 主控台視窗中，輸入 `cl arguments /TP filename.i` 命令。

1. 請確認已重現問題。

最後，將此重現附加到報表。

### <a name="link-repros"></a>連結重現

連結重現是包含組建成品的單一目錄，可共同示範連結時發生的問題，例如涉及連結時產生程式碼 (LTCG) 的後端損毀或連結器損毀；包含的組建成品就是連結器輸入所需的組建成品，以重現問題。 使用連結器所提供的功能，可以輕鬆地建立連結重現。

#### <a name="to-generate-a-link-repro"></a>產生連結重現

1. 開啟命令提示字元，然後輸入 `mkdir directory` 命令，為連結重現建立目錄。

1. 將 link_repro 環境變數設為您剛剛建立的目錄；輸入 `set link_repro=directory` 命令。

1. 如果您想要在 Visual Studio 內執行組建，請輸入 `devenv` 命令以從命令提示字元中啟動它。 這確保 Visual Studio 可以看到 link_repro 環境變數的值。

1. 建置應用程式，並確認發生預期的問題。

1. 如果您在步驟 3 啟動 Visual Studio，請立即關閉 Visual Studio。

1. 清除 link_repro 環境變數；輸入 `set link_repro=` 命令。

最後，將整個目錄壓縮成 .zip 檔案或類似檔案來封裝重現，並將它附加到報表。

### <a name="other-repros"></a>其他重現

如果您無法將問題減少為單一原始程式檔或前置處理過的重現，而且問題不需要連結重現，則我們可以調查 IDE 專案。 專案內的程式碼應該仍為最少，而且這份文件的所有指引都依然適用。

將重現建立為最少 IDE 專案，然後將整個目錄結構壓縮成 .zip 檔案或類似檔案以進行封裝，並將其附加至報表。

## <a name="send"></a> 報表的傳送方式

有幾種方式可以將您的報表送給我們。 您可以使用 Visual Studio 的內建[回報問題工具](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)，或 [Visual Studio 開發人員社群](https://developercommunity.visualstudio.com/)頁面。 您也可以透過電子郵件傳送報告，但建議您採取前兩種方式。 方法的選擇取決於您想要如何與調查報告的工程師互動，及是否要追蹤其進度或是否要與社群分享您的報告。

> [!NOTE]
> 不論您如何提交報表，Microsoft 都會尊重您的隱私權。 如需我們如何處理您所傳送之資料的相關資訊，請參閱 [Microsoft Visual Studio 產品系列隱私權聲明](https://www.visualstudio.com/dn948229)。

### <a name="use-the-report-a-problem-tool"></a>使用回報問題工具

Visual Studio 中的 [回報問題] 工具是 Visual Studio 使用者用來回報各種問題的方式，只要按幾下就可回報問題。 它提供簡單的表單以用來指定您所遇到問題的詳細資訊，然後提交報表，而不需要離開 IDE。

從 IDE 透過 [回報問題] 工具回報問題簡單又方便。 您可以選擇 [快速啟動] 搜尋方塊旁的**傳送意見反應**圖示從標題列存取這項工具，也可以在功能表列上的 [協助] > [傳送意見反應] > [回報問題] 中找到該工具。

當您選擇回報問題時，請先在開發人員社群中搜尋是否有類似問題。 如果其他人之前回報過相關問題，請附議主題並新增留言，提出具體細節。 如果您找不到類似問題，請選擇 Visual Studio 意見反應對話方塊底部的 [回報新問題] 按鈕，然後遵循這些步驟回報問題。

### <a name="use-the-visual-studio-developer-community-pages"></a>使用 Visual Studio 開發人員社群頁面

Visual Studio 開發人員社群頁面提供另一種方便的途徑，讓您回報 Visual Studio、C++ 編譯器、工具和程式庫的問題和尋找其解決方案。 [Visual Studio 問題](https://developercommunity.visualstudio.com/spaces/8/index.html)頁面可供您回報 IDE 或安裝問題。 若要回報 C++ 編譯器、連結器，及其他工具和程式庫的相關問題，則請使用 [C++ 問題](https://developercommunity.visualstudio.com/spaces/62/index.html)頁面。

在開發人員社群中，靠近每個頁面頂端的橫幅為搜尋方塊，您可用來尋找回報類似您問題的文章或主題。 您也許可在現有主題中發現到與您問題相關的解決方案或其他有用資訊。 如果其他人已回報過相同的問題，請附議該主題並留言，而非建立新的問題回報。

如果其他人未回報過該問題，請選擇開發人員社群頁面上搜尋方塊旁的 [回報問題] 按鈕。 系統可能會要求您登入 Visual Studio 帳戶，及同意將您設定檔的存取權授予開發人員社群應用程式。 登入後，您會直接前往可回報問題的頁面。 您可以包含您重新產生的程式碼和命令列、螢幕擷取畫面、相關討論的連結，及其他您認為相關且有用的任何資訊。

### <a name="send-an-email"></a>傳送電子郵件

電子郵件是將報告直接傳送給 Visual C++ 小組的另一種方式。 寄信到 [compilercrash@microsoft.com](mailto:compilercrash@microsoft.com) 即可與我們連絡。因為透過 [回報問題] 工具或網頁回報至開發人員社群的問題較能密切追蹤，而且透過電子郵件回報無法讓留言和解決方案供其他 Visual Studio 使用者參考，所以請只在無法使用其他兩種方式時，再使用此方式。

如果您選擇透過電子郵件傳送報表，則可以使用下列範本作為電子郵件訊息的本文。 如果您未在電子郵件本文中加入這項資訊，請不要忘了附加原始程式碼或其他檔案。

```Example
To: compilercrash@microsoft.com
Subject: Visual C++ Error Report
-----

Compiler version:

CL.EXE command line:

Problem description:

Source code and repro steps:

```

> [!TIP]
> 針對您可能會在 Visual Studio 中遇到與工具組無關的其他問題類型 (例如，UI 問題、中斷的 IDE 功能或一般當機)，回報問題工具可能是特別不錯的選擇，原因是其螢幕擷取畫面功能以及記錄導致您所遇到問題之 UI 動作的能力。 您應該永遠不透過寄送電子郵件至 compilercrash@microsoft.com 來回報這些其他類型的錯誤。

