---
title: Visual Studio 2019 中 C++ 的新功能
ms.date: 04/02/2019
ms.technology: cpp-ide
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 493b96a8ce3359cc18287adbae8cbd6c374671ec
ms.sourcegitcommit: b72a10a7b12e722fd91a17406b91b270026f763a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2019
ms.locfileid: "58899404"
---
<!--NOTE all https:// links to docs.microsoft.com need to be converted to site-relative links prior to publishing-->

# <a name="whats-new-for-c-in-visual-studio-2019"></a>Visual Studio 2019 中 C++ 的新功能

Visual Studio 2019 有多個 Microsoft C++ 環境的更新與修正。 我們已修正編譯器和工具中的許多 Bug 及回報問題，其中多是客戶透過 [傳送意見反應] 底下的[回報問題](/visualstudio/how-to-report-a-problem-with-visual-studio-2017)和[提供建議](https://developercommunity.visualstudio.com/spaces/62/index.html)選項提交而來。 感謝您回報 Bug！ 如需所有 Visual Studio 新功能的詳細資訊，請瀏覽 [Visual Studio 的新功能](/visualstudio/ide/whats-new-visual-studio-2019)。

## <a name="c-compiler"></a>C++ 編譯器

- `/std:c++latest` 選項現在會包含不一定完整的 C++20 功能，包括對使用 C++20 運算子 <=> (「太空船」) 的初步支援，以進行三向比較。

- [P0941R2 - 功能測試巨集](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0941r2.html)已完成，並支援 `__has_cpp_attribute`。 所有的標準模式都支援功能測試巨集。

- [C++20 P1008R1 - 禁止含使用者宣告建構函式的彙總](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p1008r1.pdf)也已完成。

- 增強支援 C++17 功能及實驗性支援 C++20 功能 (例如模組和協同程式)。 如需詳細資訊，請參閱 [Visual Studio 2019 中的 C++ 一致性改善](../cpp-conformance-improvements.md)。

- C++ 編譯器參數 `/Gm` 現已被取代。 若已明確定義 `/Gm` 參數，請考慮將它從您的組建指令碼中停用。 或者，您也可以安全地忽略 `/Gm` 的過時警告，因為當使用 [將警告視為錯誤] (`/WX`) 時不會將它視為錯誤。

- 根據預設，C++ 主控台和傳統型應用程式不再產生先行編譯標頭檔。

### <a name="codegen-security-diagnostics-and-versioning"></a>Codegen、安全性、診斷和版本控制

改善對 `/Qspectre` 的分析，以提供對 Spectre 變體 1 (CVE-2017-5753) 的風險降低協助。 如需詳細資訊，請參閱 [Spectre mitigations in MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/) (MSVC 中的 Spectre 風險降低)。

## <a name="c-standard-library-improvements"></a>C++ 標準程式庫改善

- [C++20 P0550R2 \(remove_cvref)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0550r2.pdf) 已完成。

- C++17\<charconv> 浮點數 to_chars() 已改善：最短 chars_format::fixed 已加快 60-80%，而最短/精確度 chars_format::hex 已完成。

- 更多演算法已平行處理實作：is_sorted()、is_sorted_until()、is_partitioned()、set_difference()、set_intersection()、is_heap()、is_heap_until()。

- 改善 `std::variant`，讓它更適用於更最佳化工具，以產生更好的程式碼。 現在，內嵌程式碼搭配 `std::visit` 的效果更好。

- 我們已將 clang 格式套用至 C++ 標準程式庫標頭，以改善可讀性。

- 改善使用 `if constexpr` 編譯數個標準程式庫功能時的輸送量。

- 已將標準程式庫的實體設計最佳化，以避免編譯非 #include 標準程式庫的組件，同時針對只含 \<vector> 的空檔案可省下一半的建置時間。

## <a name="performancethroughput-fixes"></a>效能/輸送量修正

- 改善建置輸送量，包括連結器對檔案 I/O 的處理方式，以及合併與建立 PDB 類型的連結時間。

- 新增了 OpenMP SIMD 向量化的基本支援。 您可以使用新的 CL 參數 `-openmp:experimental` 加以啟用。 此選項讓標註了 `#pragma omp simd` 的迴圈有機會向量化。 向量化並不保證會發生，而已標註但未向量化的迴圈會收到回報的警告。 不支援任何 SIMD 子句；系統會回報警告並加以忽略。

- 新增了內嵌命令列參數 `-Ob3`，這是比 `-Ob2` 更為積極的版本。 `-O2` (將二進位檔最佳化以提高速度) 仍預設表示 `-Ob2`。 若您發現編譯器的內嵌不夠積極，請考慮傳遞 `-O2 -Ob3`。

- 為了支援包含數學程式庫函式及其他運算 (例如整數除法) 呼叫的迴圈手動向量化，我們新增了對 Short Vector Math Library (SVML) 內建函式的支援。 這些函式可計算 128 位元、256 位元或 512 位元的向量對等項目。 若要了解支援函式的定義，請參閱 [Intel Intrinsic Guide](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#!=undefined&techs=SVML)。

- 新增及改進的最佳化：

  - 為使用 SIMD 向量內建函式的運算式提供常數摺疊和算數簡化，浮點數和整數形式均適用。

  - 有更強大的分析可從控制流程 (if/else/switch 陳述式) 擷取資訊，以移除總是證實為 true 或 false 的分支。

  - 改進了 memset 展開，以使用 SSE2 向量指令。

  - 改進了無用結構/類別複本的移除作業，尤其是依值傳遞的 C++ 程式。

  - 改進了使用 `memmove` 的程式碼最佳化，例如 `std::copy` 或 `std::vector` 及 `std::string` 建構。

## <a name="c-ide"></a>C++ IDE

### <a name="live-share-c-support"></a>支援 Live Share C++

[Live Share](/visualstudio/liveshare/) 現已支援 C++，可讓開發人員使用 Visual Studio 或 Visual Studio Code 即時共同作業。 如需詳細資訊，請參閱 [Announcing Live Share for C++:Real-Time Sharing and Collaboration](https://devblogs.microsoft.com/cppblog/cppliveshare/) (宣佈推出適用於 C++ 的 Live Share：即時共用與共同作業)

### <a name="intellicode-for-c"></a>適用於 C++ 的 IntelliCode

IntelliCode 是一款選擇性延伸模組，其可使用本身密集的訓練與您的程式碼上下文，將您最可能使用的項目放在完成清單頂端。 它通常不需要向下捲動清單。 針對 C++，當您使用標準程式庫之類的熱門程式庫時，IntelliCode 的幫助最大。 如需詳細資訊，請參閱 [AI-Assisted Code Completion Suggestions Come to C++ via IntelliCode](https://devblogs.microsoft.com/cppblog/cppintellicode/) (透過 IntelliCode 可實現 C++ 的 AI 輔助程式碼完成建議)。

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

## <a name="cmake-support"></a>CMake 支援

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

## <a name="debugging"></a>偵錯

- 針對在 Windows 上執行的 C++ 應用程式，PDB 檔案現在會在個別的 64 位元處理序上載入。 此變更已解決由於偵錯工具在針對包含大量模組與 PDB 檔案的應用程式進行偵錯時耗盡記憶體而導致的各種當機問題。

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

## <a name="unit-testing"></a>單元測試

不再提供 Managed C++ 測試專案範本。 您可以繼續在現有的專案中使用受控 C++ 測試架構。 對於新的單元測試，請考慮使用 Visual Studio 有提供範本 (MSTest、Google Test) 或受控 C# 測試專案範本的其中一個原生測試架構。
