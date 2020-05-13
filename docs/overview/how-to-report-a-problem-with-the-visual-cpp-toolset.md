---
title: 如何回報 Microsoft C++ 工具組問題
description: 如何為 Microsoft C++工具集創建一個良好的問題報告和重現資訊。
ms.date: 09/24/2019
ms.technology: cpp-ide
author: corob-msft
ms.author: corob
ms.openlocfilehash: 350e902501aca5cbe2b4022ec1f977719844644b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "71685704"
---
# <a name="how-to-report-a-problem-with-the-microsoft-c-toolset-or-documentation"></a>如何回報 Microsoft C++ 工具組或文件的問題

如果在 Microsoft C++ 編譯器 (MSVC)、連結器或其他工具和程式庫中發現問題，請告知我們。 如果問題是出自文件，也請告知我們。

## <a name="how-to-report-a-c-toolset-issue"></a>如何回報 C++ 工具組問題

讓我們知道問題的最佳方式是將一份內含描述所發現問題的報表傳送給我們。 該報告中應該有關於如何建置程式的所有詳細資料。 此外，也應該包含*重現*，以及可用來在我們自己的電腦上重現問題的完整測試案例。 這項資訊可讓我們快速確認問題是存在於程式碼，而不是環境本機的問題。 它可協助我們判斷是否影響其他版本的編譯器，並診斷其原因。

在下列各節中，您將了解如何建立良好的報表。 我們會描述如何針對您所發現的問題類型產生報表，以及如何將報表傳送給產品小組。 您的報表對我們和您這類其他開發人員而言十分重要。 感謝您協助我們改善 Microsoft C++！

## <a name="how-to-prepare-your-report"></a>如何準備報表

建立高品質的報表很重要，因為對我們來說，如果沒有完整的資訊，要重現您所發現的問題很困難。 您的報表越好，我們就越能更有效率地重新建立並診斷問題。

您的報表至少應該包含：

- 所使用工具組的完整版本資訊。

- 用來建置您程式碼的完整 cl.exe 命令列。

- 所發現問題的詳細描述。

- 重現：可示範問題的完整、簡化、獨立原始程式碼範例。

請閱讀以深入了解我們需要的特定資訊、可找到它的位置，以及如何建立良好重現。

### <a name="the-toolset-version"></a>工具組版本

我們需要完整版本資訊以及造成問題之工具組的目標架構。 如此我們能夠在我們的電腦上針對相同的工具組測試您的重現。 如果我們可以重現問題，這項資訊也會提供一個起點，讓我們調查哪些其他版本的工具組有相同的問題。

#### <a name="to-report-the-full-version-of-your-compiler"></a>回報您編譯器的完整版本

1. 開啟**開發人員命令提示字元**，以符合用來建置專案的 Visual Studio 版本和組態架構。 例如，如果您是針對 x64 目標使用 Visual Studio 2017 on x64 進行建置，則請選擇 [x64 Native Tools Command Prompt for VS 2017] (適用於 VS 2017 的 x64 Native Tools 命令提示字元)****。 如需詳細資訊，請參閱[開發人員命令提示字元捷徑](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)。

1. 在開發人員命令提示字元主控台視窗中，輸入 **cl /Bv** 命令。

輸出應該類似如下：

```Output
C:\Users\username\Source>cl /Bv
Microsoft (R) C/C++ Optimizing Compiler Version 19.14.26428.1 for x86
Copyright (C) Microsoft Corporation.  All rights reserved.

Compiler Passes:
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\cl.exe:        Version 19.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\c1.dll:        Version 19.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\c1xx.dll:      Version 19.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\c2.dll:        Version 19.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\link.exe:      Version 14.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\mspdb140.dll:  Version 14.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\1033\clui.dll: Version 19.14.26428.1

cl : Command line error D8003 : missing source filename
```

複製整個輸出，並將其貼入您的報表。

### <a name="the-command-line"></a>命令列

我們需要用來建置您程式碼的確切命令列 (cl.exe 和其所有引數)。 如此可以在我們的電腦上以完全相同的方式進行建置。 因為只有在使用特定引數或引數組合進行建置時才會存在您發現的問題，所以這十分重要。

找到這項資訊的最佳位置是在遇到問題之後那時的組建記錄檔。 這確保命令列包含可能造成問題的完全相同引數。

#### <a name="to-report-the-contents-of-the-command-line"></a>回報命令列內容

1. 找到並開啟 **CL.command.1.tlog** 檔案。 預設情況下,\\此檔案位於可檢視化工作室\\*版本*\\「*解決方案名稱*\\*專案名稱*\\ *」 專案*\\*名稱 「專案名稱*」 名稱 .tlog\\CL.指令.1.tlog" 中的「文件」 資料夾中\\, 或\\位於「\\源儲存庫*解決方案*\\*名稱專案名稱*\\ *」設定*\\*專案名稱*\\.tlog CL.command.1.tlog"下的「使用者」資料夾中。 如果您使用另一個組建系統，或已經變更您專案的預設位置，則它可能是在不同的位置。

   在此檔案內，您可以找到之後用來編譯原始程式碼檔之命令列引數的原始程式碼檔名稱，而且一行一個引數。

1. 找到包含發生問題之原始程式碼檔名稱的那一行。 該行下面的那一行會包含對應的 cl.exe 命令引數。

複製整個命令列，並將其貼入您的報表。

### <a name="a-description-of-the-problem"></a>問題描述

我們需要您所發現問題的詳細描述。 如此我們可以確認看到您電腦上的相同效果。 它有時也可讓我們知道您嘗試完成的作業以及預期發生的情況。

良好的描述可提供工具組所提供的**確切錯誤訊息**，或您看到的確切執行階段行為。 我們需要這項資訊來驗證我們已正確地重現問題。 請包含**所有**編譯器輸出，而不只是最後一個錯誤訊息。 我們需要查看導致您所回報問題的所有項目。 如果您可以使用命令列編譯器來複製問題，則會偏好使用該編譯器輸出。 IDE 和其他組建系統可以篩選您看到此項目，或只擷取錯誤訊息的第一行的錯誤訊息。

如果問題是編譯器接受無效的程式碼，而且未產生診斷，則請在報表中納入這一點。

若要報告執行階段行為問題，請包含程式所列印的**確切複本**，以及您預期看到的確切複本。 在理想情況下，您會將該複本內嵌在輸出陳述式本身中，例如，`printf("This should be 5: %d\n", actual_result);`。 如果您的程式當機或停止回應，則也會提及該問題。

新增可能有助於診斷所發現問題的其他任何詳細資料，例如您已經發現的任何因應措施。 請嘗試不要在報表的其他位置出現發現的重複資訊。

### <a name="the-repro"></a>重現

*重現*是完整且獨立的原始程式碼範例。 它會以重現方式示範您所發現的問題，因此會顯示名稱。 我們需要重現，才能在電腦上重現錯誤。 程式碼本身應該就足以建立可編譯和執行的基本可執行檔。 或*將*在不適用於您所發現問題時編譯和執行的簡單可執行檔。 重現不是程式碼片段。 它應該有完整的函式和類別，而且包含所有必要 #include 指示詞，即使針對標準標頭也是一樣。

#### <a name="what-makes-a-good-repro"></a>如何建立良好的重現

良好的重現為：

- **最小。** 重現應該越小越好，但仍然確切地示範您所發現的問題。 重現不需要複雜或實際。 它們只需要顯示符合 Standard 或所記載編譯器實作的程式碼。 如果缺少診斷，您的重現應該會顯示不一致的程式碼。 包含剛好足夠的程式碼來示範問題的簡單、重要重現最適合。 如果您可以排除或簡化程式碼並保持一致，同時將問題保持不變，則請這麼做。 您不需要包含適用的相反範例程式碼。

- **獨立。** 重現應該避免不必要的相依性。 如果您可以重現問題，而不需要協力廠商程式庫，則請這樣做。 如果您除了簡單的輸出陳述式 (例如，`puts("this shouldn't compile");`、`std::cout << value;` 和 `printf("%d\n", value);`) 之外，不需要任何程式庫程式碼即可重現問題，則請這麼做。 如果範例可以壓縮成單一原始程式碼檔，而未參考任何使用者標頭，則它十分適合。 減少視為可能造成問題的程式碼數量十分有幫助。

- **針對最新編譯器版本。** 如果可能的話，重現應該使用最新版本工具組的最新更新。 或者，使用下次更新的最新發行前版本或下一個主要版本。 在新版本中，通常已修正舊版工具組中所發現的問題。 只有在例外狀況下，修正程式才會往回移植到較舊的版本。

- **針對其他編譯器檢查** (如果相關)。 涉及可攜式 C++ 程式碼的報表應該確認其他編譯器行為 (可能的話)。 C++ Standard 最終會判斷程式正確性，而且沒有編譯器是完美的。 不過，當 Clang 和 GCC 接受沒有診斷的程式碼而 MSVC 不接受時，您可能會在我們的編譯器中發現一個 Bug。 (其他可能性包括 Unix 和 Windows 行為的差異,或不同級別的C++標準實現,等等。當所有編譯器拒絕您的代碼時,您的代碼很可能不正確。 查看不同的錯誤訊息可以協助您自行診斷問題。

   您可以在 ISO C++ 網站的[線上 C++ 編譯器](https://isocpp.org/blog/2013/01/online-c-compilers)中，或 GitHub 上這個策劃的[線上 C++ 編譯器清單](https://arnemertz.github.io/online-compilers/)，尋找線上編譯器清單來測試您的程式碼。 某些特定範例包含 [Wandbox](https://wandbox.org/)、[編譯器總管](https://godbolt.org/)和 [Coliru](https://coliru.stacked-crooked.com/)。

   > [!NOTE]
   > 線上編譯器網站未與 Microsoft 建立關聯。 許多線上編譯器網站都會當作個人專案執行。 在您閱讀這篇文章時，其中一些網站可能無法使用，但搜尋應該會發現您可以使用的其他網站。

編譯器、連結器和程式庫中的問題，傾向於以特定方式予以顯示。 您所發現問題的類型將決定應該包含在報表中的重現類型。 如果沒有適當的重現，我們就無法進行調查。 以下是您可能會看到的數種問題。 我們會包含如何產生您應該用來回報每種問題之重現類型的指示。

#### <a name="frontend-parser-crash"></a>前端 (剖析器) 損毀

前端損毀是在編譯器的剖析階段期間發生。 通常，編譯器會發出[嚴重錯誤 C1001](../error-messages/compiler-errors-1/fatal-error-c1001.md)，並參考發生錯誤所在的原始程式碼檔和行號。 它通常會提及一個名為 msc1.cpp 的檔案，但您可以忽略這個詳細資料。

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

#### <a name="backend-code-generation-crash"></a>後端 (程式碼產生) 損毀

後端損毀是在編譯器的程式碼產生階段期間發生。 通常，編譯器會發出[嚴重錯誤 C1001](../error-messages/compiler-errors-1/fatal-error-c1001.md)，而且它可能不會參考與問題相關聯的原始程式碼檔和行號。 它通常會提及檔案編譯器 \\utc\\src\\p2\\main.c，但是您可以忽略這個詳細資料。

針對這種損毀，如果您要使用由 cl.exe 的 **/GL** 命令列引數所啟用的連結時產生程式碼 (LTCG)，請提供[連結重現](#link-repros)。 否則，請改成提供[前置處理過的重現](#preprocessed-repros)。

以下是未使用 LTCG 這種後端損毀的範例編譯器輸出。 如果您的編譯器輸出看起來如下所示，則應該提供[前置處理過的重現](#preprocessed-repros)。

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

如果開頭為**編譯器內部錯誤**的行提及 link.exe，而非 cl.exe，則已啟用 LTCG。 在此情況下，請提供[連結重現](#link-repros)。 當不確定是否已從編譯器錯誤訊息啟用 LTCG 時，請檢查命令列引數。 您已經在 **/GL** 命令列引數的先前步驟中，從組建記錄檔複製它們。

#### <a name="linker-crash"></a>連結器損毀

連結器損毀是在執行編譯器後的連結階段期間發生。 連結器通常會發出[連結器工具錯誤 LNK1000](../error-messages/tool-errors/linker-tools-error-lnk1000.md)。

> [!NOTE]
> 如果輸出提及 C1001，或涉及連結時產生程式碼，請參閱[後端 (程式碼產生) 損毀](#backend-code-generation-crash)。

針對這種損毀，請提供[連結重現](#link-repros)。

以下是這種損毀的編譯器輸出範例：

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

如果已啟用累加連結，而且只有在成功初始連結之後才會發生損毀 (也就是，只有在後續累加連結所依據的第一個完整連結之後)，也請提供物件 (.obj) 和程式庫 (.lib) 檔案的複本，這些檔案必須對應到初始連結完成後經過修改的原始程式檔。

#### <a name="bad-code-generation"></a>產生錯誤的程式碼

產生錯誤的程式碼十分罕見。 當編譯器錯誤地產生不正確的程式碼讓您的應用程式在執行階段損毀時會發生這個情況。 但是，它應該產生正確的程式碼，或在編譯時期偵測問題。 如果您認為所發現的問題會導致產生錯誤的程式碼，請使用與[後端 (程式碼產生) 損毀](#backend-code-generation-crash)相同的方式來處理報表。

針對這種損毀，如果您要使用 cl.exe 的 **/GL** 命令列引數，請提供[連結重現](#link-repros)。 否則，請提供[前置處理過的重現](#preprocessed-repros)。

## <a name="how-to-generate-a-repro"></a>如何產生重現

為了協助追蹤問題來源，[良好重現](#what-makes-a-good-repro)十分重要。 執行下面針對特定重現類型所述的任何步驟之前，請嘗試盡可能緊縮示範問題的程式碼。 嘗試刪除或最小化相依性、必要標頭和程式庫。 盡可能地限制使用的編譯器選項和前置處理器定義。

以下是產生用來回報不同問題類型之各種重現類型的指示。

### <a name="preprocessed-repros"></a>前置處理過的重現

*前置處理過的重現*是單一原始程式檔，可示範問題。 它是從 C 前置處理器的輸出產生的。 若要建立一個前置處理過的重現，請使用原始重現原始程式檔上的 **/P** 編譯器選項。 此選項內嵌包含的標頭來移除其他原始程式檔和標頭檔的相依性。 此選項也會解析巨集、#ifdef 條件以及可能與您的本機環境相依的其他前置處理器命令。

> [!NOTE]
> 因為我們通常會想要替代最新進行中的實作，以查看我們是否已修正問題，所以對於可能是標準程式庫實作中 Bug 所造成的問題，前置處理過的重現不實用。 在此情況下，請不要前置處理重現，而且如果您無法將問題減少為單一原始程式檔，則請將程式碼封裝為 .zip 檔案或類似檔案，或考慮使用 IDE 專案重現。 如需詳細資訊，請參閱[其他重現](#other-repros)。

#### <a name="to-preprocess-a-source-code-file"></a>前置處理原始程式碼檔

1. 擷取用來建置重現的命令列引數，如[回報命令列內容](#to-report-the-contents-of-the-command-line)中所述。

1. 開啟**開發人員命令提示字元**，以符合用來建置專案的 Visual Studio 版本和組態架構。

1. 切換至包含重現專案的目錄。

1. 在開發人員命令提示字元主控台視窗中，輸入命令 **cl /P** *arguments* *filename.cpp*。 對於 *arguments*，請使用您上面所擷取的引數清單。 *filename.cpp* 是重現原始程式檔的名稱。 此命令會複寫用於重現的命令列，但在前置處理器通過後停止編譯。 接著，它會將前置處理過的原始程式碼寫入至 *filename.i*。

如果您要前置處理 C++/CX 原始程式碼檔案，或者要使用 C++ 模組功能，則需要執行一些其他步驟。 如需詳細資訊，請參閱以下節。

產生前置處理過的檔案之後，最好確定當您編譯前置處理過的檔案時，問題仍然會重現。

#### <a name="to-confirm-the-preprocessed-file-still-repros-the-error"></a>確認前置處理過的檔案仍然重現錯誤

1. 在開發人員命令提示字元主控台視窗中，輸入 **cl** *arguments* **/TP** *filename.i* 命令，以告訴 cl.exe 將前置處理過的檔案編譯為 C++ 原始程式檔。 *arguments* 與上面所擷取的相同引數，但已移除任何 **/D** 和 **/I** 引數。 這是因為它們已經包含在前置處理過的檔案中。 *filename.i* 是前置處理過的檔案的名稱。

1. 請確認已重現問題。

最後，將前置處理過的重現 *filename*.i 附加到報表中。

### <a name="preprocessed-ccx-winrtuwp-code-repros"></a>前置處理過的 C++/CX WinRT/UWP 程式碼重現

如果您要使用 C++/CX 來建置可執行檔，必須執行一些額外步驟，才能建立和驗證前置處理過的重現。

#### <a name="to-preprocess-ccx-source-code"></a>前置處理 C++/CX 原始程式碼

1. 建立前置處理過的原始程式檔，如[前置處理原始程式碼檔案](#to-preprocess-a-source-code-file)中所述。

1. 搜尋產生的 _filename_.i 檔案中是否有 **#using** 指示詞。

1. 製作所有參考檔案的清單。 請排除任何 Windows\*.winmd 檔案、platform.winmd 檔案和 mscorlib.dll。

若要準備驗證前置處理過的檔案仍會重現問題，請：

1. 為前置處理過的檔案建立新目錄，並將它複製到新目錄。

1. 將 **#using** 清單中的.winmd 檔案複製到新目錄。

1. 在新目錄中建立空白的 vccorlib.h 檔案。

1. 編輯前置處理過的檔案，以移除 mscorlib.dll 的任何 **#using** 指示詞。

1. 編輯前置處理過的檔案，將所有絕對路徑變更為複製之 .winmd 檔案的純檔名。

確認前置處理過的檔案仍會重現問題，如上所述。

### <a name="preprocessed-c-modules-repros"></a>前置處理過的 C++ 模組重現

如果您要使用 C++ 編譯器的模組功能，必須執行一些不同的步驟，才能建立和驗證前置處理過的重現。

#### <a name="to-preprocess-a-source-code-file-that-uses-a-module"></a>前置處理使用模組的原始程式碼檔案

1. 擷取用來建置重現的命令列引數，如[回報命令列內容](#to-report-the-contents-of-the-command-line)中所述。

1. 開啟**開發人員命令提示字元**，以符合用來建置專案的 Visual Studio 版本和組態架構。

1. 切換至包含重現專案的目錄。

1. 在開發人員命令提示字元主控台視窗中，輸入命令 **cl /P** *arguments* *filename.cpp*。 *arguments* 是上面所擷取的引數，而 *filename.cpp* 是取用模組的原始程式檔的名稱。

1. 切換至包含建置模組介面 ( .ifc 輸出) 所使用之重現專案的目錄。

1. 擷取用來建置模組介面的命令列引數。

1. 在開發人員命令提示字元主控台視窗中，輸入命令 **cl /P** *arguments* *modulename.ixx*。 *arguments* 是上面所擷取的引數，而 *filename.cpp* 是建立模組介面的檔案的名稱。

產生前置處理過的檔案之後，最好確定當您使用前置處理過的檔案時，問題仍然會重現。

#### <a name="to-confirm-the-preprocessed-file-still-repros-the-error"></a>確認前置處理過的檔案仍然重現錯誤

1. 在開發人員主控台視窗中，切換回包含您重現專案的目錄。

1. 如上所述輸入 **cl** *arguments* **/TP** *filename*.i 命令，以編譯前置處理過的檔案，就像它是 C++ 原始程式檔一樣。

1. 確認前置處理過的檔案仍會重現該問題。

最後，將前置處理過的重現檔案 (*filename*.i 和 *modulename*.i) 以及 .ifc 輸出附加到您的報表。

### <a name="link-repros"></a>連結重現

*連結重現*是目錄的連結到者生成的內容,由**鏈\_接 重現**環境變數指定,或作為[/LINKREPRO](../build/reference/linkrepro.md)連結器選項的參數指定。 它包含的組建成品可以統一示範在連結時發生的問題。 例如涉及連結時產生程式碼 (LTCG) 的後端損毀或是連結器損毀。 這些生成工件是連結器輸入所需的專案,因此可以重現問題。 使用此環境變數可以輕鬆創建連結重現。 它可啟用連結器的內建重現產生功能。

#### <a name="to-generate-a-link-repro-using-the-link_repro-environment-variable"></a>使用link_repro環境變數產生連結循環

1. 擷取用來建置重現的命令列引數，如[回報命令列內容](#to-report-the-contents-of-the-command-line)中所述。

1. 開啟**開發人員命令提示字元**，以符合用來建置專案的 Visual Studio 版本和組態架構。

1. 在開發人員命令提示字元主控台視窗中，切換至包含您重現專案的目錄。

1. 輸入**mkdir 連結重新pro**為連結重現創建名為*linkrepro*的目錄。 您可以使用其他名稱捕獲另一個連結重現。

1. 輸入 **set link\_repro=linkrepro** 命令，以便將 **link\_repro** 環境變數設為您所建立的目錄。 如果生成從其他目錄運行,就像更複雜的專案通常的情況一樣,則改為將指向連結 repro 目錄的完整路徑的**重新\_pro**設置為完整路徑。

1. 若要在 Visual Studio 中建置重現專案，請在開發人員命令提示字元主控台視窗中輸入 **devenv** 命令。 這確保 Visual Studio 可以看到 **link\_repro** 環境變數的值。 若要在命令列中建置專案，請使用上面擷取的命令列引數來複製重現組建。

1. 建置重現專案，並確認發生預期的問題。

1. 如果您已經使用 Visual Studio 來執行建置，則請予以關閉。

1. 在開發人員命令提示字元主控台視窗中，輸入 **set link\_repro=** 命令，以清除 **link\_repro** 環境變數。

最後,通過將整個 linkrepro 目錄壓縮到 .zip 檔案或類似檔,並將其附加到報表,從而打包 repro。

**/LINKREPRO**連結器選項的效果與**\_鏈接重現**環境變數的效果相同。 您可以使用[/LINKREPROTARGET 選項](../build/reference/linkreprotarget.md)指定要篩選生成連結重新pro 的名稱。 要使用 **/LINKREPROTARGET,** 還必須指定 **/OUT**連結器選項。

#### <a name="to-generate-a-link-repro-using-the-linkrepro-option"></a>使用 /LINKREPRO 選項產生連結循環

1. 建立一個目錄來保存連結重新專業。 我們將引用您創建為_目錄路徑_的完整目錄路徑。 如果路徑包含空格,則在路徑周圍使用雙引號。

1. 將 **/LINKREPRO:**_目錄路徑_命令添加到連結器命令列。 在可視化工作室中,打開專案**的屬性頁**對話框。 選擇**設定屬性** > **連結器** > **命令列**屬性頁。 然後,在 **「附加選項**」框中輸入 **/LINKREPRO:**_目錄路徑_選項。 選取 [確定]**** 儲存您的變更。

1. 建置重現專案，並確認發生預期的問題。

最後,通過將整個_目錄路徑_連結 repro 目錄壓縮到 .zip 檔或類似檔,並將其附加到報表,從而打包重現。

### <a name="other-repros"></a>其他重現

如果無法將問題減少到單個源檔或預處理的重現,並且該問題不需要連結重現,我們可以調查 IDE 專案。 有關如何創建良好重現的所有指南仍然適用:代碼應該是最小和自包含的。 我們的最新工具中應該會發生問題，而且如果相關，則問題應該不會出現在其他編譯器中。

將重現建立為最少 IDE 專案，然後將整個目錄結構壓縮成 .zip 檔案或類似檔案以進行封裝，並將其附加至報表。

## <a name="ways-to-send-your-report"></a>報表的傳送方式

有幾種不錯的方法可將您的報表送給我們。 您可以使用 Visual Studio 的內建[回報問題工具](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)，或 [Visual Studio 開發人員社群](https://developercommunity.visualstudio.com/)頁面。 此頁面底部也有一個 [產品意見反應]**** 按鈕。 選擇取決於您是否要在 IDE 中使用內建的工具擷取螢幕擷取畫面及組織您的報表。 如果您不想，可以直接使用開發人員社群網站。

> [!NOTE]
> 不論您如何提交報表，Microsoft 都會尊重您的隱私權。 Microsoft 致力於遵循所有資料的隱私權法律和規定。 如需我們如何處理您所傳送之資料的相關資訊，請參閱 [Microsoft 隱私權聲明](https://privacy.microsoft.com/privacystatement)。

### <a name="use-the-report-a-problem-tool"></a>使用回報問題工具

Visual Studio 中的 [回報問題]**** 工具是 Visual Studio 使用者用來回報問題的一種方式，只要按幾下滑鼠即可。 它會跳出一個簡單的表單來傳送您所發現問題的詳細資訊。 接著，您可以提交報表，而且不需要離開 IDE。

從 IDE 透過 [回報問題]**** 工具回報問題簡單又方便。 您可以選擇 [快速啟動]**** 搜尋方塊旁的 [傳送意見反應]**** 圖示，從標題列存取這項工具。 或者,您可以在 **「幫助** > **發送反饋** > **報告問題**」的功能表欄中找到它。

當您選擇回報問題時，請先在開發人員社群中搜尋是否有類似問題。 如果其他人之前回報過相關問題，請附議報表並新增留言，提出具體細節。 如果您找不到類似問題，請選擇 Visual Studio 意見反應對話方塊底部的 [回報新問題]**** 按鈕，然後遵循這些步驟回報問題。

### <a name="use-the-visual-studio-developer-community-pages"></a>使用 Visual Studio 開發人員社群頁面

Visual Studio 開發人員社群頁面提供另一種方便的途徑，讓您回報 Visual Studio 和 C++ 編譯器、工具和程式庫的問題和尋找其解決方案。 [Visual Studio](https://developercommunity.visualstudio.com/spaces/8/index.html)、[Visual Studio for Mac](https://developercommunity.visualstudio.com/spaces/41/index.html)、[.NET](https://developercommunity.visualstudio.com/spaces/61/index.html)、[C++](https://developercommunity.visualstudio.com/spaces/62/index.html)、[Azure DevOps Services](https://developercommunity.visualstudio.com/spaces/21/index.html) 和 [TFS](https://developercommunity.visualstudio.com/spaces/22/index.html) 都有特定的開發人員社群頁面。

在 [社群] 索引標籤底下，每個頁面頂端的附近有一個搜尋方塊。 您可以用它來尋找回報類似您問題的文章。 您也許可以找到與您問題相關的解決方案或其他有用資訊。 如果其他人已經回報過相同的問題，請附議該報表並留言，而非建立新的問題回報。 若要留言、投票或回報新問題，系統可能會要求您登入 Visual Studio 帳戶。 第一次登入時，您必須同意將您設定檔的存取權授與開發人員社群應用程式。

若要回報 C++ 編譯器、連結器，以及其他工具和程式庫的相關問題，則請使用 [C++](https://developercommunity.visualstudio.com/spaces/62/index.html) 頁面。 如果其他人未回報過您搜尋的問題，請選擇搜尋方塊旁的 [回報問題]**** 按鈕。 您可以包含您的重現程式碼和命令列、螢幕擷取畫面、相關討論的連結，及其他您認為相關且有用的任何資訊。

> [!TIP]
> 針對在 Visual Studio 中可能發現與 C++工具組無關的其他類型問題 (例如 UI 問題、損壞的 IDE 功能或常見當機)，請使用 IDE 中的 [回報問題]**** 工具。 這是最佳選擇，因為該工具有螢幕擷取畫面功能，並且能夠記錄導致您所發現問題的 UI 動作。 您也可以在[開發人員社群](https://developercommunity.visualstudio.com/)網站上尋找這類錯誤。 如需詳細資訊，請參閱[如何回報 Visual Studio 的問題](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)。

### <a name="reports-and-privacy"></a>報表和隱私權

**根據預設，報表中的所有資訊以及任何留言和回覆都是公開顯示的**。 一般來說，這是一項優點，因為它可讓整個社群查看問題、解決方案和其他使用者找到的因應措施。 不過，如果您基於隱私權或智慧財產權理由擔心會讓您的資料或身分公開，則可使用其他選項。

如果您擔心揭露您的身分，請[建立新的 Microsoft 帳戶](https://signup.live.com/)，這不會揭露關於您的任何詳細資料。 使用此帳戶來建立您的報表。

**請不要在公開的初始報表標題或內容中放置您想要保持私用的任何項目。** 但是，假設您會在個別的留言中私下傳送詳細資料。 為了確定您的報表會導向至適當的人員，請在問題報表的主題清單中包含 **cppcompiler**。 建立問題報表後，現在就能夠指定誰可以查看您的回覆和附件。

#### <a name="to-create-a-problem-report-for-private-information"></a>建立私人資訊的問題報表

1. 在建立的報表中，選擇 [新增留言]**** 來建立您對問題的私人描述。

1. 在回覆編輯器中，使用 [送出]**** 和 [取消]**** 按鈕下方的下拉式控制項來指定回覆的對象。 只有您指定的人員才能看到這些私人回覆以及其中包含的任何影像、連結或程式碼。 選擇 [可供仲裁者和原始貼文者檢視]**** 來限制 Microsoft 員工和您自己的可見性。

1. 新增描述，以及重現所需的任何其他資訊、影像和檔案附件。 選擇 [送出]**** 按鈕以私下傳送這些資訊。

   附加的檔案有 2GB 的限制，最多 10 個檔案。 對於任何較大的上傳項目，請在您的私人留言中要求一個上傳 URL。

這個留言底下的所有回覆都具有您指定的相同受限可見性。 即使回覆的下拉式控制項未正確顯示受限可見性狀態也是如此。

若要維護您的隱私權，並讓機密資訊不要公開檢視，請小心。 將所有與 Microsoft 的互動保持在這個受限留言下回覆。 對其他留言的回覆可能會導致您不小心公開機密資訊。

## <a name="how-to-report-a-c-documentation-issue"></a>如何回報 C++ 文件問題

我們使用 GitHub 問題來追蹤文件中所回報的問題。 您現在可以直接從內容頁建立 GitHub 問題，這可讓您以更豐富的方式與作者和產品小組互動。 如果您發現文件問題、錯誤的程式碼範例、造成混淆的說明、嚴重遺漏，或甚至只是錯字，，都可以輕鬆地通知我們。 請捲動至頁面底部，並選取 [登入以提供文件應見反應]****。 若您還沒有 GitHub 帳戶，您需要建立一個。 當您有 GitHub 帳戶時，您可以看到所有我們的文件問題及其狀態。 當您所回報的問題變更時，也會收到通知。 如需詳細資訊，請參閱[即將在 docs.microsoft.com 推出新的意見反應系統](/teamblog/a-new-feedback-system-is-coming-to-docs)。

當您使用文件的 [意見反應] 按鈕時，您可以在 GitHub 上建立文件問題。 該問題會自動填入有關建立問題來源頁面的一些資訊。 這是我們知道問題所在位置的方式，因此請勿編輯這項資訊。 只需要附加有關錯誤的詳細資料，如有必要，還可以提供建議的修正。 [我們的 C++ 文件是開放原始碼](https://github.com/MicrosoftDocs/cpp-docs/)，因此，如果您可以自行提交修正。 如需您可以如何參與文件的詳細資訊，請參閱我們在 GitHub 上的[參與指南](https://github.com/MicrosoftDocs/cpp-docs/blob/master/CONTRIBUTING.md) (英文)。
