---
title: Visual Studio 中 Visual C++ 的新功能
ms.date: 11/15/2017
ms.technology:
- cpp-ide
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 5a9bbf86d6febfdec5ab5cbd9969cd5076672c52
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620138"
---
# <a name="whats-new-for-visual-c-in-visual-studio-2017"></a>Visual Studio 2017 中 Visual C++ 的新功能

Visual Studio 2017 有多項 Visual C++ 環境的更新與修正。 我們已修正超過 250 錯誤，並回報的問題，編譯器和工具，許多提交客戶透過[回報問題](/visualstudio/how-to-report-a-problem-with-visual-studio-2017)和[提供建議](https://visualstudio.uservoice.com/)選項底下**傳送意見反應**. 感謝您回報 Bug！ 如需所有 Visual Studio 新功能的詳細資訊，請瀏覽 [Visual Studio 2017 新功能](/visualstudio/ide/whats-new-in-visual-studio)。

<!--The compiler and tools version number in Visual Studio 2017 is 14.10.24629. -->

## <a name="c-compiler"></a>C++ 編譯器

### <a name="c-conformance-improvements"></a>C++ 一致性改善

我們在本版中更新了 C++ 編譯器和標準程式庫，加強對 C++11 和 C++14 功能的支援，以及對 C++17 標準某些預期功能的基本支援。 如需詳細資訊，請參閱 [Visual Studio 2017 中的 C++ 一致性改善](cpp-conformance-improvements-2017.md)。

**Visual Studio 2017 15.5 版**：編譯器支援 C++17 中約 75% 的功能，包括結構化繫結、`constexpr` Lambda、`if constexpr`、內嵌變數、摺疊運算式，以及將 `noexcept` 新增至型別系統。 您可從 **/std:c++17** 選項使用這些功能。 如需詳細資訊，請參閱 [Visual Studio 2017 中的 C++ 一致性改善](cpp-conformance-improvements-2017.md)

**Visual Studio 2017 15.7 版**：Visual Studio 15.7 版中的 MSVC 編譯器工具組，現在符合 C++ 標準。 如需詳細資訊，請參閱 [Announcing: MSVC Conforms to the C++ Standard](https://blogs.msdn.microsoft.com/vcblog/2018/05/07/announcing-msvc-conforms-to-the-c-standard/) (宣告：MSVC 符合 C++ 標準) 和 [Visual C++ 語言一致性](visual-cpp-language-conformance.md)。

### <a name="new-compiler-options"></a>新的編譯器選項

- [/permissive-](build/reference/permissive-standards-conformance.md)︰啟用所有嚴格的標準一致性編譯器選項，並停用大部分 Microsoft 專用的編譯器延伸模組 (但 `__declspec(dllimport)` 即為不包含在內的例子)。 在 Visual Studio 2017 15.5 版中，此選項預設為開啟。  **/permissive-** 一致性模式包含對兩階段名稱查詢的支援。 如需詳細資訊，請參閱 [Visual Studio 2017 中的 C++ 一致性改善](cpp-conformance-improvements-2017.md)。

- [/diagnostics](build/reference/diagnostics-compiler-diagnostic-options.md)：能夠在發現錯誤或警告的位置，顯示行號、行號和欄位，或行號和欄位及程式碼下的插入點。

- [/debug:fastlink](build/reference/debug-generate-debug-info.md)：最多可讓累加連結時間快 30% (相對於Visual Studio 2015)，方法是不要將所有偵錯資訊複製到 PDB 檔案。 PDB 檔案改為指向用來建立可執行檔之物件和程式庫檔案的偵錯資訊。 請參閱 [Faster C++ build cycle in VS "15" with /Debug:fastlink](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/faster-c-build-cycle-in-vs-15-with-debugfastlink/) (在 VS "15" 中使用 /Debug:fastlink 加快 C++ 組建循環) 和 [Recommendations to speed C++ builds in Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2016/10/26/recommendations-to-speed-c-builds-in-visual-studio/) (在 Visual Studio 中加速 C++ 建置的建議)。

- Visual Studio 2017 允許在使用 [/await](build/reference/await-enable-coroutine-support.md) 時，搭配 [/sdl](build/reference/sdl-enable-additional-security-checks.md)。 我們移除了協同程式的 [/RTC](build/reference/rtc-run-time-error-checks.md) 限制。

   **Visual Studio 2017 15.3 版**：

- [/std:c++14 和 /std:c++latest](build/reference/std-specify-language-standard-version.md)︰這些編譯器選項可讓您在專案中加入特定的 ISO C++ 程式設計語言版本。 大多數新草稿標準功能都在 **/std:c++latest** 選項的防護範圍內。

- [/std:c++17](build/reference/std-specify-language-standard-version.md) 可讓編譯器實作 C++17 功能集。 此選項會對 C++ 標準中，在 C++17 之後推出但屬於進行中草稿及瑕疵更新版本的變更或新增功能，停用編譯器及標準程式庫支援。 若要啟用這些功能，請使用 **/std:c++latest**。

### <a name="codegen-security-diagnostics-and-versioning"></a>Codegen、安全性、診斷和版本控制

此版本為最佳化、程式碼產生、工具組版本控制，以及診斷方面帶來多項改善。 其中幾項值得注意的改善內容包括：

- 改善重複的程式碼產生：支援常數整數除法的自動向量化，更容易識別 memset 模式。
- 改善的程式碼安全性：緩衝區溢位編譯器診斷的發出已獲得改善，而 [/guard:cf](build/reference/guard-enable-control-flow-guard.md) 現在會防護可產生跳躍表的 switch 陳述式。
- 版本設定：現在每次 Visual C++ 工具組更新時，都一律會更新內建前置處理器巨集 **\_MSC\_VER** 的值。 如需詳細資訊，請參閱 [Visual C++ Compiler Version](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/visual-c-compiler-version/) (Visual C++ 編譯器版本)。
- 新的工具組版面配置︰編譯器和相關建置工具在開發電腦上具有新的位置和目錄結構。 新的版面配置可並存安裝多個版本的編譯器。 如需詳細資訊，請參閱 [Compiler Tools Layout in Visual Studio "15"](https://blogs.msdn.microsoft.com/vcblog/2016/10/07/compiler-tools-layout-in-visual-studio-15/) (Visual Studio "15" 中的編譯器工具版面配置)。
- 改善的診斷：輸出視窗現在會顯示發生錯誤的資料行。 如需詳細資訊，請參閱 [C++ compiler diagnostics improvements in VS "15" Preview 5](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/c-compiler-diagnostics-improvements-in-vs-15-rc/) (VS "15" Preview 5 中的 C++ 編譯器診斷改善)。
- 現已移除使用協同程式時的實驗性關鍵字 **yield** (於 **/await** 選項下提供)。 您應該更新程式碼以改用 `co_yield`。 如需詳細資訊，請參閱 [Visual C++ 小組部落格 (英文)](https://blogs.msdn.microsoft.com/vcblog/)。

**Visual Studio 2017 15.3 版**：

對編譯器中診斷的其他改善。 如需詳細資訊，請參閱 [Visual Studio 2017 15.3.0 中的診斷改善](https://blogs.msdn.microsoft.com/vcblog/2017/07/21/diagnostic-improvements-in-vs2017-15-3-0/) \(英文\)。

**Visual Studio 2017 15.5 版**：

Visual C++ 執行階段效能會持續改善，以提高產生的程式碼品質。 這表示您可以輕鬆重新編譯程式碼，而且您的應用程式執行速度會更快。 某些編譯器最佳化功能是全新的，例如條件式純量存放區的向量化、將 `sin(x)` 和 `cos(x)` 呼叫合併成新的 `sincos(x)`，以及從 SSA 最佳化工具排除多餘的指令。 其他編譯器最佳化功能則是現有功能的改善，例如條件運算式的向量化啟發學習法、更佳的迴圈最佳化，以及 float min/max codegen。 連結器有全新且更快的 **/OPT:ICF** 實作，最多可讓連結時間加速 9%，而累加連結中還有其他幾項效能修正。 如需詳細資訊，請參閱 [/OPT (Optimizations)](build/reference/opt-optimizations.md) (/OPT (最佳化)) 和 [/INCREMENTAL (Link Incrementally)](build/reference/incremental-link-incrementally.md) (/INCREMENTAL (以累加方式連結))。

Visual C++ 支援 Intel 的 AVX-512，包括將 AVX-512 的新功能整合到 128 和 256 位元寬暫存器的向量長度指令。

在一般情況下使用 C++17 模式時，可使用 [/Zc:noexceptTypes-](build/reference/zc-noexcepttypes.md) 選項還原為 C++14 版的 `noexcept`。 這可讓您更新原始程式碼以符合 C++17，而不需要同時重寫所有 `throw()` 程式碼。 如需詳細資訊，請參閱[動態例外狀況規格移除和 noexcept](cpp-conformance-improvements-2017.md#noexcept_removal)。

**Visual Studio 2017 15.7 版**：

- 新編譯器參數 [/Qspectre](build/reference/qspectre.md) 有助於減輕理論式執行側邊通道攻擊。 如需詳細資訊，請參閱 [Spectre mitigations in MSVC](https://blogs.msdn.microsoft.com/vcblog/2018/01/15/spectre-mitigations-in-msvc/) (MSVC 中的 Spectre 風險降低)。
- 適用於 Spectre 風險降低的新診斷警告。 如需詳細資訊，請參閱 [Spectre diagnostic in Visual Studio 2017 Version 15.7 Preview 4](https://blogs.msdn.microsoft.com/vcblog/2018/04/20/spectre-diagnostic-in-visual-studio-2017-version-15-7-preview-4/) (Visual Studio 2017 15.7 版 Preview 4 中的 Spectre 診斷)。
- /Zc 的新值 **/Zc:__cplusplus** 可正確報告 C++ 標準支援。 例如，當設定參數且編譯器處於 /std:c++17 模式時，值會擴大為 **201703L**。 如需詳細資訊，請參閱 [MSVC now correctly reports __cplusplus](https://blogs.msdn.microsoft.com/vcblog/2018/04/09/msvc-now-correctly-reports-__cplusplus/) (MSVC 現在會正確報告 __cplusplus)。

## <a name="c-standard-library-improvements"></a>C++ 標準程式庫改善

- 次要 `basic_string` `_ITERATOR_DEBUG_LEVEL != 0` 診斷的改善。 字串機制中的 IDL 檢查若出錯，現在將會回報導致該錯誤的特定行為。 例如，您會看見「無法為字串迭代器取值，因為它超出範圍 (例如結尾迭代器)」，而不是「無法為字串迭代器取值」。
- 效能改善：讓 `basic_string::find(char)` 多載只呼叫 `traits::find` 一次。 先前已為長度為 1 的字串將其作為一般字串搜尋實作。
- 效能改善︰`basic_string::operator==` 現在會先檢查字串的大小再比較字串的內容。
- 效能改善︰移除了 `basic_string` 中的控制項結合程度，因為編譯器最佳化工具很難加以分析。 請注意，對所有短字串呼叫 `reserve` 都不會執行任何動作，但仍有成本。
- 我們新增了 \<any\>、\<string_view\>、`apply()`、`make_from_tuple()`。
- `std::vector` 已經過大幅調整，以提高正確性和效能︰現已依標準的要求，正確處理插入/定位期間的別名；強式例外狀況保證現在會在標準透過 `move_if_noexcept()` 和其他邏輯提出要求時提供，而且插入/定位會執行較少的項目作業。
- C++ 標準程式庫現在會避免為 null 假想指標取值。
- 新增了 \<optional\>、\<variant\>、`shared_ptr::weak_type` 和 \<cstdalign\>。
- 讓 `min(initializer_list)`、`max(initializer_list)` 和 `minmax(initializer_list)`，及 `min_element()`、`max_element()` 和 `minmax_element()` 中可使用 C++ 14 `constexpr`。
- 改善了 `weak_ptr::lock()` 效能。
- 修正了 `std::promise` 移動指派運算子原本可能造成程式碼永久封鎖的問題。
- 修正了 `atomic<T*>` 隱含轉換為 `T*` 這項編譯器錯誤。
- `pointer_traits<Ptr>` 現在會正確偵測 `Ptr::rebind<U>`。
- 修正了 `move_iterator` 減法運算子缺少 `const` 限定詞這項問題。
- 修正了要求 `propagate_on_container_copy_assignment` 和 `propagate_on_container_move_assignment` 的具狀態使用者定義配置器會產生錯誤程式碼而不發出訊息的問題。
- `atomic<T>` 現已容許多載 `operator&()`。
- 為了新增編譯器輸送量，C++ 標準程式庫標頭現在會避免包含非必要編譯器內建的宣告。
- 稍微改善不正確 `bind()` 呼叫的編譯器診斷。
- 改善了 `std::string` 和 `std::wstring` 移動建構函式的效能，改善幅度超過三倍。

如需標準程式庫改善的完整清單，請參閱 [VS 2017 RTM 中的標準程式庫修正](https://blogs.msdn.microsoft.com/vcblog/2017/02/06/stl-fixes-in-vs-2017-rtm/) \(英文\)。

### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 15.3 版

#### <a name="c17-features"></a>C++17 功能

已實作數個額外的 C++17 功能。 如需詳細資訊，請參閱 [Visual C++ 語言一致性](cpp-conformance-improvements-2017.md#improvements_153)。

#### <a name="other-new-features"></a>其他新功能

- 已實作 P0602R0「Variant 和 Optional 應隨意地散佈 Copy/Move」。
- 標準程式庫現已正式容許透過 [/GR-](build/reference/gr-enable-run-time-type-information.md) 選項停用動態 RTTI。 `dynamic_pointer_cast()` 和 `rethrow_if_nested()` 原本就都需要 `dynamic_cast`，因此標準程式庫現已將其標示為 **/GR-** 下的 `=delete`。
- 就算已透過 **/GR-** 停用動態 RTTI，「靜態 RTTI」(形式為 `typeid(SomeType)`) 仍可使用，並能提供數個標準程式庫元件。 標準程式庫現在也支援停用此項，方法是透過 **/D\_HAS\_STATIC\_RTTI=0**。 請注意，這會停用 `std::function` 的 `std::any`、`target()` 和 `target_type()` 成員函式，及 `std::shared_ptr` 和 `std::weak_ptr` 的 `get_deleter()` friend 成員函式。

#### <a name="correctness-fixes-in-visual-studio-2017-version-153"></a>Visual Studio 2017 15.3 版中的正確性修正

- 標準程式庫容器現在將其 `max_size()` 包含至 `numeric_limits<difference_type>::max()` 中，而不是包含在 `size_type` 的 `max()` 中。 如此可確保該容器迭代器上 `distance()` 的結果能以 `distance()` 的傳回型別代表。
- 修正了缺少特舒化 `auto_ptr<void>` 的問題。
- 若長度引數不是整數型別，`for_each_n()`、`generate_n()` 和 `search_n()` 演算法原本無法編譯，而現在會嘗試將非整數長度轉換為迭代器的 `difference_type`。
- `normal_distribution<float>` 不會再於標準程式庫內，對從雙精確度縮減為浮點數的情況發出警告。
- 修正了部分 `basic_string` 作業，這些作業先前在檢查大小溢位上限時會與 `npos` 而非 `max_size()` 比較。
- `condition_variable::wait_for(lock, relative_time, predicate)` 先前會在發生假性喚醒前，等候完整的相對時間。 現在則只會等候單一間隔的相對時間。
- 依標準的規定，`future::get()` 現在會使 `future` 無效。
- 因 `iterator_traits<void *>` 之前會嘗試形成 `void&`，而成為硬碟錯誤，現在則會完全成為空的結構，以允許在 "is iterator" SFINAE 條件中使用 `iterator_traits`。
- Clang **-Wsystem-headers** 回報的部分警告已獲修正。
- 同時也修正了由 Clang **-Wmicrosoft-exception-spec** 回報的「宣告中的例外狀況規格不符合先前的宣告」這項問題。
- 同時已修正由 Clang 和 C1XX 所回報的 mem-initializer-list 排序錯誤。
- 先前未排序的容器在容器本身已交換的情況下，並不會交換其 hasher 或述詞。 現在它們已會這麼做。
- 許多容器交換作業現在標示了 `noexcept` (因為我們的標準程式庫永遠不會試圖在偵測到 non-`propagate_on_container_swap` non-equal-allocator 未定義行為條件時擲出例外狀況)。
- 許多 `vector<bool>` 作業現在標示了 `noexcept`。
- 標準程式庫現在會強制將配置器 `value_type` (在 C++17 模式中) 與退出安全出口配對。
- 修正了對 `basic_string` 進行 self-range-insert 會擾亂字串內容的某些條件。 (注意：針對 vectors 進行 self-range-insert 仍受標準所禁止)。
- `basic_string::shrink_to_fit()` 不再受配置器的 `propagate_on_container_swap` 影響。
- `std::decay` 現在會處理不受歡迎的函式類型 (也就是 cv 限定和 (或) ref 限定的函式類型)。
- 已變更 include 指示詞以使用適當的區分大小寫和斜線，以改善可攜性​​。
- 修正了警告 C4061「case 標籤未明確處理列舉 '*enumeration*' 參數中的列舉程式 '*enumerator*'」。 此警告為 off-by-default，並已修正為標準程式庫針對警告之一般原則的例外狀況。 (標準程式庫無 **/W4** 瑕疵，但不會嘗試達到無 **/Wall** 瑕疵。 許多 off-by-default 警告都極為吵雜，且不應該作為一般用途使用)。
- 改善 `std::list` 偵錯檢查。 List 迭代器現在會檢查 `operator->()`，且 `list::unique()` 現在會將迭代器標示為無效。
- 修正了 `tuple` 中的 uses-allocator 中繼程式設計。

#### <a name="performancethroughput-fixes"></a>效能/輸送量修正

- 解決了與 `noexcept` 的互動，這原本會導致無法將 `std::atomic` 實作內嵌至使用結構化例外狀況處理 (SEH) 的函式。
- 標準程式庫的內部 `_Deallocate()` 函式已變更為較小的程式碼，使其適合內嵌至更多位置。
- `std::try_lock()` 已從使用遞迴改為使用套件展開。
- 改善了 `std::lock()` 鎖死迴避演算法，從原本對所有鎖定重複執行 `try_lock()` ，改為使用 `lock()` 作業。
- 讓 `system_category::message()` 中可進行具名傳回值最佳化。
- `conjunction` 和 `disjunction` 現在會的具現化對象為 N + 1 類型，而非 2N + 2 類型。
- `std::function` 不會再對每個已清除類型的可呼叫項目將配置器支援機制具現化，如此可在會傳遞許多相異 Lambda 到 `std::function` 的程式中，改善輸送量並減少 .obj 大小。
- `allocator_traits<std::allocator>` 包含手動內嵌的 `std::allocator` 作業，以減少只透過 `allocator_traits` 與 `std::allocator` 互動之程式碼 (也就是大部分程式碼) 中的程式碼大小。
- C++11 最小配置器介面現已由標準程式庫直接呼叫 `allocator_traits` 來處理，而非將配置器包裝在內部類別 `_Wrap_alloc` 中。 這會減少為支援配置器所產生的程式碼大小、改善最佳化工具在某些情況下對標準程式庫容器進行判斷的能力，並提供更佳的偵錯體驗 (如同您現在會在偵錯工具中看見您的配置器類型，而非 `_Wrap_alloc<your_allocator_type>`)。
- 移除了自訂 `allocator::reference` 的中繼程式設計，因為實際上並不允許配置器自訂該項目。 (配置器可以使容器使用自訂的指標，但不能使用自訂的參考)。
- 編譯器前端被教導在範圍架構的 for 迴圈中解除偵錯迭代器的包裝，以改善偵錯組建的效能。
- `shrink_to_fit()` 和 `reserve()` 的 `basic_string` 內部縮小路徑已不再位於重新配置作業的路徑中，以減少所有變動成員的程式碼大小。
- `basic_string` 的內部成長路徑已不再位於 `shrink_to_fit()` 的路徑中。
- 現已將 `basic_string` 變動作業納入非配置的快速路徑和配置的慢速路徑函式中，讓一般的無重新配置案例更容易內嵌至呼叫者。
- `basic_string` 變動作業現在會以所需狀態建構重新配置的緩衝區，而非就地調整大小。 例如，在字串開頭進行插入，現在將會使插入點之後的內容移動一次 (無論是向下移動，或是移動至新配置的緩衝區)，而非有如重新配置案例一般移動兩次 (移動至新配置的緩衝區，然後再向下移動)。
- 在 \<string\> 中呼叫 C 標準程式庫的作業現在會快取 `errno` 位址，以免與 TLS 間重複互動。
- 簡化了 `is_pointer` 實作。
- 以函式為基礎的運算式 SFINAE 已變更為以 `struct` 和 `void_t` 為基礎。
- 標準程式庫演算法現在會避免會後續累加的迭代器。
- 已修正在 64 位元系統上使用 32 位元配置器時會出現的截斷警告。
- 透過在情況允許時重複使用緩衝區，`std::vector` 移動指派現在在非 POCMA non-equal-allocator 案例中變得更有效率。

#### <a name="readability-and-other-improvements"></a>可讀性和其他改善

- 標準程式庫現在會無條件使用 C++14 `constexpr`，而不使用已定義條件的巨集。
- 標準程式庫現在會於內部使用別名樣板。
- 標準程式庫現在會於內部使用 `nullptr`，而不使用 `nullptr_t{}`。 (已經完全清除 NULL 的內部使用情況。 正在逐步清除 0-as-null 的內部使用情況)。
- 標準程式庫現在會於內部使用 `std::move()`，而非誤用 `std::forward()`。
- `static_assert(false, "message")` 已變更為 `#error message`。 這改善了編譯器診斷，因為 `#error` 會使編譯立刻停止。
- 標準程式庫已不再將函式標示為 `__declspec(dllimport)`。 新式的連結器已不再需要這麼做。
- 已將 SFINAE 擷取至預設樣板引數；與傳回類型和函式引數類型相比，這將會減少雜亂的情形。
- \<random\> 中的偵錯檢查現在會使用標準程式庫的一般機制，而不使用會對 **stderr** 呼叫 `fputs()` 的內部函式 `_Rng_abort()`。 此函式的實作目前已針對二進位相容性做出保留，但是已在下一個與二進位不相容的標準程式庫版本中移除。

### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 15.5 版

根據 C++17 標準，已新增、取代或移除數項標準程式庫功能。 如需詳細資訊，請參閱 [Visual Studio 中的 C++ 一致性改善](cpp-conformance-improvements-2017.md#improvements_155)。

#### <a name="new-experimental-features"></a>新的實驗性功能

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
- 下列平行演算法已新增簽章但目前未平行化；分析顯示，將只會移動或排列項目的演算法平行化並沒有任何好處：
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

#### <a name="performance-fixes-and-improvements"></a>效能修正和改善

- `basic_string<char16_t>` 現在會與 `basic_string<wchar_t>` 納入相同的 `memcmp`、`memcpy` 及相似的最佳化。
- 我們在 Visual Studio 2015 Update 3 中進行的「避免複製函式」顯示了最佳化工具有一項限制會導致函式指標無法內嵌，而這項問題已獲得解決，從而恢復 `lower_bound(iter, iter, function pointer)` 的效能。
- 現在會先將迭代器解除包裝再檢查順序，讓迭代器偵錯對 `includes`、`set_difference`、`set_symmetric_difference` 和 `set_union` 輸入執行的順序驗證得以減輕額外負荷。
- `std::inplace_merge` 現在會跳過已就位的項目。
- 建構 `std::random_device` 不會再建構並終結 `std::string`。
- `std::equal` 和 `std::partition` 具有跳躍執行緒最佳化傳遞，可免去迭代器比較。
- 當 `std::reverse` 是已傳遞至可完整複製之 `T` 的指標時，現在會分派至手寫的向量化實作。
- 已指示 `std::fill`、`std::equal` 和 `std::lexicographical_compare` 如何分派至 `std::byte` 和 `gsl::byte` (及其他 char 一類的列舉和列舉類別) 的 `memset` 和 `memcmp`。 請注意，`std::copy` 使用 `is_trivially_copyable` 分派，因此不需任何變更。
- 標準程式庫不再包含空的大括弧解構函式，其唯一的行為是使類型成為 non-trivially-destructible。

#### <a name="correctness-fixes-in-visual-studio-2017-version-155"></a>Visual Studio 2017 15.5 版中的正確性修正

- 按照標準的規定，`std::partition` 現在會呼叫述詞 N 次，而不是 N + 1 次。
- 在 15.5 版中，已修復 15.3 版中嘗試避免使用魔術靜態這項問題。
- `std::atomic<T>` 不再要求 `T` 必須預設為可建構的。
- 採用對數時間的堆積演算法不再執行線性時間判斷提示，因為當啟用迭代器偵錯時，輸入其實就是堆積。
- `__declspec(allocator)` 現在只會為 C1XX 而防護，以防止 Clang 不了解此 declspec 而發出警告。
- `basic_string::npos` 現在可作為編譯時間常數。
- C++17 模式中的 `std::allocator` 現在會正確處理過度對齊類型 (對齊大於 `max_align_t` 的類型) 的配置，除非 **/Zc:alignedNew-** 加以停用。  例如，具有 16 或 32 位元組對齊的物件向量現在會正確對齊 SSE 和 AVX 指令。

### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 15.6 版

- \<memory_resource>
- 程式庫基本概念 V1
- 刪除 polymorphic_allocator 指派
- 改善類別範本引數推斷

### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 15.7 版

- 平行演算法的支援不再為實驗性
- \<filesystem> 的新實作
- 基礎字串轉換 (部分)
- std::launder()
- std::byte
- hypot(x,y,z)
- 避免不必要的 decay
- 數學特殊函式
- constexpr char_traits
- STL 推斷指引

如需詳細資訊，請參閱 [Visual C++ 語言一致性](visual-cpp-language-conformance.md)。

## <a name="other-libraries"></a>其他程式庫

### <a name="open-source-library-support"></a>開放原始碼程式庫支援

**Vcpkg** 是一種開放原始碼命令列工具，可大幅簡化在 Visual Studio 中取得和建置開放原始碼 C++ 靜態程式庫和 DLLS 的程序。 如需詳細資訊，請參閱 [vcpkg：C++ 的套件管理員](vcpkg.md)。

**Visual Studio 2017 15.5 版**：

### <a name="cpprest-sdk-290"></a>CPPRest SDK 2.9.0

CPPRestSDK 是適用於 C++ 的跨平台 Web API，已更新成 2.9.0 版。 如需詳細資訊，請參閱 [CppRestSDK 2.9.0 is available on GitHub](https://blogs.msdn.microsoft.com/vcblog/2016/10/21/cpprestsdk-2-9-0-is-available-on-github/)(GitHub 上可用的 CppRestSDK 2.9.0)。

### <a name="atl"></a>ATL

- 另一組 name-lookup 一致性修正
- 現有的移動建構函式和移動指派運算子現在已正確標示為非擲回
- 取消隱藏和 atlstr.h 中區域靜態安全執行緒初始化有關的有效警告 C4640
- 區域靜態的安全執行緒初始化已在 [使用 ATL AND 建置 DLL] 時在 XP 工具組中自動關閉。 不過，此情況以已不再適用。 如果需要關閉安全執行緒初始化，您可以在您的專案設定中新增 **/Zc:threadSafeInit-**。

### <a name="visual-c-runtime"></a>Visual C++ 執行階段

- 「控制流程防護」符號的新標頭 ‘cfguard.h’。

## <a name="c-ide"></a>C++ IDE

- C++ 原生專案的組態變更效能現已提升，而 C++/CLI 專案的組態變更效能則更佳。 解決方案組態在首次啟用時將會較快，而它在後續啟用時將能幾乎瞬間完成。

**Visual Studio 2017 15.3 版**：

- 已重寫數個專案和程式碼精靈的簽章對話方塊樣式。
- [加入類別] 現在會直接啟動 [加入類別精靈]。 之前在這裡的所有其他項目，現在會在 [新增] > [新增項目] 下提供。
- Win32 專案現在在 [新增專案] 對話方塊的 [Windows Desktop] 類別下。
- **Windows 主控台**和**傳統型應用程式**範本現在會建立專案，而不顯示精靈。 相同類別下有新的 [Windows Desktop 精靈]，其顯示的選項與舊版 [Win32 主控台應用程式精靈] 相同。

**Visual Studio 2017 15.5 版**：

使用 IntelliSense 引擎進行重構和程式碼瀏覽的數項 C++ 作業執行速度更快。 下列數值是根據含有 3500 個專案的 Visual Studio Chromium 方案而來：

|||
|-|-|
|功能|效能改善|
|重新命名|5.3 倍|
|變更簽章 |4.5 倍|
|尋找所有參考|4.7 倍|

C++ 現在支援以 Ctrl+按一下 [移至定義]，如此可輕鬆使用滑鼠瀏覽至定義。 Productivity Power Tools 套件的 Structure Visualizer 現在預設也會隨附於產品。

## <a name="intellisense"></a>IntelliSense

- 現在預設使用新的 SQLite 型資料庫引擎。 這會加速 [移至定義] 和 [尋找所有參考] 這類的資料庫作業，並會大幅改善初始解決方案剖析階段。 該設定已移至 [工具] > [選項] > [文字編輯器] > [C/C++] > [進階] (原位於 ...[C/C++] | [實驗性] 下)。

- 我們已對未使用先行編譯標頭檔的專案及檔案提升 IntelliSense 效能，將會為目前檔案中的標頭建立自動先行編譯標頭檔。

- 我們也為錯誤清單中的 IntelliSense 錯誤新增了錯誤篩選及說明。 現在按一下錯誤資料行即可進行篩選。 此外，按一下特定錯誤或按下 F1 鍵，將會啟動線上搜尋錯誤訊息。

  ![錯誤清單](media/ErrorList1.png "錯誤清單")

  ![篩選出的錯誤清單](media/ErrorList2.png "篩選出的錯誤清單")

- 新增了依種類篩選成員清單項目的功能。

  ![成員清單篩選](media/mlfiltering.png "成員清單篩選")

- 新增了實驗性的預測性 IntelliSense 功能，提供成員清單中出現項目的內容相關篩選。 請參閱 [C++ IntelliSense Improvements - Predictive IntelliSense & Filtering](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/c-intellisense-improvements-predictive-intellisense-filtering/) (C++ IntelliSense 改善 - 預測性 IntelliSense 和篩選)。
- [尋找所有參考] (Shift+F12) 現可協助您輕鬆搜索，即使在複雜的程式碼基底亦然。 它提供進階分組、篩選、排序、在結果內搜尋和顏色標示 (適用於某些語言)，因此您可以清楚了解您的參考。 針對 C++，新的 UI 包含要讀取或寫入變數的相關資訊。
- [點改為箭號] IntelliSense 功能已從實驗性改為進階，現在預設為啟用。 編輯器功能 [展開範圍] 和 [展開優先順序] 也已從實驗性功能改為進階功能。
- 根據預設，現已可使用實驗性重構功能 [變更簽章] 和 [擷取函式]。
- C++ 專案實驗性的 [加快專案載入] 功能。 C++ 專案會在您下次開啟時更快載入，之後即以極快速度載入！
- 其中有部分功能通用於其他語言，部分功能則是 C++ 的特定功能。 如需這些新功能的詳細資訊，請參閱[宣布 Visual Studio "15"](https://blogs.msdn.microsoft.com/visualstudio/2016/10/05/announcing-visual-studio-15-preview-5/)。

**Visual Studio 2017 15.7 版**：新增對 ClangFormat 的支援。 如需詳細資訊，請參閱 [ClangFormat Support in Visual Studio 2017](https://blogs.msdn.microsoft.com/vcblog/2018/03/13/clangformat-support-in-visual-studio-2017-15-7-preview-1/) (Visual Studio 2017 中的 ClangFormat 支援)。

## <a name="non-msbuild-projects-with-open-folder"></a>使用開啟資料夾的非 MSBuild 專案

Visual Studio 2017 推出了 [開啟資料夾] 功能，讓您可在包含原始程式碼的資料夾中撰寫程式碼、建置和偵錯，而不需建立任何解決方案或專案。 如果您的專案不是 MSBuild 專案，則這可讓開始使用 Visual Studio 更為簡單。 透過 [開啟資料夾]，您就能使用 Visual Studio 已為 MSBuild 專案提供的強大程式碼理解、編輯、建置和偵錯功能。 如需詳細資訊，請參閱 [Visual C++ 中的「開啟資料夾」專案](ide/non-msbuild-projects.md)。

- [開啟資料夾] 體驗的改良。 您可以透過這些 .json 檔案自訂體驗：
  - CppProperties.json，用以自訂 IntelliSense 及瀏覽體驗。
  - Tasks.json，用以自訂建置步驟。
  - Launch.json，用以自訂偵錯經驗。

**Visual Studio 2017 15.3 版**：

- 已改善針對替代編譯器和建置環境 (例如 MinGW 和 Cygwin) 的支援。 如需詳細資訊，請參閱[搭配 Visual C++ 和「開啟資料夾」使用 MinGW 和 Cygwin](https://blogs.msdn.microsoft.com/vcblog/2017/07/19/using-mingw-and-cygwin-with-visual-cpp-and-open-folder/) \(英文\)。
- 新增了在 CppProperties.json 和 CMakeSettings.json 中定義全域和組態專用環境變數的支援。 這些環境變數可供 launch.vs.json 中定義的偵錯組態和 tasks.vs.json 中的工作取用。 如需詳細資訊，請參閱 [Customizing your Environment with Visual C++ and Open Folder](https://blogs.msdn.microsoft.com/vcblog/2017/11/02/customizing-your-environment-with-visual-c-and-open-folder/) (使用 Visual C++ 和開啟資料夾來自訂您的環境)。
- 已改善針對 CMake Ninja 產生器的支援，包括能夠輕鬆以 64 位元平台作為目標的能力。

## <a name="cmake-support-via-open-folder"></a>透過開啟資料夾的 CMake 支援

Visual Studio 2017 支援使用 CMake 專案，而不需要轉換為 MSBuild 專案檔 (.vcxproj)。 如需詳細資訊，請參閱 [Visual C++ 中的 CMake 專案](ide/cmake-tools-for-visual-cpp.md)。 使用 [開啟資料夾] 開啟 CMake 專案會自動為 C++ 編輯、建置和偵錯設定環境。

- 無須在根資料夾中建立 CppProperties.json 檔案，C++ IntelliSense 即可運作。 此外，我們新增了下拉式清單，可讓使用者輕易地切換 CMake 和 CppProperties.json 檔案所提供的設定。

- 透過與 CMakeLists.txt 檔案位於相同資料夾的 CMakeSettings.json 檔案，支援進一步設定。

  ![Cmake 開啟資料夾](media/cmake_cpp.png "CMake 開啟資料夾")

**Visual Studio 2017 15.3**：已新增針對 CMake Ninja 產生器的支援。

**Visual Studio 2017 15.5 版**：新增對匯入現有 CMake 快取的支援。

**Visual Studio 2017 15.7 版**：新增對 CMake 3.11、CMake 專案中的程式碼分析、[方案總管] 中的目標檢視、用於產生快取的選項及單一檔案編譯的支援。 如需詳細資訊，請參閱 [CMake Support in Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2018/04/09/cmake-support-in-visual-studio-targets-view-single-file-compilation-and-cache-generation-settings/) (Visual Studio 中的 CMake 支援) 和 [Visual C++ 中的 CMake 專案](ide/cmake-tools-for-visual-cpp.md)。

## <a name="windows-desktop-development-with-c"></a>使用 C++ 進行 Windows 桌面開發

我們現在提供安裝原始 C++ 工作負載時更細微的安裝體驗。 我們已新增可選取的元件，讓您能夠只安裝所需的工具。  請注意，安裝程式 UI 中所列元件指出的安裝大小，並不準確且低估總大小。

若要在 C++ 桌面工作負載中成功建立 Win32 專案，您必須安裝工具組和 Windows SDK。 安裝建議 (選取) 的元件 **VC++ 2017 v141 工具組 (x86、x64)** 和 **Windows 10 SDK (10.0.nnnnn)** 可確保其正常運作。 如果未安裝必要工具，將無法成功建立專案，而且精靈將會停止回應。

**Visual Studio 2017 15.5 版**：

Visual Studio Build Tools (先前以獨立產品形式提供) 現在以工作負載形式包含在 Visual Studio 安裝程式中。 此工作負載只會安裝建置 C++ 專案所需的工具，而不會安裝 Visual Studio IDE。 v140 和 v141 工具組都包含在內。 v141 工具組包含 Visual Studio 2017 15.5 版的最新改善功能。 如需詳細資訊，請參閱 [Visual Studio Build Tools now include the VS2017 and VS2015 MSVC Toolsets](https://blogs.msdn.microsoft.com/vcblog/2017/11/02/visual-studio-build-tools-now-include-the-vs2017-and-vs2015-msvc-toolsets/) (Visual Studio 建置工具現在包含 VS2017 和 VS2015 MSVC 工具組)。

## <a name="linux-development-with-c"></a>使用 C++ 的 Linux 程式開發

熱門的 [Visual C++ for Linux Development](https://visualstudiogallery.msdn.microsoft.com/725025cf-7067-45c2-8d01-1e0fd359ae6e) 擴充功能現已納入 Visual Studio 中。 這個安裝提供您開發在 Linux 環境上執行的 C++ 應用程式，並進行偵錯所需的一切。

**Visual Studio 2017 15.2 版**：

跨平台程式碼共用和類型視覺效果已經過功能改善。 如需詳細資訊，請參閱[針對跨平台程式碼共用和類型視覺效果的 Linux C++ 改善](https://blogs.msdn.microsoft.com/vcblog/2017/05/10/linux-cross-platform-and-type-visualization/) \(英文\)。

**Visual Studio 2017 15.5 版**：

- Linux 工作負載已新增對 **rsync** 的支援，當成 **sftp** 的替代方案，以將檔案同步至遠端 Linux 電腦。
- 新增以 ARM 為目標的交互編譯支援。 若要在安裝中啟用這項支援，請選擇 [使用 C++ 進行 Linux 開發] 工作負載，並選取 [內嵌和 IoT 開發] 的選項。 這會將 ARM GCC 交互編譯工具和 Make 新增至您的安裝。 如需詳細資訊，請參閱 [ARM GCC Cross Compilation in Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2017/10/23/arm-gcc-cross-compilation-in-visual-studio/) (Visual Studio 中的 ARM GCC 交互編譯)。
- 新增對 CMake 的支援。 您現在可以使用現有的 CMake 程式碼基底，而不必將它轉換成 Visual Studio 專案。 如需詳細資訊，請參閱[設定 Linux CMake 專案](linux/cmake-linux-project.md)。
- 新增對執行遠端工作的支援。 這項功能可讓您在 Visual Studio 的 連線管理員中定義的遠端系統上執行任何命令。 遠端工作也會提供將檔案複製到遠端系統的功能。
如需詳細資訊，請參閱[設定 Linux CMake 專案](linux/cmake-linux-project.md)。

**Visual Studio 2017 15.7 版**：

- 對 Linux 工作負載案例的各項改善。 如需詳細資訊，請參閱 [Linux C++ Workload improvements to the Project System, Linux Console Window, rsync and Attach to Process](https://blogs.msdn.microsoft.com/vcblog/2018/03/13/linux-c-workload-improvements-to-the-project-system-linux-console-window-rsync-and-attach-to-process/) (專案系統、Linux 主控台視窗、rsync 及附加至處理序的 Linux C++ 工作負載改善)。
- 適用於遠端 Linux 連線標頭的 IntelliSense。 如需詳細資訊，請參閱 [IntelliSense for Remote Linux Headers](https://blogs.msdn.microsoft.com/vcblog/2018/04/09/intellisense-for-remote-linux-headers/) (適用於遠端 Linux 標頭的 IntelliSense) 和[設定 Linux CMake 專案](linux/cmake-linux-project.md)。

## <a name="game-development-with-c"></a>使用 C++ 的遊戲程式開發

使用 C++ 的完整功能建置由 DirectX 或 Cocos2d 技術提供的專業遊戲。

## <a name="mobile-development-with-c-android-and-ios"></a>使用 C++ 進行行動裝置應用程式開發 (Android 與 iOS)

您現在能夠使用可以 Android 及 iOS 為目標的 Visual Studio 建立行動應用程式並對其偵錯。

## <a name="universal-windows-apps"></a>通用 Windows App

C++ 以通用 Windows app 工作負載的選用元件形式提供。  升級 C++ 專案目前必須以手動方式完成。 如果您在 Visual Studio 2017 中開啟以 v140 為目標的 UWP 專案且未安裝 Visual Studio 2015，則需要在專案屬性頁中選取 v141 平台工具組。

## <a name="new-options-for-c-on-universal-windows-platform-uwp"></a>通用 Windows 平台 (UWP) 上 C++ 的新選項
您現在可使用新選項，為通用 Windows 平台及 Microsoft Store 撰寫和封裝 C++ 應用程式：您可以使用傳統型橋接器基礎結構來封裝現有的傳統型應用程式或 COM 物件，以透過 Microsoft Store 部署，或透過現有通道以側載的方式部署。 Windows 10 中的新功能可讓您以各種方式將 UWP 功能新增至傳統型應用程式。 如需詳細資訊，請參閱[傳統型橋接器](/windows/uwp/porting/desktop-to-uwp-root)。

**Visual Studio 2017 15.5 版**：新增 [Windows 應用程式封裝專案] 專案範本，可大幅簡化使用傳統型橋接器來封裝傳統型應用程式的工作。 該範本位於 [檔案] | [開新檔案] | [專案] | [已安裝] | [Visual C++] | [通用 Windows 平台] 中。 如需詳細資訊，請參閱[使用 Visual Studio 封裝應用程式 (傳統型橋接器)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net)。

撰寫新的程式碼時，您現在可以使用 C++/WinRT，它是一種標準 C++ 語言推演，適用於僅在標頭檔中實作的 Windows 執行階段。 它可讓您使用任何符合標準規範的 C++ 編譯器來編寫和使用 Windows 執行階段 API。 C++/WinRT 設計成將現代 Windows API 的第一級存取提供給 C++ 開發人員。 如需詳細資訊，請參閱 [C++/WinRT Available on GitHub](https://moderncpp.com/) (GitHub 上可用的 C++/WinRT)。

自 Windows SDK Insider Preview 的組建 17025 起，C++/WinRT 會隨附於 Windows SDK。 如需詳細資訊，請參閱 [C++/WinRT is now included the Windows SDK](https://blogs.msdn.microsoft.com/vcblog/2017/11/01/cppwinrt-is-now-included-the-windows-sdk/) (C++/WinRT 現在隨附於 Windows SDK)。

## <a name="clangc2-platform-toolset"></a>Clang/C2 平台工具組

Visual Studio 2017 隨附的 Clang/C2 工具組，現已支援 **/bigobj** 參數，這對於建置大型專案很重要。 它也包含數個重要的 Bug 修正，包括編譯器前端和後端。

## <a name="c-code-analysis"></a>C++ 程式碼分析

用於強制 [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines) 的 C++ Core Checkers 現已隨 Visual Studio 散發。 只要在專案屬性頁中的 [程式碼分析延伸模組] 頁面中啟用檢查程式，就能在您執行程式碼分析時包含延伸模組。 如需詳細資訊，請參閱[使用 C++ 核心指南檢查工具](/visualstudio/code-quality/using-the-cpp-core-guidelines-checkers)。

![CppCoreCheck](media/CppCoreCheck.png "CppCoreCheck 屬性頁面")

**Visual Studio 2017 15.3 版**：已針對與資源管理相關的規則加入支援。

**Visual Studio 2017 15.5 版**：新的 C++ Core Guidelines 檢查範圍涵蓋智慧型指標正確性、全域初始設定式是否正確使用，並標示 `goto` 等建構的使用和不正確的轉換。

某些您可以在 15.3 中找到的警告編號，在 15.5 中已不再使用。 這些警告已取代為更明確的檢查。

**Visual Studio 2017 15.6 版**：

- 新增對單一檔案分析的支援，以及分析執行階段效能的改善。 如需詳細資訊，請參閱 [C++ Static Analysis Improvements for Visual Studio 2017 15.6 Preview 2](https://blogs.msdn.microsoft.com/vcblog/2018/01/10/c-static-analysis-improvements-for-visual-studio-2017-15-6-preview-2/) (Visual Studio 2017 15.6 Preview 2 的 C++ 靜態分析改善)

**Visual Studio 2017 15.7 版**：

- 新增對 [/analyze:ruleset](build/reference/analyze-code-analysis.md) 的支援，這可讓您指定要執行的程式碼分析規則。
- 新增對其他 C++ Core Guidelines 規則的支援。  如需詳細資訊，請參閱[使用 C++ 核心指南檢查工具](/visualstudio/code-quality/using-the-cpp-core-guidelines-checkers)。

## <a name="unit-testing"></a>單元測試

**Visual Studio 2017 15.5 版**：

Google Test Adapter 和 Boost.Test Adapter 現在是 [使用 C++ 進行桌面開發] 工作負載的元件，並與 [測試清單編輯器] 整合。 新增對 Cmake 專案的 CTest 支援 (使用 [開啟資料夾])，但尚未與**測試總管**完全整合。 如需詳細資訊，請參閱[撰寫 C/C++ 的單元測試](/visualstudio/test/writing-unit-tests-for-c-cpp)。

**Visual Studio 2017 15.6 版**：

- 新增對 Boost.Test 動態程式庫支援的支援。
- 現在可以在 IDE 中使用 Boost.Test 項目範本。

如需詳細資訊，請參閱 [Boost.Test Unit Testing: Dynamic Library support and New Item Template](https://blogs.msdn.microsoft.com/vcblog/2018/01/10/boost-test-unit-testing-dynamic-library-support-and-new-item-template/) (Boost.Test 單元測試：動態程式庫支援與新項目範本)。

**Visual Studio 2017 15.7 版**：

新增對 C++ 單元測試專案的 [CodeLens](/visualstudio/ide/find-code-changes-and-other-history-with-codelens) 支援。 如需詳細資訊，請參閱 [Announcing CodeLens for C++ Unit Testing](https://blogs.msdn.microsoft.com/vcblog/2018/04/09/announcing-codelens-for-c-unit-testing/) (宣佈適用於 C++ 單元測試的 CodeLens)。

## <a name="visual-studio-graphics-diagnostics"></a>Visual Studio 圖形診斷

Visual Studio 圖形診斷是一組工具，用來記錄並分析 Direct3D 應用程式中的轉譯和效能問題。 圖形診斷功能可以與在 Windows 電腦、Windows 裝置模擬器或遠端電腦或裝置上本機執行的應用程式搭配使用。

- **頂點和幾何著色器的輸入和輸出：** 檢視頂點和幾何著色器之輸入和輸出的能力已是其中一項最常被要求的功能，現在於工具中也予以支援。 只要在 [管線階段] 檢視中選取 VS 或 GS 階段，即可開始檢查其在下表中的輸入和輸出。

  ![著色器的輸入/輸出](media/io-shaders.png)

- **在物件表格中搜尋和篩選︰** 提供快速且輕鬆的方式來尋找所尋找的資源。

  ![搜尋](media/search.png)

- **資源歷程記錄：** 這個新檢視提供簡化的方式，來查看在轉譯所擷取畫面格期間使用之資源的整個修改歷程記錄。 若要叫用任何資源的歷程記錄，只需要按一下任何資源超連結旁邊的時鐘圖示。

  ![資源歷程記錄](media/resource-history.png)

  這會顯示新的 [資源歷程記錄] 工具視窗，當中會填入資源的變更歷程記錄。

  ![資源歷程記錄變更](media/resource-history-change.png)

  請注意，如果啟用完整呼叫堆疊擷取來擷取您的畫面格 ([圖形診斷] 下的 [Visual Studio] > [工具] > [選項])，則可以在 Visual Studio 專案內快速推算和檢查每個變更事件的內容。

- **API 統計資料︰** 檢視畫面格中 API 使用方式的高階摘要。 在探索根本不了解所進行的呼叫或太常進行的呼叫時，這十分有用。 透過 [Visual Studio 圖形分析器] 中的 [檢視] > [API 統計資料] 可以存取此視窗。

  ![API 統計資料](media/api-stats.png)

- **記憶體統計資料︰** 檢視驅動程式針對您在畫面格中建立之資源所配置的記憶體數量。 您可透過 [Visual Studio 圖形分析器] 中的 [檢視] > [記憶體統計資料] 存取此視窗。 以滑鼠右鍵按一下並選擇 [全部複製] 可將資料複製到 CSV 檔案，以透過試算表檢視。

  ![記憶體統計資料](media/memory-stats.png)

- **畫面格驗證：** 新的錯誤和警告清單提供簡單的方法，以根據 Direct3D 偵錯層所偵測到的潛在問題來巡覽事件清單。 按一下 [Visual Studio 圖形分析器] 中的 [檢視] > [畫面格驗證] 開啟此視窗。 然後按一下 [執行驗證] 開始分析。 根據畫面格的複雜性而定，這可能需要幾分鐘的時間才能完成。

  ![畫面格驗證](media/frame-validation.png)

- **D3D12 的畫面格分析：** 透過畫面格分析使用導向式「假設」實驗來分析繪製呼叫效能。 切換至 [畫面格分析] 索引標籤，然後執行分析以檢視報表。 如需詳細資訊，請觀看 [GoingNative 25: Visual Studio Graphics Frame Analysis](https://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool) (GoingNative 25：Visual Studio 圖形畫面格分析) 視訊。

  ![畫面格分析](media/frame-analysis.png)

- **GPU 使用量改善：** 使用 GPU 檢視或 Windows Performance Analyzer (WPA) 工具開啟透過 Visual Studio GPU 使用量分析工具所採取的追蹤，以進行更詳細的分析。 如果您已安裝 Windows 效能工具組，則在工作階段概觀的右下方會有兩個超連結：一個用於 WPA，另一個則用於 GPU 檢視。

  ![GPU 使用量](media/gpu-usage.png)

  透過此連結在 GPU 檢視中開啟的追蹤，支援 VS 與 GPU 檢視間之時間軸中的同步縮放和移動瀏覽。 VS 中有一個核取方塊用來控制是否啟用同步處理。

  ![GPU 檢視](media/gpu-view.png)
