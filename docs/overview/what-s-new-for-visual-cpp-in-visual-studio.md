---
title: Visual Studio 中 C++ 的新功能
ms.date: 05/19/2020
ms.technology: cpp-ide
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
ms.openlocfilehash: 28b3708c8064623a364b7a60eb63c508808b0a0b
ms.sourcegitcommit: 6e55aeb538b1c39af754f82d6f7738a18f5aa031
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87389996"
---
# <a name="whats-new-for-c-in-visual-studio"></a>Visual Studio 中 C++ 的新功能

::: moniker range=">=vs-2019"

Visual Studio 2019 有多個 Microsoft C++ 環境的更新與修正。 我們已修正編譯器和工具中的許多錯誤 (Bug) 與問題。 其中多是客戶透過 [傳送意見反應]**** 底下的 [回報問題](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019) 和 [提供建議](https://developercommunity.visualstudio.com/spaces/62/index.html) 選項提交而來。 感謝您回報 Bug！ 如需有關所有 Visual Studio 新功能的詳細資訊，請瀏覽 [Visual Studio 2019 的新功能](/visualstudio/ide/whats-new-visual-studio-2019)。 如需有關 Visual Studio 2017 中 C++ 新功能的資訊，請參閱 [Visual Studio 2017 中 C++ 的新功能](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2017)。 如需有關 Visual Studio 2015 和更舊版本中 C++ 新功能的資訊，請參閱[從 2003 到 2015 的 Visual C++ 新功能](/cpp/porting/visual-cpp-what-s-new-2003-through-2015)。

## <a name="c-compiler"></a>C++ 編譯器

- 增強支援 C++17 功能與正確性修正，加上 C++20 功能 (例如模組和協同程式) 的實驗性支援。 如需詳細資訊，請參閱 [Visual Studio 2019 中的 C++ 一致性改善](cpp-conformance-improvements.md)。

- `/std:c++latest`選項現在包含不一定完整的 c + + 20 功能，包括對三向比較之 c + + 20 運算子 \<=> （"太空船"）的初始支援。

- C++ 編譯器參數 `/Gm` 現已被取代。 若已明確定義 `/Gm` 參數，請考慮將它從您的組建指令碼中停用。 或者，您也可以安全地忽略 `/Gm` 的過時警告，因為當使用 [將警告視為錯誤] (`/WX`) 時不會將它視為錯誤。

- 隨著 MSVC 開始實作來自 C++20 標準版草稿的功能 (在 `/std:c++latest` 旗標下)，`/std:c++latest` 現在與 `/clr` (所有版本)、`/ZW` 與 `/Gm` 不相容。 在 Visual Studio 2019 中，當使用 `/clr`、`/ZW` 或 `/Gm` 編譯時，請使用 `/std:c++17` 或 `/std:c++14` 模式 (但請參閱先前的項目符號內容)。

- 根據預設，C++ 主控台和傳統型應用程式不再產生先行編譯標頭檔。

### <a name="codegen-security-diagnostics-and-versioning"></a>Codegen、安全性、診斷和版本控制

改善對 `/Qspectre` 的分析，以提供對 Spectre 變體 1 (CVE-2017-5753) 的風險降低協助。 如需詳細資訊，請參閱 [Spectre mitigations in MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/) (MSVC 中的 Spectre 風險降低)。

## <a name="c-standard-library-improvements"></a>C++ 標準程式庫改善

- 額外 C++17 與 C++20 程式庫功能與正確性修咒的實作。 如需詳細資訊，請參閱 [Visual Studio 2019 中的 C++ 一致性改善](cpp-conformance-improvements.md)。

- 我們已將 Clang 格式套用至 C++ 標準程式庫標頭，以改善可讀性。

- 因為 Visual Studio 現在針對 C++ 支援 Just My Code，因此標準程式庫再也不需要為 `std::function` 與 `std::visit` 提供自訂機器，就可以達到相同的效果。 大幅移除該機器對使用者沒有可見的影響。 其中一個例外狀況是編譯器不會再產生診斷，以指出或的第15732480行或16707566的問題 \<type_traits> \<variant> 。

## <a name="performancethroughput-improvements-in-the-compiler-and-standard-library"></a>編譯器和標準程式庫在效能/輸送量方面的改進

- 改善建置輸送量，包括連結器對檔案 I/O 的處理方式，以及合併與建立 PDB 類型的連結時間。

- 新增了 OpenMP SIMD 向量化的基本支援。 您可以使用新的編譯器參數來加以啟用 **`/openmp:experimental`** 。 此選項讓標註了 `#pragma omp simd` 的迴圈有機會向量化。 向量化並不保證會發生，而已標註但未向量化的迴圈會收到回報的警告。 不支援任何 SIMD 子句；系統會忽略這些子句並回報警告。

- 新增了內嵌命令列參數 **`/Ob3`** ，這是更積極的版本 **`/Ob2`** 。 **`/O2`**（將二進位檔優化以加快速度）仍 **`/Ob2`** 預設表示。 如果您發現編譯器不夠嚴格地內嵌，請考慮傳遞 **`/O2 -Ob3`** 。

- 我們已新增對簡短向量數學程式庫（SVML）內建函式的支援。 這些函式可計算 128 位元、256 位元或 512 位元的向量對等項目。 我們新增了這些專案，以支援以數學程式庫函式的呼叫來向量化迴圈，以及一些其他作業，例如整數除法。 若要了解支援函式的定義，請參閱 [Intel Intrinsic Guide](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#!=undefined&techs=SVML)。

- 新增及改進的最佳化：

  - 為使用 SIMD 向量內建函式的運算式提供常數摺疊和算數簡化，浮點數和整數形式均適用。

  - 有更強大的分析可從控制流程 (if/else/switch 陳述式) 擷取資訊，以移除總是證實為 true 或 false 的分支。

  - 改進了 memset 展開，以使用 SSE2 向量指令。

  - 改進了無用結構/類別複本的移除作業，尤其是依值傳遞的 C++ 程式。

  - 改進了使用 `memmove` 的程式碼最佳化，例如 `std::copy` 或 `std::vector` 及 `std::string` 建構。

- 已將標準程式庫的實體設計最佳化，以避免編譯未直接包含標準程式庫的部分。 這項變更會剪下只包含一半的空白檔案的組建時間 \<vector> 。 因此，您可能必須為先前間接包含的標頭加入 `#include` 指示詞。 例如，使用 `std::out_of_range` 的程式碼現在可能必須加入 `#include <stdexcept>`。 使用串流插入作業的程式碼現在可能必須加入 `#include <ostream>`。 其優點是只有實際使用 \<stdexcept> 或元件的轉譯單位會 \<ostream> 支付用來編譯它們的輸送量成本。

- `if constexpr` 已套用到標準程式庫中的更多位置，以便在複製作業、反向與旋轉的排列組合，以及平行演算法程式庫中，提高輸送量並降低程式碼大小。

- 標準程式庫現在會在內部使用 `if constexpr` 來減少編譯時間 (即使是在 C++14 模式中)。

- 平行演算法程式庫的執行階段動態連結偵測已不再使用整個頁面來存放函式指標陣列。 將此記憶體標示為唯讀已被視為與安全性目的不再相關。

- `std::thread` 的建構函式已不會再等候該執行緒啟動，而且已不會再於底層 C 程式庫 `_beginthreadex` 與提供的可呼叫物件之間插入這麼多層函式呼叫。 先前會 `std::thread` `_beginthreadex` 在和提供的可呼叫物件之間加上六個函式。 這個數位已縮減為只有三個，其中兩個只是 `std::invoke` 。 這項變更也會解決不明確的計時 bug，其中 `std::thread` 如果系統時鐘在建立時的確切時間變更，則會停止回應 `std::thread` 。

- 已修正 `std::hash` 中的效能迴歸，這是我們在實作 `std::hash<std::filesystem::path>` 時所引進的功能。

- 標準程式庫現在會在數個地方使用解構函式來達到正確性，而非使用 Catch 區塊。 這項變更會導致偵錯工具互動更佳：您透過受影響位置中的標準程式庫擲回的例外狀況，現在會顯示為從其原始擲回網站（而不是我們的重新引發 並非所有的標準程式庫 catch 區塊都已消除。 我們預期在較新的 MSVC 版本中，將會減少 catch 區塊的數目。

- `std::bitset` 中由 noexcept 函式內的條件式擲回導致的次佳 codegen 已透過鑽研出擲回路徑而修正。

- `std::list` 與 `std::unordered_*` 系列在內部的許多位置使用非偵錯列舉程式。

- 數個 `std::list` 成員已變更為儘可能重複使用清單節點，而非解除配置並重新配置它們。 例如，假設 `list<int>` 已有大小為3的，現在的呼叫會 `assign(4, 1729)` 覆寫前三個清單節點中的整數，並配置一個新的清單節點，其值為1729。

- 對 `erase(begin(), end())` 的所有標準程式庫呼叫都已變更為 `clear()`。

- `std::vector` n現在會在特定案例中以更有效率的方式初始化及擦除元素。

- 改善 `std::variant`，讓它更適用於更最佳化工具，以產生更好的程式碼。 現在，內嵌程式碼搭配 `std::visit` 的效果更好。

## <a name="c-ide"></a>C++ IDE

### <a name="live-share-c-support"></a>支援 Live Share C++

[Live Share](/visualstudio/liveshare/) 現已支援 C++，可讓開發人員使用 Visual Studio 或 Visual Studio Code 即時共同作業。 如需詳細資訊，請參閱[宣佈 c + + 的 Live Share：即時共用和](https://devblogs.microsoft.com/cppblog/cppliveshare/)共同作業

### <a name="intellicode-for-c"></a>適用於 C++ 的 IntelliCode

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 16.1 版

IntelliCode 會使用自己的廣泛訓練和您的程式碼內容，將您最有可能使用的內容放在完成清單的最上方。 它通常不需要向下捲動清單。 針對 C++，當您使用標準程式庫之類的熱門程式庫時，IntelliCode 的幫助最大。 IntelliCode 是選擇性的擴充功能，可做為安裝程式中的工作負載元件。 如需詳細資訊，請參閱 [AI-Assisted Code Completion Suggestions Come to C++ via IntelliCode](https://devblogs.microsoft.com/cppblog/cppintellicode/) (透過 IntelliCode 可實現 C++ 的 AI 輔助程式碼完成建議)。

### <a name="template-intellisense"></a>範本 IntelliSense

**範本列**現在使用**瞄孔 Window** UI 來取代強制回應視窗、支援巢狀範本，並會將任何預設引數預先填入**瞄孔視窗**中。 如需詳細資訊，請參閱 [Template IntelliSense Improvements for Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/template-intellisense-improvements-for-visual-studio-2019-preview-2/) (Visual Studio 2019 Preview 2 的範本 IntelliSense 改善)。 **範本列**中的 [最近使用]**** 下拉式清單，可讓您在前一組範例引數之間快速切換。

### <a name="new-start-window-experience"></a>新的啟動視窗體驗

啟動 IDE 時，會出現新的開始視窗。 它有選項可開啟最近使用的專案、從原始檔控制複製程式碼、將本機程式碼開啟為方案或資料夾，或建立新的專案。 [新增專案] 對話方塊也大幅修改為易於搜尋的可篩選體驗。

### <a name="new-names-for-some-project-templates"></a>部分專案範本的新名稱

我們已修改數個專案範本名稱與描述，以符合更新的 [新增專案] 對話方塊。

### <a name="various-productivity-improvements"></a>各種生產力改善功能

Visual Studio 2019 包含的下列功能可協助您更輕鬆且更直覺地撰寫程式碼：

- 快速修正：
  - 新增遺漏的 #include
  - 將 NULL 修正為 nullptr
  - 加入遺漏的分號
  - 解決遺漏命名空間或範圍的問題
  - 取代不正確的間接取值運算元 (\* to & and & to \*)
- 將滑鼠游標停留在右括號，可顯示區塊的快速諮詢
- 瞄孔標頭/程式碼檔
- #include 的 [移至定義] 可開啟檔案

如需詳細資訊，請參閱 [C++ Productivity Improvements in Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/c-productivity-improvements-in-visual-studio-2019-preview-2/) (Visual Studio 2019 Preview 2 中的 C++ 生產力改善功能)。

### <a name="quickinfo-improvements"></a>QuickInfo 增強功能

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 16.1 版

快速諮詢工具提示現在會遵守您編輯器的語意色彩標示。 它也有新的**線上搜尋**連結，此連結可用來搜尋線上文件以深入了解動態顯示程式碼建構。 Squiggled 程式碼的 [快速諮詢] 所提供的連結將會在線上搜尋錯誤。 如此一來，您就不需要在瀏覽器中重新輸入訊息。 如需詳細資訊，請參閱[Visual Studio 2019：顏色標示和線上搜尋中的快速資訊改進](https://devblogs.microsoft.com/cppblog/quick-info-improvements-in-visual-studio-2019-colorization-and-search-online/)。

### <a name="intellicode-available-in-c-workload"></a>IntelliCode 可在 C++ 工作負載中找到

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 16.1 版

IntelliCode 現在是以「使用 C++ 的桌面開發」**** 工作負載中的選擇性元件形式提供。 如需詳細資訊，請參閱[改良了C++ IntelliCode 現在隨附於 Visual Studio 2019](https://devblogs.microsoft.com/cppblog/improved-c-intellicode-now-ships-with-visual-studio-2019/)。

## <a name="cmake-support"></a>CMake 支援

- CMake 3.14 的支援

- Visual Studio 現在可以開啟外部工具所產生的現有 CMake 快取，例如 CMakeGUI、自訂的中繼組建系統，或可自動叫用 cmake.exe 的組建指令碼。

- 改善的 IntelliSense 效能。

- 新的設定編輯器可當成手動編輯 CMakeSettings.json 檔的替代方式，而且與 CMakeGUI 有部分同位。

- Visual Studio 藉由偵測您的 Linux 電腦上是否有相容的 CMake 版本，協助您在 Linux 上使用 CMake 啟動 C++ 開發。 若沒有，則會為您安裝。

- CMakeSettings 中不相容的設定 (例如不相符的架構或不相容的 CMake 產生器設定) 會在 JSON 編輯器中顯示波浪線，並在錯誤清單中顯示錯誤。

- 只要執行了 `vcpkg integrate install`，就會為 IDE 中開啟的 CMake 專案自動偵測和啟用 vcpkg 工具鏈。 您可透過在 CMakeSettings 中指定空白的工具鏈檔案來關閉這個行為。

- 根據預設，CMake 現在會啟用 Just My Code 偵錯。

- 靜態分析警告現在會在背景中處理，並顯示在 CMake 專案的編輯器中。

- 為 CMake 專案新增了更清楚的建置及設定「開始」和「結束」訊息，及 Visual Studio 建置進度 UI 的支援。 此外，[工具] > [選項]**** 中現在有 CMake 詳細資訊設定，可用來自訂輸出視窗中的 CMake 組建詳細等級及設定訊息。

- CMakeSettings.json 中現在支援 `cmakeToolchain` 設定，不必手動修改 CMake 命令列就能指定工具鏈。

- 新增 [全部建置]**** 功能表捷徑 **Ctrl+Shift+B**。

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 16.1 版

- 對使用 Clang/LLVM 編輯、建置及針對 CMake 專案進行偵錯的整合式支援。 如需詳細資訊，請參閱 [Visual Studio 中的 Clang/LLVM 支援](https://devblogs.microsoft.com/cppblog/clang-llvm-support-in-visual-studio/) \(英文\)。

## <a name="linux-and-the-windows-subsystem-for-linux"></a>Linux 和適用於 Linux 的 Windows 子系統

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 16.1 版

- 對 Linux 中之 [AddressSanitizer (ASan)](https://github.com/google/sanitizers/wiki/AddressSanitizer) 與 CMake 跨平台專案的支援。 如需詳細資訊，請參閱 [Visual Studio 2019 中Linux 工作負載的 AddressSanitizer (ASan)](https://devblogs.microsoft.com/cppblog/addresssanitizer-asan-for-the-linux-workload-in-visual-studio-2019/) \(英文\)。

- 使用適用於 Linux 的 Windows 子系統 (WSL) 時對使用 C++ 的整合式 Visual Studio 支援。 如需詳細資訊，請參閱[使用 Visual Studio 2019 與適用於 Linux 的 Windows 子系統 (WSL) 的 C++](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/) \(英文\)。

## <a name="incredibuild-integration"></a>IncrediBuild 整合

IncrediBuild 現在是以「使用 C++ 的桌面開發」**** 工作負載中的選擇性元件形式提供。 IncrediBuild 建置監視器已完全整合在 Visual Studio IDE 中。 如需詳細資訊，請參閱[使用 IncrediBuild 的組建監視器來視覺化組建和 Visual Studio 2019](https://devblogs.microsoft.com/cppblog/visualize-your-build-with-incredibuilds-build-monitor-and-visual-studio-2019/)。

## <a name="debugging"></a>偵錯

- 針對在 Windows 上執行的 C++ 應用程式，PDB 檔案現在會在個別的 64 位元處理序上載入。 這項變更解決了因偵錯工具記憶體不足所造成的損毀範圍。 例如，當您對包含大量模組和 PDB 檔案的應用程式進行偵錯工具時。

- 搜尋已在 [監看式]****、[自動變數]**** 與 [區域變數]**** 視窗中啟用。

## <a name="windows-desktop-development-with-c"></a>使用 C++ 進行 Windows 桌面開發

- 下列 C++ ATL/MFC 精靈已無法再使用：

  - ATL COM+ 1.0 元件精靈
  - ATL 動態伺服器網頁元件精靈
  - ATL OLE DB 提供者精靈
  - ATL 屬性頁精靈
  - ATL OLE DB 消費者精靈
  - MFC ODBC 消費者
  - 來自 ActiveX 控制項的 MFC 類別
  - 來自 Type Lib 的 MFC 類別。

  這些技術的範例程式碼封存於 Microsoft Docs 和 VCSamples GitHub 存放庫。

- Visual Studio 安裝程式中已不再提供 Windows 8.1 軟體發展工具組（SDK）。 建議您將 C++ 專案升級到最新 Windows 10 SDK。 若您有 8.1 的強式相依性，可從 Windows SDK 封存加以下載。

- 最新的 C++ 工具組無法再將 Windows XP 設為目標。 仍支援 VS 2017 級 MSVC 編譯器與程式庫的 XP 目標設定，並可透過「個別元件」安裝。

- 我們的文件積極勸阻您對 Visual C++ 執行階段部署使用合併模組。 我們在這個版本更進一步淘汰了 MSM。 請考慮將您的 VCRuntime 集中部署從 MSM 移轉到可轉散發套件。

## <a name="mobile-development-with-c-android-and-ios"></a>使用 C++ 進行行動裝置應用程式開發 (Android 與 iOS)

C++ Android 體驗現在預設為 Android SDK 25 與 Android NDK 16b。

## <a name="clangc2-platform-toolset"></a>Clang/C2 平台工具組

已移除 Clang/C2 實驗性元件。 針對具有 `/permissive-` 和 `/std:c++17` 的完整 C++ 標準一致性使用 MSVC 工具集，或針對 Windows 使用 Clang/LLVM 工具鏈。

## <a name="code-analysis"></a>程式碼分析

- 程式碼分析現在會在背景自動執行。 警告會在您鍵入的同時，在編輯器內以綠色波浪線顯示。 如需詳細資訊，請參閱 [In-editor code analysis in Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/in-editor-code-analysis-in-visual-studio-2019-preview-2/) (Visual Studio 2019 Preview 2 編輯器中的程式碼分析)。

- 來自標頭的知名標準程式庫類型的新實驗性 ConcurrencyCheck 規則 \<mutex> 。 如需詳細資訊，請參閱 [Concurrency Code Analysis in Visual Studio 2019](https://devblogs.microsoft.com/cppblog/concurrency-code-analysis-in-visual-studio-2019/) (Visual Studio 2019 中的並行程式碼分析)。

- [存留期設定檔檢查程式](https://herbsutter.com/2018/09/20/lifetime-profile-v1-0-posted/)已更新的部分實作，可偵測懸置的指標和參考。 如需詳細資訊，請參閱 [Lifetime Profile Update in Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/lifetime-profile-update-in-visual-studio-2019-preview-2/) (Visual Studio 2019 Preview 2 中的存留期設定檔更新)。

- 更多協同程式相關的檢查，包括 C26138、C26810、C26811 和實驗性規則 C26800。 如需詳細資訊，請參閱 [New Code Analysis Checks in Visual Studio 2019: use-after-move and coroutine](https://devblogs.microsoft.com/cppblog/new-code-analysis-checks-in-visual-studio-2019-use-after-move-and-coroutine/) (Visual Studio 2019 中的新程式碼分析檢查：use-after-move 和協同程式)。

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 16.1 版

- 針對已解除初始化之變數檢查的新快速修正程式。 如需詳細資訊，請參閱[適用於已解除初始化之記憶體 (C6001) 並使用 before init (C26494) 警告的新程式碼分析快速修正程式](https://devblogs.microsoft.com/cppblog/new-code-analysis-quick-fixes-for-uninitialized-memory-c6001-and-use-before-init-c26494-warnings/) \(英文\)。

## <a name="unit-testing"></a>單元測試

不再提供 Managed C++ 測試專案範本。 您可以繼續在現有的專案中使用受控 C++ 測試架構。 對於新的單元測試，請考慮使用 Visual Studio 有提供範本 (MSTest、Google Test) 或受控 C# 測試專案範本的其中一個原生測試架構。

::: moniker-end

::: moniker range="=vs-2017"

Visual Studio 2017 有多個 C++ 環境的更新與修正。 我們已修正編譯器和工具中超過250個 bug 和回報的問題。 許多都是由客戶透過回報[問題，並](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2017)在 [**傳送意見**反應] 下提供建議選項來提交。 感謝您回報 Bug！ 如需有關所有 Visual Studio 新功能的詳細資訊，請參閱 [Visual Studio 2017 的新功能](/visualstudio/ide/whats-new-visual-studio-2017?view=vs-2017)。 如需有關 Visual Studio 2019 中 C++ 新功能的資訊，請參閱 [Visual Studio 中 C++ 的新功能](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2019)。 如需有關 Visual Studio 2015 和更舊版本中 C++ 新功能的資訊，請參閱[從 2003 到 2015 的 Visual C++ 新功能](/cpp/porting/visual-cpp-what-s-new-2003-through-2015)。

## <a name="visual-studio-2017-c-compiler"></a>Visual Studio 2017 c + + 編譯器

### <a name="c-conformance-improvements"></a>C++ 一致性改善

我們已在此版本中更新 c + + 編譯器和標準程式庫，並增強對 c + + 11 和 c + + 14 功能的支援。 它也包括對 c + + 17 標準中預期的特定功能的初步支援。 如需詳細資訊，請參閱 [Visual Studio 2017 中的 C++ 一致性改善](cpp-conformance-improvements.md)。

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 15.5 版

編譯器支援 c + + 17 中新的75% 的功能，包括結構化系結、 **`constexpr`** lambda、 `if constexpr` 、內嵌變數、折迭運算式，以及將新增 **`noexcept`** 至型別系統。 這些功能可以在選項下取得 **`/std:c++17`** 。 如需詳細資訊，請參閱[Visual Studio 2017 中的 c + + 一致性改進](cpp-conformance-improvements.md)

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 15.7 版

Visual Studio 15.7 版中的 MSVC 編譯器工具組現在符合 C++ 標準。 如需詳細資訊，請參閱[宣佈： MSVC 符合 c + + 標準](https://devblogs.microsoft.com/cppblog/announcing-msvc-conforms-to-the-c-standard/)和[Microsoft c + + 語言一致性](../visual-cpp-language-conformance.md)。

##### <a name="visual-studio-2017-version-158"></a>Visual Studio 2017 15.8 版

[`/experimental:preprocessor`](../build/reference/experimental-preprocessor.md)編譯器參數會啟用新的實驗性 MSVC 預處理器，最後會符合所有適用的 C 和 c + + 標準。 如需詳細資訊，請參閱[MSVC 實驗性預處理器總覽](../preprocessor/preprocessor-experimental-overview.md)。

### <a name="new-compiler-options"></a>新的編譯器選項

- [`/permissive-`](../build/reference/permissive-standards-conformance.md)：啟用所有嚴格的標準一致性編譯器選項，並停用大部分的 Microsoft 特定編譯器擴充功能（例如，而不是 `__declspec(dllimport)` ）。 在 Visual Studio 2017 15.5 版中，此選項預設為開啟。  **`/permissive-`** 一致性模式包含對兩階段名稱查閱的支援。 如需詳細資訊，請參閱[Visual Studio 中的 c + + 一致性改進](cpp-conformance-improvements.md)。

- [`/diagnostics`](../build/reference/diagnostics-compiler-diagnostic-options.md)：可讓您以三種不同的方式顯示診斷錯誤或警告位置：只有行號、行號和資料行，或行號和欄，並在違規的程式程式碼底下加上插入點。

- [`/debug:fastlink`](../build/reference/debug-generate-debug-info.md)：藉由不將所有的偵錯工具資訊複製到 PDB 檔案，讓累加連結時間更快（與 Visual Studio 2015）達到最高30%。 PDB 檔案改為指向用來建立可執行檔之物件和程式庫檔案的偵錯資訊。 請參閱[VS "15" 中更快的 c `/Debug:fastlink` + + 組建週期](https://devblogs.microsoft.com/cppblog/faster-c-build-cycle-in-vs-15-with-debugfastlink/)，並提供[建議，以 Visual Studio 中加速 c + + 組建](https://devblogs.microsoft.com/cppblog/recommendations-to-speed-c-builds-in-visual-studio/)。

- Visual Studio 2017 允許搭配 [`/sdl`](../build/reference/sdl-enable-additional-security-checks.md) 使用 [`/await`](../build/reference/await-enable-coroutine-support.md) 。 我們已移除 [`/RTC`](../build/reference/rtc-run-time-error-checks.md) 協同程式的限制。

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 15.3 版

- [ `/std:c++14` 和 `/std:c++latest` ](../build/reference/std-specify-language-standard-version.md)：這些編譯器選項可讓您在專案中加入特定版本的 ISO c + + 程式設計語言。 最新的草稿標準功能會受到選項的保護 **`/std:c++latest`** 。

- [`/std:c++17`](../build/reference/std-specify-language-standard-version.md)啟用編譯器所執行的 c + + 17 功能集。 這個選項會停用 c + + 17 之後的編譯器和標準程式庫支援：在較新的工作草稿版本中變更或新增的功能，以及 c + + 標準的瑕疵更新。 若要啟用這些功能，請使用 **`/std:c++latest`** 。

### <a name="codegen-security-diagnostics-and-versioning"></a>Codegen、安全性、診斷和版本控制

此版本為最佳化、程式碼產生、工具組版本控制，以及診斷方面帶來多項改善。 其中幾項值得注意的改善內容包括：

- 改善重複的程式碼產生：支援常數整數除法的自動向量化，更容易識別 memset 模式。
- 改良的程式碼安全性：改善緩衝區溢位編譯器診斷的發出，並 [`/guard:cf`](../build/reference/guard-enable-control-flow-guard.md) 現在保護產生跳躍表的 switch 語句。
- 版本設定：內建預處理器宏** \_ MSC \_ VER**的值現在會在每個 Visual C++ 工具組更新時進行單純更新。 如需詳細資訊，請參閱 [Visual C++ Compiler Version](https://devblogs.microsoft.com/cppblog/visual-c-compiler-version/) (Visual C++ 編譯器版本)。
- 新的工具組版面配置︰編譯器和相關建置工具在開發電腦上具有新的位置和目錄結構。 新的版面配置可並存安裝多個版本的編譯器。 如需詳細資訊，請參閱 [Visual Studio 2017 中的編譯器工具版面配置](https://devblogs.microsoft.com/cppblog/compiler-tools-layout-in-visual-studio-15/) \(英文\)。
- 改善的診斷：輸出視窗現在會顯示發生錯誤的資料行。 如需詳細資訊，請參閱[VS "15" Preview 5 中的 c + + 編譯器診斷改善](https://devblogs.microsoft.com/cppblog/c-compiler-diagnostics-improvements-in-vs-15-rc/)。
- 使用協同程式時，已移除實驗關鍵字**yield** （可在 **`/await`** 選項下取得）。 您應該更新程式碼以改用 `co_yield`。 如需詳細資訊，請參閱[ `yield` 要 `co_yield` 在 VS 2017 中變成的關鍵字](https://devblogs.microsoft.com/cppblog/yield-keyword-to-become-co_yield-in-vs-2017/)。

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 15.3 版

對編譯器中診斷的其他改善。 如需詳細資訊，請參閱 [Visual Studio 2017 15.3.0 中的診斷改善](https://devblogs.microsoft.com/cppblog/diagnostic-improvements-in-vs2017-15-3-0/) \(英文\)。

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 15.5 版

Visual C++ 的執行時間效能會透過更好的產生程式碼品質繼續改善。 現在您可以只重新編譯程式碼，而且您的應用程式執行速度會更快。 某些編譯器最佳化功能是全新的，例如條件式純量存放區的向量化、將 `sin(x)` 和 `cos(x)` 呼叫合併成新的 `sincos(x)`，以及從 SSA 最佳化工具排除多餘的指令。 其他編譯器優化會改善現有的功能，例如：向量化工具條件運算式的啟發學習法、更佳的迴圈優化，以及 float min/max codegen。 連結器具有全新且更快速的 **`/OPT:ICF`** 執行方式，這可能會導致最多9% 的連結時間加速，而且在增量連結中有其他效能修正。 如需詳細資訊，請參閱 [/OPT (Optimizations)](../build/reference/opt-optimizations.md) (/OPT (最佳化)) 和 [/INCREMENTAL (Link Incrementally)](../build/reference/incremental-link-incrementally.md) (/INCREMENTAL (以累加方式連結))。

Microsoft c + + 編譯器支援 Intel 的 AVX-512。 其具有向量長度指示，可將 AVX-512 中的新函式帶入128位和 256-bit 寬暫存器。

在一般情況下使用 c + + 17 模式時，可以使用[/zc： noexceptTypes-](../build/reference/zc-noexcepttypes.md)選項來還原為 c + + 14 版的 **`noexcept`** 。 此選項可讓您更新原始程式碼以符合 C++17，而不需要同時重寫所有 `throw()` 程式碼。 如需詳細資訊，請參閱[動態例外狀況規格移除和 noexcept](cpp-conformance-improvements.md#noexcept_removal)。

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 15.7 版

- 新的編譯器參數[/Qspectre](../build/reference/qspectre.md)有助於緩和理論式執行端通道攻擊。 如需詳細資訊，請參閱[MSVC 中的 Spectre 緩和措施](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/)。
- 適用於 Spectre 風險降低的新診斷警告。 如需詳細資訊，請參閱 [Visual Studio 2017 15.7 版 Preview 4 中的 Spectre 診斷](https://devblogs.microsoft.com/cppblog/spectre-diagnostic-in-visual-studio-2017-version-15-7-preview-4/) \(英文\)。
- /Zc 的新值會 **`/Zc:__cplusplus`** 啟用 c + + 標準支援的正確報告功能。 例如，設定參數且編譯器處於模式時， **`/std:c++17`** 值會展開為 **`201703L`** 。 如需詳細資訊，請參閱 [MSVC 現在會正確報告 __cplusplus](https://devblogs.microsoft.com/cppblog/msvc-now-correctly-reports-__cplusplus/) \(英文\)。

## <a name="c-standard-library"></a>C++ 標準程式庫

### <a name="correctness-improvements"></a>正確性改善

##### <a name="visual-studio-2017-rtm-version-150"></a>Visual Studio 2017 RTM (15.0 版)

- 次要 `basic_string` `_ITERATOR_DEBUG_LEVEL != 0` 診斷改善。 當字串機制中的 IDL 檢查被取出時，它現在會報告造成旅程的特定行為。 例如，您會看見「無法為字串迭代器取值，因為它超出範圍 (例如結尾迭代器)」，而不是「無法為字串迭代器取值」。
- 修正了 `std::promise` 移動指派運算子原本可能造成程式碼永久封鎖的問題。
- 修正了 `atomic<T*>` 隱含轉換為 `T*` 這項編譯器錯誤。
- `pointer_traits<Ptr>` 現在會正確偵測 `Ptr::rebind<U>`。
- 已修正 **`const`** 減法運算子中遺漏的限定詞 `move_iterator` 。
- 修正了要求 `propagate_on_container_copy_assignment` 和 `propagate_on_container_move_assignment` 的具狀態使用者定義配置器會產生錯誤程式碼而不發出訊息的問題。
- `atomic<T>` 現已容許多載 `operator&()`。
- 稍微改善不正確 `bind()` 呼叫的編譯器診斷。

Visual Studio 2017 RTM 中有更多標準程式庫改良功能。 如需完整清單，請參閱[VS 2017 RTM 中](https://devblogs.microsoft.com/cppblog/stl-fixes-in-vs-2017-rtm/)的 c + + Team Blog 專案標準程式庫修正。

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 15.3 版

- 標準程式庫容器現在將其 `max_size()` 包含至 `numeric_limits<difference_type>::max()` 中，而不是包含在 `size_type` 的 `max()` 中。 此變更可確保該容器迭代器上 `distance()` 的結果能以 `distance()` 的傳回類型代表。
- 修正了缺少特舒化 `auto_ptr<void>` 的問題。
- `for_each_n()` `generate_n()` `search_n()` 如果 length 引數不是整數類資料類型，則先前無法編譯、和演算法。 它們現在會嘗試將非整數長度轉換成反覆運算器」 `difference_type` 。
- `normal_distribution<float>` 不會再於標準程式庫內對從雙精確度縮減為浮點數的情況發出警告。
- 修正了部分 `basic_string` 作業，這些作業先前在檢查大小溢位上限時會使用 `npos` 而非 `max_size()`。
- `condition_variable::wait_for(lock, relative_time, predicate)`如果有偽喚醒，會等待整個相對時間。 現在它只會等候相對時間的單一間隔。
- 依標準的規定，`future::get()` 現在會使 `future` 無效。
- 因 `iterator_traits<void *>` 之前會嘗試形成 `void&`，而成為硬碟錯誤，現在則會完全成為空的結構，以允許在 "is iterator" SFINAE 條件中使用 `iterator_traits`。
- 已修正 Clang **-wsystem-headers 標頭**所報告的一些警告。
- 也已修正「宣告中的例外狀況規格不符合 Clang **-Wmicrosoft-exception-spec**所回報的先前宣告」。
- 同時已修正由 Clang 和 C1XX 所回報的 mem-initializer-list 排序錯誤。
- 先前未排序的容器在容器本身已交換的情況下，並不會交換其 hasher 函式或述詞。 現在它們已會這麼做。
- 許多容器交換作業現在都會標示 **`noexcept`** （因為我們的標準程式庫在偵測非不相等配置器未定義的行為條件時，永遠不會擲回例外 `propagate_on_container_swap` 狀況）。
- `vector<bool>`現在已將許多作業標示為 **`noexcept`** 。
- 標準程式庫現在會強制將配置器 `value_type` (在 C++17 模式中) 與退出安全出口配對。
- 修正了對 `basic_string` 進行 self-range-insert 會擾亂字串內容的某些條件。 (注意：針對 vectors 進行 self-range-insert 仍受標準所禁止)。
- `basic_string::shrink_to_fit()` 不再受配置器的 `propagate_on_container_swap` 影響。
- `std::decay`現在會處理不受歡迎的函式類型，也就是 cv 限定的函數類型、ref 限定的，或兩者。
- 已變更 include 指示詞以使用適當的區分大小寫和斜線，以改善可攜性​​。
- 修正了警告 C4061「case 標籤未明確處理列舉 '*enumeration*' 參數中的列舉程式 '*enumerator*'」。 此警告為 off-by-default，並已修正為標準程式庫針對警告之一般原則的例外狀況  （標準程式庫是 **`/W4`** 乾淨的，但不會嘗試 **`/Wall`** 清除。 許多預設的關閉警告都是異常雜訊，不適合定期使用。）
- 改善 `std::list` 偵錯檢查。 List 迭代器現在會檢查 `operator->()`，且 `list::unique()` 現在會將迭代器標示為無效。
- 修正了 `tuple` 中的 uses-allocator 中繼程式設計。

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 15.5 版

- `std::partition`現在會呼叫 `N` 述詞時間，而不是 `N + 1` 時間，如標準所需。
- 在 15.5 版中，已修復 15.3 版中嘗試避免使用魔術靜態這項問題。
- `std::atomic<T>` 不再要求 `T` 必須預設為可建構的。
- 當反覆運算器進行偵錯工具啟用時，採用對數時間的堆積演算法會以不同的方式運作。 它們不會再執行線性時間判斷提示，因為輸入實際上是堆積。
- `__declspec(allocator)` 現在只會為 C1XX 而防護，以防止 Clang 不了解此 declspec 而發出警告。
- `basic_string::npos` 現在可作為編譯時間常數。
- `std::allocator`在 c + + 17 模式中，現在可以適當地處理過度對齊類型的配置，也就是，其對齊大於的類型， `max_align_t` 除非已停用 **`/Zc:alignedNew-`** 。  例如，具有 16 位元組或 32 位元組對齊的物件向量現在會正確對齊 SSE 和 AVX 指令。

### <a name="conformance-improvements"></a>一致性改善

- 我們已新增 \<any\> 、 \<string_view\> 、 `apply()` 、 `make_from_tuple()` 。
- 已加入 \<optional\> 、、 \<variant\> `shared_ptr::weak_type` 和 \<cstdalign\> 。
- **`constexpr`** 在、、和中啟用 c + + 14、 `min(initializer_list)` `max(initializer_list)` `minmax(initializer_list)` 和 `min_element()` 、和 `max_element()` `minmax_element()` 。

如需詳細資訊，請參閱[Microsoft c + + 語言一致性表格](../visual-cpp-language-conformance.md)。

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 15.3 版

- 已實作數個額外的 C++17 功能。 如需詳細資訊，請參閱[Microsoft c + + 語言一致性表格](cpp-conformance-improvements.md#improvements_153)。
- 已實作 P0602R0「Variant 和 Optional 應隨意地散佈 Copy/Move」。
- 標準程式庫現已正式容許透過 [/GR-](../build/reference/gr-enable-run-time-type-information.md) 選項停用動態 RTTI。 `dynamic_pointer_cast()`和 `rethrow_if_nested()` 原本都需要 **`dynamic_cast`** ，因此標準程式庫現在會將它們標示為 `=delete` **`/GR-`** 。
- 即使已透過停用動態 RTTI **`/GR-`** ，的形式的「靜態 rtti」 `typeid(SomeType)` 仍然可供使用，並提供數個標準程式庫元件。 標準程式庫現在也支援透過來停用這項功能 **`/D_HAS_STATIC_RTTI=0`** 。 此旗標也會停用 `std::function` 的 `std::any`、`target()` 和 `target_type()` 成員函式，及 `std::shared_ptr` 和 `std::weak_ptr` 的 `get_deleter()` friend 成員函式。
- 標準程式庫現在會無條件地使用 c + + 14 **`constexpr`** ，而不是有條件地定義宏。
- 標準程式庫現在會於內部使用別名範本。
- 標準程式庫現在會 **`nullptr`** 在內部使用，而不是 `nullptr_t{}` 。 (已經完全清除 NULL 的內部使用情況。 正在逐步清除 0-as-null 的內部使用情況)。
- 標準程式庫現在會於內部使用 `std::move()`，而非誤用 `std::forward()`。
- `static_assert(false, "message")` 已變更為 `#error message`。 此變更會改善編譯器診斷，因為 `#error` 會使編譯立刻停止。
- 標準程式庫已不再將函式標示為 `__declspec(dllimport)`。 新式的連結器技術已不再需要這麼做。
- 已將 SFINAE 擷取至預設範本引數，相較於傳回類型和函式引數類型，這將會減少雜亂的情形。
- 中的 Debug 檢查 \<random\> 現在會使用標準程式庫的一般機制，而不是會 `_Rng_abort()` 呼叫 `fputs()` **stderr**的內部函式。 為了二進位相容性，已保留此函式的執行功能。 我們會在下一個二進位不相容的標準程式庫版本中移除它。

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 15.5 版

- 已根據 c + + 17 標準新增、取代或移除數個標準程式庫功能。 如需詳細資訊，請參閱[Visual Studio 中的 c + + 一致性改進](cpp-conformance-improvements.md#improvements_155)。
- 提供對下列平行演算法的實驗性支援：
  - `all_of`
  - `any_of`
  - `for_each`
  - `for_each_n`
  - `none_of`
  - `reduce`
  - `replace`
  - `replace_if`
  - `sort`
- 此時會加入下列平行演算法的簽章，但不會平行處理。 分析在僅移動或置換元素的平行處理演算法中沒有任何好處：
  - `copy`
  - `copy_n`
  - `fill`
  - `fill_n`
  - `move`
  - `reverse`
  - `reverse_copy`
  - `rotate`
  - `rotate_copy`
  - `swap_ranges`

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 15.6 版

- \<memory_resource>
- 程式庫基本概念 V1
- 刪除 `polymorphic_allocator` 指派
- 改善類別範本引數推斷

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 15.7 版

- 對平行演算法的支援不再為實驗性
- 的新執行\<filesystem>
- 基礎字串轉換 (部分)
- `std::launder()`
- `std::byte`
- `hypot(x,y,z)`
- 避免不必要的 Decay
- 數學特殊函式
- `constexpr char_traits`
- 標準程式庫的推算指南

如需詳細資訊，請參閱[Microsoft c + + 語言一致性表格](../visual-cpp-language-conformance.md)。

### <a name="performance-and-throughput-fixes"></a>效能和輸送量修正

- 使 `basic_string::find(char)` 多載只呼叫 `traits::find` 一次。 先前已為長度為 1 的字串將其作為一般字串搜尋實作。
- `basic_string::operator==` 現在會先檢查字串的大小再比較字串的內容。
- 移除了 `basic_string` 中的控制項結合程度，因為編譯器最佳化工具很難加以分析。 對所有短字串呼叫 `reserve` 都不會執行任何動作，但仍有成本。
- `std::vector`已針對正確性和效能翻修了：在插入和 emplace 作業期間的別名現在會依照標準的要求正確處理，現在當標準透過和其他邏輯需要時，會提供強式例外狀況保證 `move_if_noexcept()` ，而 insert 和 emplace 則會執行較少的元素作業。
- C++ 標準程式庫現在會避免為 null 假想指標取值。
- 改善了 `weak_ptr::lock()` 效能。
- 為了增加編譯器輸送量，C++ 標準程式庫標頭現在會避免包含非必要編譯器內建的宣告。
- 改善了 `std::string` 和 `std::wstring` 移動建構函式的效能，改善幅度超過三倍。

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 15.3 版

- 解決與的互動 **`noexcept`** ，這可防止將 `std::atomic` 執行內嵌至使用結構化例外狀況處理（SEH）的函式。
- 標準程式庫的內部 `_Deallocate()` 函式已變更為較小的程式碼，使其適合內嵌至更多位置。
- `std::try_lock()` 已從使用遞迴改為使用套件展開。
- 改善了 `std::lock()` 鎖死迴避演算法，從原本對所有鎖定重複執行 `try_lock()` ，改為使用 `lock()` 作業。
- 讓 `system_category::message()` 中可進行具名傳回值最佳化。
- `conjunction`和 `disjunction` 現在會具現化 `N + 1` 類型，而不是 `2N + 2` 類型。
- `std::function` 不會再對每個已清除類型的可呼叫項目將配置器支援機制具現化，如此可在會傳遞許多相異 Lambda 到 `std::function` 的程式中，改善輸送量並減少 .obj 大小。
- `allocator_traits<std::allocator>` 包含手動內嵌的 `std::allocator` 作業，以減少只透過 `allocator_traits` 與 `std::allocator` 互動之程式碼 (也就是大部分程式碼) 中的程式碼大小。
- C++11 最小配置器介面現已由標準程式庫直接呼叫 `allocator_traits` 來處理，而非將配置器包裝在內部類別 `_Wrap_alloc` 中。 此變更會減少為支援配置器所產生的程式碼大小、改善最佳化工具在某些情況下對標準程式庫容器進行判斷的能力，並提供更佳的偵錯體驗 (如同您現在會在偵錯工具中看見您的配置器類型，而非 `_Wrap_alloc<your_allocator_type>`)。
- 已移除自訂的元化 `allocator::reference` ，而不允許自訂配置器。 (配置器可以使容器使用自訂的指標，但不能使用自訂的參考)。
- 編譯器前端被教導在範圍架構的 for 迴圈中解除偵錯迭代器的包裝，以改善偵錯組建的效能。
- `shrink_to_fit()` 和 `reserve()` 的 `basic_string` 內部縮小路徑已不再位於重新配置作業的路徑中，以減少所有變動成員的程式碼大小。
- `basic_string` 的內部成長路徑已不再位於 `shrink_to_fit()` 的路徑中。
- 現已將 `basic_string` 變動作業納入非配置的快速路徑和配置的慢速路徑函式中，讓一般的無重新配置案例更容易內嵌至呼叫者。
- 變動 `basic_string` 作業現在會以慣用狀態來建立重新配置的緩衝區，而非就地調整大小。 例如，在字串開頭的插入，現在只會在插入一次後移動內容。 它會向下移動或移至新配置的緩衝區。 在重新配置的情況下，不會再將它移到新配置的緩衝區，然後再移動。
- 在中呼叫 C 標準程式庫的作業現在會快 \<string\> `errno` 取位址，以移除與 TLS 的重複互動。
- 簡化了 `is_pointer` 實作。
- 已完成將以函式為基礎的運算式 SFINAE 變更為 **`struct`** ，並以為 `void_t` 基礎。
- 標準程式庫演算法現在會避免會後續累加的迭代器。
- 已修正在 64 位元系統上使用 32 位元配置器時會出現的截斷警告。
- 透過在情況允許時重複使用緩衝區，`std::vector` 移動指派現在在非 POCMA non-equal-allocator 案例中變得更有效率。

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 15.5 版

- `basic_string<char16_t>` 現在會與 `basic_string<wchar_t>` 納入相同的 `memcmp`、`memcpy` 及相似的最佳化。
- 我們在 Visual Studio 2015 Update 3 中進行的「避免複製函式」顯示了最佳化工具有一項限制會導致函式指標無法內嵌，而這項問題已獲得解決，從而恢復 `lower_bound(iter, iter, function pointer)` 的效能。
- 現在會先將迭代器解除包裝再檢查順序，讓迭代器偵錯對 `includes`、`set_difference`、`set_symmetric_difference` 和 `set_union` 輸入執行的順序驗證得以減輕額外負荷。
- `std::inplace_merge` 現在會跳過已就位的項目。
- 建構 `std::random_device` 不會再建構並終結 `std::string`。
- `std::equal` 和 `std::partition` 具有跳躍執行緒最佳化傳遞，可免去迭代器比較。
- 當 `std::reverse` 是已傳遞至可完整複製之 `T` 的指標時，現在會分派至手寫的向量化實作。
- 已指示 `std::fill`、`std::equal` 和 `std::lexicographical_compare` 如何分派至 `std::byte` 和 `gsl::byte` (及其他 char 一類的列舉和列舉類別) 的 `memset` 和 `memcmp`。 `std::copy` 使用 `is_trivially_copyable` 分派，因此不需任何變更。
- 標準程式庫不再包含空的大括弧解構函式，其唯一的行為是使類型成為 non-trivially-destructible。

## <a name="other-libraries"></a>其他程式庫

### <a name="open-source-library-support"></a>開放原始碼程式庫支援

**Vcpkg** 是一種開放原始碼命令列工具，可大幅簡化在 Visual Studio 中取得和建置開放原始碼 C++ 靜態程式庫和 DLLS 的程序。 如需詳細資訊，請參閱 [vcpkg：C++ 的套件管理員](../build/vcpkg.md)。

### <a name="cpprest-sdk-290"></a>CPPRest SDK 2.9.0

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 15.5 版

CPPRestSDK 是適用於 C++ 的跨平台 Web API，已更新成 2.9.0 版。 如需詳細資訊，請參閱 [CppRestSDK 2.9.0 is available on GitHub](https://devblogs.microsoft.com/cppblog/cpprestsdk-2-9-0-is-available-on-github/)(GitHub 上可用的 CppRestSDK 2.9.0)。

### <a name="atl"></a>ATL

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 15.5 版

- 另一組 name-lookup 一致性修正
- 現有的移動建構函式和移動指派運算子現在已正確標示為非擲回
- 取消隱藏和 atlstr.h 中區域靜態安全執行緒初始化有關的有效警告 C4640
- 當使用 ATL 來建立 DLL 時，會在 XP 工具組中自動關閉本機靜態的安全線程初始化。 現在不是。 **`/Zc:threadSafeInit-`** 如果您不想要進行安全線程初始化，您可以在專案設定中加入。

### <a name="visual-c-runtime"></a>Visual C++ 執行階段

- 「控制流程防護」符號的新標頭 ‘cfguard.h’。

## <a name="visual-studio-2017-c-ide"></a>Visual Studio 2017 c + + IDE

- C++ 原生專案的組態變更效能現已提升，而 C++/CLI 專案的組態變更效能則更佳。 現在解決方案組態在首次啟用時將會較快，而它在之後啟用時將能幾乎瞬間完成。

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 15.3 版

- 已重寫數個專案和程式碼精靈的簽章對話方塊樣式。
- [**加入類別**] 現在會直接啟動 [加入類別] wizard。 之前在這裡的所有其他項目，現在會在 [新增] > [新增項目]**** 下提供。
- Win32 專案現在會在 [**新增專案**] 對話方塊的 [ **Windows 桌面**] 類別之下。
- **Windows 主控台**和**桌面應用程式**範本現在會建立專案，而不會顯示嚮導。 相同類別下有新的 [Windows Desktop 精靈]****，其顯示的選項與舊版 [Win32 主控台應用程式精靈]**** 相同。

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 15.5 版

使用 IntelliSense 引擎進行重構和程式碼瀏覽的數項 C++ 作業執行速度更快。 下列數值是根據含有 3500 個專案的 Visual Studio Chromium 方案而來：

| 功能 | 效能改善 |
|--|--|
| 重新命名 | 5.3 倍 |
| 變更簽章 | 4.5 倍 |
| 尋找所有參考 | 4.7 倍 |

C++ 現在支援以 Ctrl+按一下 [移至定義]****，如此可輕鬆使用滑鼠瀏覽至定義。 Productivity Power Tools 套件的 Structure Visualizer 現在預設也會隨附於產品。

## <a name="intellisense"></a>IntelliSense

- 現在預設使用新的 SQLite 型資料庫引擎。 新引擎可加速 [**移至定義**] 和 [**尋找所有參考**] 等資料庫作業。 它可大幅改善初始解決方案剖析時間。 設定已移至 [**工具] > 選項 > 文字編輯器 > C/c + + > Advanced**]。 （以前是在 .。。C/c + + > 實驗性）。

- 我們已對未使用先行編譯標頭檔的專案及檔案提升 IntelliSense 效能，將會為目前檔案中的標頭建立自動先行編譯標頭檔。

- 我們也為錯誤清單中的 IntelliSense 錯誤新增了錯誤篩選及說明。 現在按一下錯誤資料行即可進行篩選。 此外，按一下特定錯誤或按下 F1 鍵，將會啟動線上搜尋錯誤訊息。

  ![錯誤清單](media/ErrorList1.png "錯誤清單")

  ![篩選出的錯誤清單](media/ErrorList2.png "篩選出的錯誤清單")

- 新增了依種類篩選成員清單項目的功能。

  ![成員清單篩選](media/mlfiltering.png "成員清單篩選")

- 新增了實驗性的預測性 IntelliSense 功能，提供成員清單中出現項目的內容相關篩選。 如需詳細資訊，請參閱 [C++ IntelliSense 改善 - 預測性 IntelliSense 和篩選](https://devblogs.microsoft.com/cppblog/c-intellisense-improvements-predictive-intellisense-filtering/) \(英文\)。
- [**尋找所有參考**] （Shift + F12）現在可協助您更輕鬆地進行，即使在複雜的 codebase 中也一樣。 它提供進階分組、篩選、排序、在結果內搜尋和顏色標示 (適用於某些語言)，因此您可以清楚了解您的參考。 針對 C++，新的 UI 包含要從變數讀取或寫入變數的相關資訊。
- [點改為箭號] IntelliSense 功能已從實驗性改為進階，現在預設為啟用。 編輯器功能 [**展開範圍**] 和 [**展開優先順序**] 也已從實驗性移至 [advanced]。
- 根據預設，實驗性重構功能**變更**簽章和**解壓縮**函式已可供使用。
- 已新增 C++ 專案實驗性的 [加快專案載入] 功能。 C++ 專案會在您下次開啟時更快載入，之後將以*更快*速度載入！
- 其中有部分功能通用於其他語言，部分功能則是 C++ 的特定功能。 如需有關這些新功能的詳細資訊，請參閱[宣布 Visual Studio "15" Preview 5](https://devblogs.microsoft.com/visualstudio/announcing-visual-studio-15-preview-5/)。

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 15.7 版

- 為 ClangFormat 新增了支援。 如需詳細資訊，請參閱 [ClangFormat Support in Visual Studio 2017](https://devblogs.microsoft.com/cppblog/clangformat-support-in-visual-studio-2017-15-7-preview-1/) (Visual Studio 2017 中的 ClangFormat 支援)。

## <a name="non-msbuild-projects-with-open-folder"></a>使用開啟資料夾的非 MSBuild 專案

Visual Studio 2017 引進了「**開啟資料夾**」功能。 它可讓您在包含原始程式碼的資料夾中撰寫程式碼、建立和偵錯工具，而不需要建立任何方案或專案。 現在，即使您的專案不是 MSBuild 專案，這可讓開始使用 Visual Studio 更為簡單。 [**開啟資料夾**] 可讓您存取強大的程式碼理解、編輯、建立和偵錯工具功能。 它們與 Visual Studio 已經為 MSBuild 專案提供的是相同的。 如需詳細資訊，請參閱 [Open Folder projects for C++](../build/open-folder-projects-cpp.md) (適用於 C++ 的開啟資料夾專案)。

- [開啟資料夾] 體驗的改良。 您可以透過這些 .json 檔案自訂體驗：
  - CppProperties.json，用以自訂 IntelliSense 及瀏覽體驗。
  - Tasks.json，用以自訂建置步驟。
  - Launch.json，用以自訂偵錯經驗。

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 15.3 版

- 已改善針對替代編譯器和建置環境 (例如 MinGW 和 Cygwin) 的支援。 如需詳細資訊，請參閱[搭配 Visual C++ 和「開啟資料夾」使用 MinGW 和 Cygwin](https://devblogs.microsoft.com/cppblog/using-mingw-and-cygwin-with-visual-cpp-and-open-folder/) \(英文\)。
- 新增了在 CppProperties.json 和 CMakeSettings.json 中定義全域和組態專用環境變數的支援。 這些環境變數可供 launch.vs.json 中定義的偵錯組態和 tasks.vs.json 中的工作取用。 如需詳細資訊，請參閱 [Customizing your Environment with Visual C++ and Open Folder](https://devblogs.microsoft.com/cppblog/customizing-your-environment-with-visual-c-and-open-folder/) (使用 Visual C++ 和開啟資料夾來自訂您的環境)。
- 已改善針對 CMake Ninja 產生器的支援，包括能夠輕鬆以 64 位元平台作為目標的能力。

## <a name="cmake-support-via-open-folder"></a>透過開啟資料夾的 CMake 支援

Visual Studio 2017 支援使用 CMake 專案，而不需要轉換為 MSBuild 專案檔 (.vcxproj)。 如需詳細資訊，請參閱 [Visual Studio 中的 CMake 專案](../build/cmake-projects-in-visual-studio.md)。 使用 [**開啟資料夾**] 開啟 CMake 專案時，會自動設定 c + + 編輯、建立和偵錯工具的環境。

- 無須在根資料夾中建立 CppProperties.json 檔案，C++ IntelliSense 即可運作。 此外，我們新增了下拉式清單，可讓使用者輕易地切換 CMake 和 CppProperties.json 檔案所提供的設定。

- 透過與 CMakeLists.txt 檔案位於相同資料夾的 CMakeSettings.json 檔案，支援進一步設定。

  ![CMake 開啟資料夾](media/cmake-cpp.png "CMake 開啟資料夾")

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 15.3 版

- 為 CMake Ninja 產生器新增了支援。

##### <a name="visual-studio-2017-version-154"></a>Visual Studio 2017 15.4 版

- 為匯入現有 CMake 快取新增了支援。

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 15.5 版

- 新增對 CMake 3.11、CMake 專案中程式碼分析、方案總管中的目標檢視、用於產生快取的選項以及單一檔案編譯的支援。 如需詳細資訊，請參閱 [Visual Studio 中的 CMake 支援](https://devblogs.microsoft.com/cppblog/cmake-support-in-visual-studio-targets-view-single-file-compilation-and-cache-generation-settings/) \(英文\) 與 [Visual Studio 中的 CMake 專案](../build/cmake-projects-in-visual-studio.md)。

## <a name="windows-desktop-development"></a>Windows 桌面開發

我們現在提供安裝原始 C++ 工作負載時更細微的安裝體驗。 我們已新增可選取的元件，讓您能夠只安裝所需的工具。 安裝程式 UI 中列出之元件的指定安裝大小不正確，且低估總大小。

若要在 C++ 桌面工作負載中成功建立 Win32 專案，您必須安裝工具組和 Windows SDK。 安裝建議 (選取) 的元件 **VC++ 2017 v141 工具組 (x86、x64)** 和 **Windows 10 SDK (10.0.nnnnn)** 可確保其正常運作。 如果未安裝所需的工具，將無法成功建立專案，而且 wizard 會停止回應。

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 15.5 版

Visual Studio Build Tools (先前以獨立產品形式提供) 現在以工作負載形式包含在 Visual Studio 安裝程式中。 此工作負載只會安裝建置 C++ 專案所需的工具，而不會安裝 Visual Studio IDE。 v140 和 v141 工具組都包含在內。 v141 工具組包含 Visual Studio 2017 15.5 版的最新改善功能。 如需詳細資訊，請參閱 [Visual Studio Build Tools now include the VS2017 and VS2015 MSVC Toolsets](https://devblogs.microsoft.com/cppblog/visual-studio-build-tools-now-include-the-vs2017-and-vs2015-msvc-toolsets/) (Visual Studio 建置工具現在包含 VS2017 和 VS2015 MSVC 工具組)。

## <a name="linux-development-with-c"></a>使用 C++ 的 Linux 程式開發

熱門的 [Visual C++ for Linux Development](https://marketplace.visualstudio.com/items?itemName=VisualCppDevLabs.VisualCforLinuxDevelopment) 擴充功能現已納入 Visual Studio 中。 這個安裝提供您開發在 Linux 環境上執行的 C++ 應用程式，並進行偵錯所需的一切。

##### <a name="visual-studio-2017-version-152"></a>Visual Studio 2017 15.2 版

跨平台程式碼共用和類型視覺效果已經過功能改善。 如需詳細資訊，請參閱[針對跨平台程式碼共用和類型視覺效果的 Linux C++ 改善](https://devblogs.microsoft.com/cppblog/linux-cross-platform-and-type-visualization/) \(英文\)。

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 15.5 版

- Linux 工作負載已新增對**rsync**的支援，做為**sftp**的替代方案，可將檔案同步處理至遠端 Linux 電腦。
- 新增以 ARM 為目標的交互編譯支援。 若要在安裝中啟用這項支援，請選擇 [使用 C++ 進行 Linux 開發]**** 工作負載，並選取 [內嵌和 IoT 開發]**** 的選項。 此選項會將 ARM GCC 交互編譯工具和 Make 新增至您的安裝。 如需詳細資訊，請參閱 [ARM GCC Cross Compilation in Visual Studio](https://devblogs.microsoft.com/cppblog/arm-gcc-cross-compilation-in-visual-studio/) (Visual Studio 中的 ARM GCC 交互編譯)。
- 新增對 CMake 的支援。 您現在可以使用現有的 CMake 程式碼基底，而不必將它轉換成 Visual Studio 專案。 如需詳細資訊，請參閱[設定 Linux CMake 專案](../linux/cmake-linux-project.md)。
- 新增對執行遠端工作的支援。 這項功能可讓您在 Visual Studio 的連線管理員中定義的遠端系統上執行任何命令。 遠端工作也會提供將檔案複製到遠端系統的功能。
如需詳細資訊，請參閱[設定 Linux CMake 專案](../linux/cmake-linux-project.md)。

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 15.7 版

- 對 Linux 工作負載案例的各項改善。 如需詳細資訊，請參閱 [Linux C++ Workload improvements to the Project System, Linux Console Window, rsync and Attach to Process](https://devblogs.microsoft.com/cppblog/linux-c-workload-improvements-to-the-project-system-linux-console-window-rsync-and-attach-to-process/) (專案系統、Linux 主控台視窗、rsync 及附加至處理序的 Linux C++ 工作負載改善)。
- 適用於遠端 Linux 連線標頭的 IntelliSense。 如需詳細資訊，請參閱 [IntelliSense for Remote Linux Headers](https://devblogs.microsoft.com/cppblog/intellisense-for-remote-linux-headers/) (適用於遠端 Linux 標頭的 IntelliSense) 和[設定 Linux CMake 專案](../linux/cmake-linux-project.md)。

## <a name="game-development-with-c"></a>使用 C++ 的遊戲程式開發

使用 C++ 的完整功能建置由 DirectX 或 Cocos2d 技術提供的專業遊戲。

## <a name="mobile-development-with-c-for-android-and-ios"></a>適用于 Android 和 iOS 的行動裝置開發（c + +）

您現在能夠使用可以 Android 及 iOS 為目標的 Visual Studio 建立行動應用程式並對其偵錯。

## <a name="universal-windows-apps"></a>通用 Windows App

C++ 以通用 Windows app 工作負載的選用元件形式提供。 目前，您必須手動升級 c + + 專案。 您可以在 Visual Studio 2017 中開啟以 v140 為目標的通用 Windows 平臺專案。 不過，如果您未安裝 Visual Studio 2015，則需要在專案屬性頁中選取 [v141] 平臺工具組。

## <a name="new-options-for-c-on-universal-windows-platform-uwp"></a>通用 Windows 平台 (UWP) 上 C++ 的新選項

您現在有新的選項，可為通用 Windows 平臺和 Windows Store 撰寫和封裝 c + + 應用程式：桌面橋接器基礎結構可讓您封裝現有的桌面應用程式或 COM 物件，以透過 Windows Store 進行部署。 或者，透過側載的現有通道進行部署。 Windows 10 中的新功能可讓您以各種方式將 UWP 功能新增至傳統型應用程式。 如需詳細資訊，請參閱[傳統型橋接器](/windows/uwp/porting/desktop-to-uwp-root)。

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 15.5 版

新增了 [Windows 應用程式封裝專案]**** 專案範本，可大幅簡化使用傳統型橋接器封裝傳統型應用程式的工作。 該範本位於 [檔案] | [開新檔案] | [專案] | [已安裝] | [Visual C++] | [通用 Windows 平台]**** 底下。 如需詳細資訊，請參閱[使用 Visual Studio 封裝應用程式 (傳統型橋接器)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net)。

撰寫新的程式碼時，您現在可以使用 C++/WinRT，它是一種標準 C++ 語言推演，適用於僅在標頭檔中實作的 Windows 執行階段。 它可讓您使用任何符合標準的 c + + 編譯器來取用和撰寫 Windows 執行階段 Api。 C++/WinRT 設計成將現代 Windows API 的第一級存取提供給 C++ 開發人員。 如需詳細資訊，請參閱[c + +/WinRT：適用于 Windows 執行階段的新式 c + +](https://moderncpp.com/)。

從 Windows SDK Insider Preview 的組建17025開始，c + +/WinRT 會包含在 Windows SDK 中。 如需詳細資訊，請參閱 [C++/WinRT is now included the Windows SDK](https://devblogs.microsoft.com/cppblog/cppwinrt-is-now-included-the-windows-sdk/) (C++/WinRT 現在隨附於 Windows SDK)。

## <a name="the-clangc2-platform-toolset"></a>Clang/C2 平臺工具組

隨附于 Visual Studio 2017 的 Clang/C2 工具組現在支援 **`/bigobj`** 參數，這對於建立大型專案很重要。 此外，它也包含在編譯器前端和後端中的數個重要 bug 修正。

## <a name="c-code-analysis"></a>C++ 程式碼分析

用於強制 [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines) 的 C++ Core Checkers 現已隨 Visual Studio 散發。 在專案屬性頁的 [程式**代碼分析延伸**模組] 頁面中啟用檢查程式。 然後，當您執行程式碼分析時，就會包含這些延伸模組。 如需詳細資訊，請參閱[使用 C++ 核心指南檢查工具](/cpp/code-quality/using-the-cpp-core-guidelines-checkers)。

![CppCoreCheck](media/CppCoreCheck.png "CppCoreCheck 屬性頁面")

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 15.3 版

- 新增了資源管理相關規則的支援。

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 15.5 版

- 新的 C++ Core Guidelines 檢查會涵蓋智慧型指標正確性、全域初始化運算式的正確用法，以及標記使用和不正確轉換等結構的用法 **`goto`** 。

- 某些您可以在 15.3 中找到的警告編號，在 15.5 中已不再使用。 這些警告已取代為更明確的檢查。

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 15.6 版

- 新增對單一檔案分析的支援，以及分析執行階段效能的改善。 如需詳細資訊，請參閱 [C++ Static Analysis Improvements for Visual Studio 2017 15.6 Preview 2](https://devblogs.microsoft.com/cppblog/c-static-analysis-improvements-for-visual-studio-2017-15-6-preview-2/) (Visual Studio 2017 15.6 Preview 2 的 C++ 靜態分析改善)

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 15.7 版

- 為新增的支援 [`/analyze:ruleset`](../build/reference/analyze-code-analysis.md) ，可讓您指定要執行的程式碼分析規則。
- 新增對其他 C++ Core Guidelines 規則的支援。  如需詳細資訊，請參閱[使用 C++ 核心指南檢查工具](/cpp/code-quality/using-the-cpp-core-guidelines-checkers)。

## <a name="unit-testing-in-visual-studio-2017"></a>Visual Studio 2017 中的單元測試

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 15.5 版

Google Test 介面卡和提升。測試介面卡現在可作為**使用 c + + 的桌面開發**工作負載的元件。 它們會與**測試瀏覽器**整合在一起。 已針對 CMake 專案（使用 [開啟資料夾]）新增 CTest 支援，雖然尚未提供與**Test Explorer**的完整整合。 如需詳細資訊，請參閱[撰寫 C/c + + 的單元測試](/visualstudio/test/writing-unit-tests-for-c-cpp)。

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 15.6 版

- 新增支援 `Boost.Test` 動態連結程式庫支援。
- `Boost.Test`專案範本現在可在 IDE 中使用。

如需詳細資訊，請參閱[ `Boost.Test` 單元測試：動態連結程式庫支援和新專案範本](https://devblogs.microsoft.com/cppblog/boost-test-unit-testing-dynamic-library-support-and-new-item-template/)。

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 15.7 版

已新增對 C++ 單元測試專案的 [CodeLens](/visualstudio/ide/find-code-changes-and-other-history-with-codelens) 支援。 如需詳細資訊，請參閱 [Announcing CodeLens for C++ Unit Testing](https://devblogs.microsoft.com/cppblog/announcing-codelens-for-c-unit-testing/) (宣佈適用於 C++ 單元測試的 CodeLens)。

## <a name="visual-studio-graphics-diagnostics"></a>Visual Studio 圖形診斷

Visual Studio 圖形診斷工具：您可以使用它們來記錄和分析 Direct3D 應用程式中的轉譯和效能問題。 在 Windows 電腦、Windows 裝置模擬器或遠端電腦或裝置上本機執行的應用程式上使用它們。

- **頂點和幾何著色器的輸入 & 輸出：** 查看頂點著色器和幾何著色器之輸入和輸出的功能，已經是其中一個最常要求的功能。 這項工具現在已受到支援。 在 [管線階段] 視圖中選取 [VS] 或 [GS] 階段，以開始檢查其在下表中的輸入和輸出。

  ![著色器的輸入/輸出](media/io-shaders.png)

- **在物件表格中搜尋和篩選︰** 提供快速且輕鬆的方式來尋找所尋找的資源。

  ![搜尋](media/search.png)

- **資源歷程記錄：** 這個新檢視提供簡化的方式，來查看在轉譯所擷取畫面格期間使用之資源的整個修改歷程記錄。 若要叫用任何資源的歷程記錄，請按一下任何資源超連結旁的時鐘圖示。

  ![資源歷程記錄](media/resource-history.png)

  它會顯示新的 [**資源歷程記錄**] 工具視窗，其中填入了資源的變更歷程記錄。

  ![資源歷程記錄變更](media/resource-history-change.png)

  您可以捕獲已啟用完整呼叫堆疊捕捉的畫面格。 這可讓您快速推算出每個變更事件的內容，並在您的 Visual Studio 專案中進行檢查。 在 [**圖形診斷**] 下的 [Visual Studio**工具 > 選項**] 對話方塊中，設定 [完整堆疊捕捉] 選項。

- **API 統計資料︰** 檢視畫面格中 API 使用方式的高階摘要。 這很適合用來探索您可能不知道的呼叫，或是太常進行的呼叫。 您可以透過 View > Visual Studio 圖形分析器中的**API 統計資料**取得此視窗。

  ![API 統計資料](media/api-stats.png)

- **記憶體統計資料：** 針對您在畫面格中建立的資源，查看驅動程式所配置的記憶體數量。 您可以透過 View > **Visual Studio 圖形分析器**中的**記憶體統計資料**取得此視窗。 若要將資料複製到 CSV 檔案，以在試算表中進行查看，請以滑鼠右鍵按一下並選擇 [**全部複製**]。

  ![記憶體統計資料](media/memory-stats.png)

- **畫面格驗證：** 新的錯誤和警告清單提供簡單的方法，以根據 Direct3D 偵錯層所偵測到的潛在問題來巡覽事件清單。 按一下 [Visual Studio 圖形分析器中的 [ **View > 框架驗證**] 以開啟視窗。 然後按一下 [**執行驗證**] 開始分析。 根據畫面格的複雜性而定，這可能需要幾分鐘的時間才能完成。

  ![畫面格驗證](media/frame-validation.png)

- **D3D12 的畫面格分析：** 使用畫面格分析，利用「假設」的指示來分析繪製呼叫效能。 切換至 [畫面格分析] 索引標籤，然後執行分析以檢視報表。 如需詳細資訊，請觀看 [GoingNative 25: Visual Studio Graphics Frame Analysis](https://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool) (GoingNative 25：Visual Studio 圖形畫面格分析) 視訊。

  ![畫面格分析](media/frame-analysis.png)

- **GPU 使用量改善：** 您可以透過使用 GPU View 或 Windows Performance Analyzer （WPA）工具的 Visual Studio GPU 使用量分析工具來取得開啟追蹤，以取得更詳細的分析。 如果您已安裝 Windows 效能工具組，則會有兩個超連結：一個用於 WPA，另一個用於 GPU 視圖（位於會話總覽的右下方）。

  ![GPU 使用量](media/gpu-usage.png)

  您透過此連結在 GPU 視圖中開啟的追蹤，支援同步處理與 GPU 視圖時間軸縮放和移動。 VS 控制項中的核取方塊，表示是否啟用同步處理。

  ![GPU 檢視](media/gpu-view.png)

::: moniker-end

::: moniker range="=vs-2015"

如需到 Visual Studio 2015 Update 3 為止的完整新功能清單，請參閱 [Visual C++ 2003 至 2015 的新功能](/cpp/porting/visual-cpp-what-s-new-2003-through-2015)。

如需所有 Visual Studio 2015 中新功能的詳細資訊，請參閱版本資訊。 它們是從[Visual Studio 2015 版本資訊歷程記錄](/visualstudio/releasenotes/vs2015-version-history)連結而來。

如需有關 Visual Studio 2019 中 C++ 新功能的資訊，請參閱 [Visual Studio 中 C++ 的新功能](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2019)。

如需有關 Visual Studio 2017 中 C++ 新功能的資訊，請參閱 [Visual Studio 2017 中 C++ 的新功能](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2017)。

::: moniker-end
