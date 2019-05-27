---
title: Visual Studio 2019 中 C++ 的新功能
ms.date: 05/13/2019
ms.technology: cpp-ide
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 19eaa9d4ed1cf12e721825f998fa674363eda488
ms.sourcegitcommit: 61121faf879cc581a4d39e4baccabf7cf1f673a5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2019
ms.locfileid: "65934135"
---
# <a name="whats-new-for-c-in-visual-studio-2019"></a>Visual Studio 2019 中 C++ 的新功能

Visual Studio 2019 有多個 Microsoft C++ 環境的更新與修正。 我們已修正編譯器和工具中的許多錯誤 (Bug) 與問題，其中多是客戶透過 [傳送意見反應] 底下的[回報問題](/visualstudio/how-to-report-a-problem-with-visual-studio-2017)和[提供建議](https://developercommunity.visualstudio.com/spaces/62/index.html)選項提交而來。 感謝您回報 Bug！ 如需所有 Visual Studio 新功能的詳細資訊，請瀏覽 [Visual Studio 的新功能](/visualstudio/ide/whats-new-visual-studio-2019)。

## <a name="c-compiler"></a>C++ 編譯器

- 增強支援 C++17 功能與正確性修正，加上 C++20 功能 (例如模組和協同程式) 的實驗性支援。 如需詳細資訊，請參閱 [Visual Studio 2019 中的 C++ 一致性改善](../cpp-conformance-improvements.md)。

- `/std:c++latest` 選項現在會包含不一定完整的 C++20 功能，包括對使用 C++20 運算子 \<=> (「太空船」) 的初步支援，以進行三向比較。

- C++ 編譯器參數 `/Gm` 現已被取代。 若已明確定義 `/Gm` 參數，請考慮將它從您的組建指令碼中停用。 或者，您也可以安全地忽略 `/Gm` 的過時警告，因為當使用 [將警告視為錯誤] (`/WX`) 時不會將它視為錯誤。

- 隨著 MSVC 開始實作來自 C++20 標準版草稿的功能 (在 `/std:c++latest` 旗標下)，`/std:c++latest` 現在與 `/clr` (所有版本)、`/ZW` 與 `/Gm` 不相容。 在 Visual Studio 2019 中，當使用 `/clr`、`/ZW` 或 `/Gm` 編譯時，請使用 `/std:c++17` 或 `/std:c++14` 模式 (但請參閱先前的項目符號內容)。

- 根據預設，C++ 主控台和傳統型應用程式不再產生先行編譯標頭檔。

### <a name="codegen-security-diagnostics-and-versioning"></a>Codegen、安全性、診斷和版本控制

改善對 `/Qspectre` 的分析，以提供對 Spectre 變體 1 (CVE-2017-5753) 的風險降低協助。 如需詳細資訊，請參閱 [Spectre mitigations in MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/) (MSVC 中的 Spectre 風險降低)。

## <a name="c-standard-library-improvements"></a>C++ 標準程式庫改善

- 額外 C++17 與 C++20 程式庫功能與正確性修咒的實作。 如需詳細資訊，請參閱 [Visual Studio 2019 中的 C++ 一致性改善](../cpp-conformance-improvements.md)。

- 我們已將 Clang 格式套用至 C++ 標準程式庫標頭，以改善可讀性。

- 因為 Visual Studio 現在針對 C++ 支援 Just My Code，標準程式庫再也不需要為 `std::function` 與 `std::visit` 提供自訂機器以達成相同的效果。 大幅移除該機器對使用者沒有可見的影響，但編譯器將不再產生指出 \<type_traits> 或 \<variant> 第 15732480 或 16707566 行發生問題的診斷。

## <a name="performancethroughput-improvements-in-the-compiler-and-standard-library"></a>編譯器與標準程式庫中的效能/輸送量改進

- 改善建置輸送量，包括連結器對檔案 I/O 的處理方式，以及合併與建立 PDB 類型的連結時間。

- 新增了 OpenMP SIMD 向量化的基本支援。 您可以使用新的編譯器參數 `-openmp:experimental` 來啟用它。 此選項讓標註了 `#pragma omp simd` 的迴圈有機會向量化。 向量化並不保證會發生，而已標註但未向量化的迴圈會收到回報的警告。 不支援任何 SIMD 子句；系統會回報警告並加以忽略。

- 新增了內嵌命令列參數 `-Ob3`，這是比 `-Ob2` 更為積極的版本。 `-O2` (將二進位檔最佳化以提高速度) 仍預設表示 `-Ob2`。 若您發現編譯器的內嵌不夠積極，請考慮傳遞 `-O2 -Ob3`。

- 為了支援包含數學程式庫函式及其他運算 (例如整數除法) 呼叫的迴圈手動向量化，我們新增了對 Short Vector Math Library (SVML) 內建函式的支援。 這些函式可計算 128 位元、256 位元或 512 位元的向量對等項目。 若要了解支援函式的定義，請參閱 [Intel Intrinsic Guide](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#!=undefined&techs=SVML)。

- 新增及改進的最佳化：

  - 為使用 SIMD 向量內建函式的運算式提供常數摺疊和算數簡化，浮點數和整數形式均適用。

  - 有更強大的分析可從控制流程 (if/else/switch 陳述式) 擷取資訊，以移除總是證實為 true 或 false 的分支。

  - 改進了 memset 展開，以使用 SSE2 向量指令。

  - 改進了無用結構/類別複本的移除作業，尤其是依值傳遞的 C++ 程式。

  - 改進了使用 `memmove` 的程式碼最佳化，例如 `std::copy` 或 `std::vector` 及 `std::string` 建構。

- 已將標準程式庫的實體設計最佳化，以避免編譯非 #include 標準程式庫的組件，同時針對只含 \<vector> 的空檔案可省下一半的建置時間。 由於此變更，您可能必須為先前間接包含的標頭新增 #include 指示詞。 例如，使用 `std::out_of_range` 的程式碼可能必須包括 #include \<stdexcept>。 使用串流插入作業的程式碼現在可能必須　#include \<ostream>。 優點是只有實際使用 \<stdexcept> 或 \<ostream> 元件的轉譯單位才必須支付編譯的輸送量成本。

- `if constexpr` 已套用到標準程式庫中的更多位置，以在進行複製作業時獲得改進的輸送量與降低的程式碼大小 - 在反向與旋轉的排列組合，以及在平行演算法程式庫中。 

- 標準程式庫現在會在內部使用 `if constexpr` 來減少編譯時間 (即使是在 C++14 模式中)。

- 平行演算法程式庫的執行階段動態連結偵測已不再使用整個頁面來存放函式指標陣列。 將此記憶體標示為唯讀已被視為與安全性目的不相關。

- `std::thread` 的建構函式已不會再等候該執行緒啟動，而且已不會再於底層 C 程式庫 `_beginthreadex` 與提供的可呼叫物件之間插入這麼多層函式呼叫。 先前 `std::thread` 在 `_beginthreadex` 與提供的可呼叫物件之間放置了 6 個函式，這現在已經減少為 3 個 (其中 2 個只是 `std::invoke`)。 這也可解決 `std::thread` 的建構函式會在系統時鐘於 `std::thread` 建立時變更而當機的問題。

- 已修正 `std::hash` 中的效能迴歸，這是我們在實作 `std::hash<std::filesystem::path>` 時所引進的功能。

- 在數個地方，標準程式庫現在會使用解構函式來達成正確性，而非使用 Catch 區塊。 這讓我們獲得更好的偵錯工具互動；您在受影響位置透過標準程式庫擲回的例外狀況現在將顯示為從其原始擲回網站擲回，而非我們的重新擲回。 並非所有標準程式庫 Catch 區塊都已消除；我們預期 Catch 區塊數目在後續發行 MSVC 時將會減少。

- `std::bitset` 中由 noexcept 函式內的條件式擲回導致的次佳 codegen 已透過鑽研出擲回路徑而修正。

- `std::list` 與 `std::unordered_*` 系列在內部的許多位置使用非偵錯列舉程式。

- 數個 `std::list` 成員已變更為儘可能重複使用清單節點，而非解除配置並重新配置它們。 例如，假設已經有大小為 3 的 `list<int>`，對 `assign(4, 1729)` 的呼叫現在會在前 3 個清單節點中覆寫 ints，並配置一個值為 1729 的新清單節點，而非解除配置全部 3 個清單節點並配置 4 具值為 1729 的新清單節點。

- 對 `erase(begin(), end())` 的所有標準程式庫呼叫都已變更為 `clear()`。

- `std::vector` n現在會在特定案例中以更有效率的方式初始化及擦除元素。

- 改善 `std::variant`，讓它更適用於更最佳化工具，以產生更好的程式碼。 現在，內嵌程式碼搭配 `std::visit` 的效果更好。

## <a name="c-ide"></a>C++ IDE

### <a name="live-share-c-support"></a>支援 Live Share C++

[Live Share](/visualstudio/liveshare/) 現已支援 C++，可讓開發人員使用 Visual Studio 或 Visual Studio Code 即時共同作業。 如需詳細資訊，請參閱 [Announcing Live Share for C++:Real-Time Sharing and Collaboration](https://devblogs.microsoft.com/cppblog/cppliveshare/) (宣佈推出適用於 C++ 的 Live Share：即時共用與共同作業)

### <a name="intellicode-for-c"></a>適用於 C++ 的 IntelliCode

IntelliCode 是一個選擇性延伸模組 (新增為 16.1 中的工作負載元件)，它可以使用本身密集的訓練與您的程式碼上下文，將您最可能使用的項目放在完成清單頂端。 它通常不需要向下捲動清單。 針對 C++，當您使用標準程式庫之類的熱門程式庫時，IntelliCode 的幫助最大。 如需詳細資訊，請參閱 [AI-Assisted Code Completion Suggestions Come to C++ via IntelliCode](https://devblogs.microsoft.com/cppblog/cppintellicode/) (透過 IntelliCode 可實現 C++ 的 AI 輔助程式碼完成建議)。

### <a name="template-intellisense"></a>範本 IntelliSense

**範本列**現在使用**瞄孔 Window** UI 來取代強制回應視窗、支援巢狀範本，並會將任何預設引數預先填入**瞄孔視窗**中。 如需詳細資訊，請參閱 [Template IntelliSense Improvements for Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/template-intellisense-improvements-for-visual-studio-2019-preview-2/) (Visual Studio 2019 Preview 2 的範本 IntelliSense 改善)。 **範本列**中的 [最近使用] 下拉式清單，可讓您在前一組範例引數之間快速切換。

### <a name="new-start-window-experience"></a>新的啟動視窗體驗

啟動 IDE 時，系統會顯示新的啟動視窗與相關選項，可讓您開啟最近使用的專案、從原始檔控制複製程式碼、以方案或資料夾形式開啟本機程式碼，或建立新的專案。 [新增專案] 對話方塊也大幅修改為易於搜尋的可篩選體驗。

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

 Visual Studio 2019 16.1 版

### <a name="quickinfo-improvements"></a>QuickInfo 增強功能

快速諮詢工具提示現在會遵守您編輯器的語意色彩標示。 它也有新的**線上搜尋**連結，此連結可用來搜尋線上文件以深入了解動態顯示程式碼建構。 針對具有紅色波浪線的程式碼，由 Quick Info 提供的連結連結將會在線上搜尋錯誤。 這樣您就不需要在您的瀏覽器中重新輸入訊息。 如需詳細資訊，請參閱 [Visual Studio 2019 中的 Quick Info 改善：色彩標示與線上搜尋](https://devblogs.microsoft.com/cppblog/quick-info-improvements-in-visual-studio-2019-colorization-and-search-online/)。

### <a name="intellicode-available-in-c-workload"></a>IntelliCode 可在 C++ 工作負載中找到

IntelliCode 現在是以「使用 C++ 的桌面開發」 工作負載中的選擇性元件形式提供。 如需詳細資訊，請參閱[改良了C++ IntelliCode 現在隨附於 Visual Studio 2019](https://devblogs.microsoft.com/cppblog/)。

## <a name="cmake-support"></a>CMake 支援

- CMake 3.14 的支援

- Visual Studio 現在可以開啟外部工具所產生的現有 CMake 快取，例如 CMakeGUI、自訂的中繼組建系統，或可自動叫用 cmake.exe 的組建指令碼。

- 改善的 IntelliSense 效能。

- 新的設定編輯器可當成手動編輯 CMakeSettings.json 檔的替代方式，而且與 CMakeGUI 有部分同位。

- Visual Studio 藉由偵測您的 Linux 電腦上是否有相容的 CMake 版本 (若否，則會提供安裝選項)，協助您在 Linux 上使用 CMake 啟動 C++ 開發。

- CMakeSettings 中不相容的設定 (例如不相符的架構或不相容的 CMake 產生器設定) 會在 JSON 編輯器中顯示波浪線，並在錯誤清單中顯示錯誤。

- 只要執行了 `vcpkg integrate install`，就會為 IDE 中開啟的 CMake 專案自動偵測和啟用 vcpkg 工具鏈。 您可透過在 CMakeSettings 中指定空白的工具鏈檔案來關閉這個行為。

- 根據預設，CMake 現在會啟用 Just My Code 偵錯。

- 靜態分析警告現在可在背景處理，以及在 CMake 專案的編輯器中顯示。

- 為 CMake 專案新增了更清楚的建置及設定「開始」和「結束」訊息，及 Visual Studio 建置進度 UI 的支援。 此外，[工具] > [選項] 中現在有 CMake 詳細資訊設定，可用來自訂輸出視窗中的 CMake 組建詳細等級及設定訊息。

- CMakeSettings.json 中現在支援 `cmakeToolchain` 設定，不必手動修改 CMake 命令列就能指定工具鏈。

- 新增 [全部建置] 功能表捷徑 **Ctrl+Shift+B**。

 Visual Studio 2019 16.1 版

- 對使用 Clang/LLVM 編輯、建置及針對 CMake 專案進行偵錯的整合式支援。 如需詳細資訊，請參閱 [Visual Studio 中的 Clang/LLVM 支援](https://devblogs.microsoft.com/cppblog/clang-llvm-support-in-visual-studio/) \(英文\)。

## <a name="linux-and-wsl"></a>Linux 與 WSL

 Visual Studio 2019 16.1 版

- 對 Linux 中之 [AddressSanitizer (ASan)](https://github.com/google/sanitizers/wiki/AddressSanitizer) 與 CMake 跨平台專案的支援。 如需詳細資訊，請參閱 [Visual Studio 2019 中Linux 工作負載的 AddressSanitizer (ASan)](https://devblogs.microsoft.com/cppblog/addresssanitizer-asan-for-the-linux-workload-in-visual-studio-2019/) \(英文\)。

- 使用適用於 Linux 的 Windows 子系統 (WSL) 時對使用 C++ 的整合式 Visual Studio 支援。 如需詳細資訊，請參閱[使用 Visual Studio 2019 與適用於 Linux 的 Windows 子系統 (WSL) 的 C++](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/) \(英文\)。

## <a name="incredibuild-integration"></a>IncrediBuild 整合

IncrediBuild 現在是以「使用 C++ 的桌面開發」 工作負載中的選擇性元件形式提供。 IncrediBuild 建置監視器已完全整合在 Visual Studio IDE 中。 如需詳細資訊，請參閱[使用 IncrediBuild 的建置監視器與 Visual Studio 2019 來視覺化您的建置](https://devblogs.microsoft.com/cppblog/visualize-your-build-with-incredibuilds-build-monitor-and-visual-studio-2019/) \(英文 \)。
 
## <a name="debugging"></a>偵錯

- 針對在 Windows 上執行的 C++ 應用程式，PDB 檔案現在會在個別的 64 位元處理序上載入。 此變更已解決由於偵錯工具在針對包含大量模組與 PDB 檔案的應用程式進行偵錯時耗盡記憶體而導致的各種當機問題。

- 搜尋已在 [監看式]、[自動變數] 與 [區域變數] 視窗中啟用。

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

- Visual Studio 安裝程式不再提供 Windows 8.1 SDK。 建議您將 C++ 專案升級到最新 Windows 10 SDK。 若您有 8.1 的強式相依性，可從 Windows SDK 封存加以下載。

- 最新的 C++ 工具組無法再將 Windows XP 設為目標。 仍支援 VS 2017 級 MSVC 編譯器與程式庫的 XP 目標設定，並可透過「個別元件」安裝。

- 我們的文件積極勸阻您對 Visual C++ 執行階段部署使用合併模組。 我們在這個版本更進一步淘汰了 MSM。 請考慮將您的 VCRuntime 集中部署從 MSM 移轉到可轉散發套件。

## <a name="mobile-development-with-c-android-and-ios"></a>使用 C++ 進行行動裝置應用程式開發 (Android 與 iOS)

C++ Android 體驗現在預設為 Android SDK 25 與 Android NDK 16b。

## <a name="clangc2-platform-toolset"></a>Clang/C2 平台工具組

已移除 Clang/C2 實驗性元件。 針對具有 `/permissive-` 和 `/std:c++17` 的完整 C++ 標準一致性使用 MSVC 工具集，或針對 Windows 使用 Clang/LLVM 工具鏈。

## <a name="code-analysis"></a>程式碼分析

- 程式碼分析現在會在背景自動執行。 警告會在您鍵入的同時，在編輯器內以綠色波浪線顯示。 如需詳細資訊，請參閱 [In-editor code analysis in Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/in-editor-code-analysis-in-visual-studio-2019-preview-2/) (Visual Studio 2019 Preview 2 編輯器中的程式碼分析)。

- 針對來自 \<mutex> 標頭的已知標準程式庫類型，新增實驗性 ConcurrencyCheck 規則。 如需詳細資訊，請參閱 [Concurrency Code Analysis in Visual Studio 2019](https://devblogs.microsoft.com/cppblog/concurrency-code-analysis-in-visual-studio-2019/) (Visual Studio 2019 中的並行程式碼分析)。

- [存留期設定檔檢查程式](https://herbsutter.com/2018/09/20/lifetime-profile-v1-0-posted/)已更新的部分實作，可偵測懸置的指標和參考。 如需詳細資訊，請參閱 [Lifetime Profile Update in Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/lifetime-profile-update-in-visual-studio-2019-preview-2/) (Visual Studio 2019 Preview 2 中的存留期設定檔更新)。

- 更多協同程式相關的檢查，包括 C26138、C26810、C26811 和實驗性規則 C26800。 如需詳細資訊，請參閱 [New Code Analysis Checks in Visual Studio 2019: use-after-move and coroutine](https://devblogs.microsoft.com/cppblog/new-code-analysis-checks-in-visual-studio-2019-use-after-move-and-coroutine/) (Visual Studio 2019 中的新程式碼分析檢查：use-after-move 和協同程式)。

 Visual Studio 2019 16.1 版

針對已解除初始化之變數檢查的新快速修正程式。 如需詳細資訊，請參閱[適用於已解除初始化之記憶體 (C6001) 並使用 before init (C26494) 警告的新程式碼分析快速修正程式](https://devblogs.microsoft.com/cppblog/new-code-analysis-quick-fixes-for-uninitialized-memory-c6001-and-use-before-init-c26494-warnings/) \(英文\)。

## <a name="unit-testing"></a>單元測試

不再提供 Managed C++ 測試專案範本。 您可以繼續在現有的專案中使用受控 C++ 測試架構。 對於新的單元測試，請考慮使用 Visual Studio 有提供範本 (MSTest、Google Test) 或受控 C# 測試專案範本的其中一個原生測試架構。
