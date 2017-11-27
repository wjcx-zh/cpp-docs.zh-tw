---
title: "Visual Studio 中 Visual C++ 的新功能 | Microsoft Docs"
ms.custom: 
ms.date: 11/15/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9927726585572f69bdf121c4ed71e8b034fc1ed3
ms.sourcegitcommit: 1b480aa74886930b3bd0435d71cfcc3ccda36424
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="whats-new-for-visual-c-in-includevsdev15mdmiscincludesvsdev15mdmd"></a>[!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] 中 Visual C++ 的新功能

[!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] 帶來 Visual C++ 環境的多個更新與修正。 我們修正了編譯器及工具中超過 250 個 Bug 與回報的問題，其中多為客戶透過 [Microsoft Connect](https://connect.microsoft.com/VisualStudio "Microsoft Connect") 所提交。 感謝您回報 Bug！  如需所有 Visual Studio 新功能的詳細資訊，請瀏覽 [[!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] 的新功能](https://go.microsoft.com/fwlink/?linkid=834481)。

<!--The compiler and tools version number in [!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] is 14.10.24629. -->


## <a name="c-compiler"></a>C++ 編譯器

### <a name="c-conformance-improvements"></a>C++ 一致性改善
我們在本版中更新了 C++ 編譯器和標準程式庫，加強對 C++11 和 C++14 功能的支援，以及對 C++17 標準某些預期功能的基本支援。 如需詳細資訊，請參閱 [Visual Studio 2017 中的 C++ 一致性改善](cpp-conformance-improvements-2017.md)。

### <a name="new-compiler-switches"></a>新的編譯器參數  

 -**/std:c++14** 和 **/std:c++latest**︰這些編譯器參數可讓您在專案中選擇加入特定版本的 ISO C++ 程式設計語言。 如需詳細資訊，請參閱 [-std (指定語言標準版本)](build/reference/std-specify-language-standard-version.md)。 大部分的新草稿標準功能是由 /std:c++latest 參數所防護。 

**Visual Studio 2017 15.3 版**：**/std:c++17** 選項可啟用由 Visual C++ 編譯器實作的 C++17 功能集。 此選項會針對較新版工作草案中已變更或全新的功能，以及 C++ Standard 的瑕疵更新，停用編譯器和標準程式庫支援。

-[/permissive-](build/reference/permissive-standards-conformance.md)︰啟用所有嚴格標準一致性編譯器選項，並停用大部分 Microsoft 特定編譯器延伸模組 (舉例來說，不是 __declspec(dllimport)) (預設為關閉，但在未來的某個時間點將會預設為開啟)。

-[/diagnostics](build/reference/diagnostics-compiler-diagnostic-options.md)︰啟用顯示行號、行號和資料行，或行號和資料行以及找到診斷錯誤或警告之程式碼下方的插入點。

-[/debug:fastlink](build/reference/debug-generate-debug-info.md)：  
啟用最多 30% 更快的累加連結時間 (與Visual Studio 2015)，方法是不要將所有偵錯資訊複製到 PDB 檔案。 PDB 檔案改為指向用來建立可執行檔之物件和程式庫檔案的偵錯資訊。 請參閱 [Faster C++ build cycle in VS “15” with /Debug:fastlink](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/faster-c-build-cycle-in-vs-15-with-debugfastlink/) (VS “15” 中使用 /Debug:fastlink 的較快 C++ 組建循環) 和 [Recommendations to speed C++ builds in Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2016/10/26/recommendations-to-speed-c-builds-in-visual-studio/) (Visual Studio 中加速 C++ 建置的建議)。

[!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] 允許搭配使用 /sdl 與 /await。 我們已移除協同程式的 /RTC 限制。 

**Visual Studio 2017 15.5 版**：Visual C++ 編譯器支援約 75% 的 C++17 功能，包括結構化繫結、`constexpr` Lambda `if constexpr`、內嵌變數、摺疊運算式，並新增 `noexcept` 型別系統。 這些功能會在 /std:c++17 參數下提供。 /permissive- conformance 模式包含對兩階段名稱查閱的部分支援。 如需詳細資訊，請參閱 [Visual Studio 2017 中的 C++ 一致性改善](cpp-conformance-improvements-2017.md)。 

### <a name="codegen-security-diagnostics-and-versioning"></a>Codegen、安全性、診斷和版本控制
此版本為最佳化、程式碼產生、工具組版本控制，以及診斷方面帶來多項改善。 其中幾項值得注意的改善內容包括：  

- 改善重複的程式碼產生：支援常數整數除法的自動向量化，更容易識別 memset 模式。
- 改善的程式碼安全性：改善發出緩衝區溢位編譯器診斷，而且 /guard:cf 現在會防護產生跳躍表的 switch 陳述式。
- 版本控制：現在，每次 Visual C++ 工具組更新時，都只會更新內建前置處理器巨集 _MSC_VER 的值。 如需詳細資訊，請參閱 [Visual C++ Compiler Version](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/visual-c-compiler-version/) (Visual C++ 編譯器版本)。
- 新的工具組版面配置︰編譯器和相關建置工具在開發電腦上具有新的位置和目錄結構。 新的版面配置可並存安裝多個版本的編譯器。 如需詳細資訊，請參閱 [Compiler Tools Layout in Visual Studio "15"](https://blogs.msdn.microsoft.com/vcblog/2016/10/07/compiler-tools-layout-in-visual-studio-15/) (Visual Studio "15" 中的編譯器工具版面配置)。
- 改善的診斷：輸出視窗現在會顯示發生錯誤的資料行。 如需詳細資訊，請參閱 [C++ compiler diagnostics improvements in VS "15" Preview 5](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/c-compiler-diagnostics-improvements-in-vs-15-rc/) (VS "15" Preview 5 中的 C++ 編譯器診斷改善)。
- 使用共同常式時，已移除實驗關鍵字 "yield" (於 /await 參數下提供)。 您應該更新程式碼以改用 `co_yield`。 如需詳細資訊，請參閱 [Visual C++ 小組部落格 (英文)](https://blogs.msdn.microsoft.com/vcblog/)。 

**Visual Studio 2017 15.3 版**：針對編譯器中診斷的其他改善。 如需詳細資訊，請參閱 [Visual Studio 2017 15.3.0 中的診斷改善](https://blogs.msdn.microsoft.com/vcblog/2017/07/21/diagnostic-improvements-in-vs2017-15-3-0/) \(英文\)。

**Visual Studio 2017 15.5 版**：Visual C++ 執行階段效能將持續改善，以提高產生的程式碼品質。 這表示您可以直接重新編譯程式碼，而且您的應用程式執行速度會更快。 某些編譯器最佳化功能是全新的，例如條件式純量存放區的向量化、將 sin(x) 和 cos(x) 呼叫合併成新的 sincos(x)，以及從 SSA 最佳化工具排除多餘的指令。 其他編譯器最佳化功能則是現有功能的改善，例如條件運算式的向量化啟發學習法、更佳的迴圈最佳化，以及 float min/max codegen。 連結器有全新且更快的 /OPT:ICF 實作，最多可加速 9% 的連結時間，而且「累加連結」中有其他效能修正。 如需詳細資訊，請參閱 [/OPT (Optimizations)](https://docs.microsoft.com/en-us/cpp/build/reference/opt-optimizations) (/OPT (最佳化)) 和 [/INCREMENTAL (Link Incrementally)](https://docs.microsoft.com/en-us/cpp/build/reference/incremental-link-incrementally) (/INCREMENTAL (以累加方式連結))。

Visual C++ 支援 Intel 的 AVX-512，包括將 AVX-512 的新功能整合到 128 和 256 位元寬暫存器的向量長度指令。

在一般情況下使用 C++17 模式時，可使用 **/Zc:noexceptTypes-** 參數還原為 C++14 版的 `noexcept`。 這可讓您更新原始程式碼以符合 C++17，而不需要同時重寫所有 `throw()` 程式碼。 如需詳細資訊，請參閱[動態例外狀況規格移除和 noexcept](cpp-conformance-improvements-2017.md#noexcept_removal)。


## <a name="c-standard-library-improvements"></a>C++ 標準程式庫改善

* 次要 basic_string _ITERATOR_DEBUG_LEVEL != 0 診斷改良功能。 字串機制中的 IDL 檢查若出錯，現在將會回報導致該錯誤的特定行為。 例如，您會看見「無法為字串迭代器取值，因為它超出範圍 (例如結尾迭代器)」，而不是「無法為字串迭代器取值」。
* 效能改進︰讓 basic_string::find(char) 多載只呼叫 traits::find 一次。 先前已為長度為 1 的字串將其作為一般字串搜尋實作。
* 效能改進︰basic_string::operator== 現在會先檢查字串的大小，再比較字串的內容。
* 效能改進︰已移除 basic_string 中的控制項結合程度，編譯器最佳化工具很難加以分析。 解決 VSO# 262848「\<string\>: reserve() 做太多的工作」。 請注意，對於所有的短字串，呼叫保留仍有非零的正整數成本，且不會執行任何動作。
* 我們已新增 \<any\>、\<string_view\>、apply()、make_from_tuple()。
* std:: vector 已針對正確性和效能經過大幅度調整︰插入/定位期間的別名現在已針對標準所需正確地處理、標準透過 move_if_noexcept() 和其他邏輯要求強式例外狀況保證時即會加以提供，且插入/定位會執行較少的項目作業。
* C++ 標準程式庫現在會避免為 null 假想指標取值。
* 新增 \<optional\>、\<variant\>、shared_ptr::weak_type 及 \<cstdalign\>。
* 允許在 min/max/minmax(initializer_list) 及 min_element/max_element/minmax_element() 中使用 C++14 constexpr。
* 改善 weak_ptr::lock() 效能。
* 修正 std::promise 的移動指派運算子，這在之前可能造成程式碼永久封鎖。
* 已修正 atomic\<T \*\> 隱含轉換為 T \*的編譯器錯誤。
* pointer_traits\<Ptr\> 現在可正確偵測 Ptr::rebind\<U\>。
* 修正 move_iterator 減法運算子中遺失的 const 限定詞。
* 修正要求 propagate_on_container_copy_assignment 及 propagate_on_container_move_assignment 之具狀態使用者定義配置器的無訊息不正確程式碼產生。
* atomic\<T\> 現在可容許多載的 operator&()。
* 為了新增編譯器輸送量，C++ 標準程式庫標頭現在會避免包含非必要編譯器內建的宣告。
* 稍微改善不正確 bind() 呼叫的編譯器診斷。
* 已改善 std::string/std::wstring 的移動建構函式的效能，改善幅度超過 3 倍
* 如需標準程式庫改善的完整清單，請參閱 [VS 2017 RTM 中的標準程式庫修正](https://blogs.msdn.microsoft.com/vcblog/2017/02/06/stl-fixes-in-vs-2017-rtm/) \(英文\)。

### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 15.3 版

#### <a name="c17-features"></a>C++17 功能 
已實作數個額外的 C++17 功能。 如需詳細資訊，請參閱 [Visual C++ 語言一致性](cpp-conformance-improvements-2017.md#improvements_153)。

#### <a name="other-new-features"></a>其他新功能
* 已實作 P0602R0「Variant 和 Optional 應隨意地散佈 Copy/Move」。
* 標準程式庫現已正式容許透過 /GR- 停用動態 RTTI。 dynamic_pointer_cast() 和 rethrow_if_nested() 原本就需要 dynamic_cast，因此標準程式庫現在會在 /GR- 底下將它們標記為 =delete。
* 就算在動態 RTTI 已透過 /GR- 停用的情況下，「靜態 RTTI」(具有 typeid(SomeType) 形式) 仍然可供使用，並能提供數個標準程式庫元件。 標準程式庫現在也已支援停用此項，方法是透過 /D_HAS_STATIC_RTTI=0。 「請注意，這將會停用 std::any、std::function 的 target() 和 target_type()，以及 shared_ptr 的 get_deleter()。」

#### <a name="correctness-fixes"></a>正確性修正
* 標準程式庫容器現在會將其 max_size() 固定至 numeric_limits\<difference_type\>::max()，而非 size_type 的最大值。這能確保來自該容器之迭代器上的 distance() 結果，可在 distance() 的傳回類型中顯示。
* 已修正遺失的特製化 auto_ptr\<void\>。
* 先前在長度引數不是整數類型之下會無法編譯的 meow_n() 演算法，現在會嘗試將非整數的長度轉換為迭代器的 difference_type。
* normal_distribution\<float\> 已不再會於標準程式庫內針對從 double 縮小至 float 的情況發出警告。
* 已修正部分 basic_string 作業，這些作業先前在檢查大小上限溢位時會比較 npo，而非 max_size()。
* condition_variable::wait_for(lock, relative_time, predicate) 先前在發生假性喚醒時，會針對整個相對時間進行等候。 現在它只會針對相對時間的單一間隔進行等候。
* future::get() 現在會依據標準的規定，使未來無效。
* iterator_traits\<void \*\> 之前為磁碟錯誤，因為它會嘗試形成 void&;，它現在會完全成為空的結構，以允許在 "is iterator" SFINAE 條件之下使用 iterator_traits。
* 已修正由 Clang -Wsystem-headers 所回報的部分警告。
* 同時已修正由 Clang -Wmicrosoft-exception-spec 所回報的「宣告中的例外狀況規格不符合先前的宣告」。
* 同時已修正由 Clang 和 C1XX 所回報的 mem-initializer-list 排序錯誤。
* 先前未排序的容器在容器本身已交換的情況下，並不會交換其 hasher 或述詞。 現在它們已會這麼做。
* 許多容器交換作業現在已標記為 noexcept (因為我們的標準程式庫永遠不會試圖在偵測到 non-propagate_on_container_swap non-equal-allocator 未定義行為條件時擲出例外狀況)。
* 許多 vector\<bool\> 作業現已標記為 noexcept。
* 標準程式庫現在會強制將配置器 value_types (於 C++17 模式) 與退出逃生門進行配對。
* 已修正針對 basic_strings 進行 self-range-insert 會擾亂字串內容的某些情況。 (注意：針對 vectors 進行 self-range-insert 仍受標準所禁止)。
* basic_string::shrink_to_fit() 已不再受到配置器的 propagate_on_container_swap 所影響。
* std::decay 現在會處理不受歡迎的函式類型 (也就是 cv 限定和/或 ref 限定的函式類型)。
* 已變更 include 指示詞以使用適當的區分大小寫和斜線，以改善可攜性​​。
* 已修正警告 C4061「case 標籤不會明確處理列舉 'Kitten' 參數中的列舉程式 'Meow'」。 此警告為 off-by-default，並已修正為標準程式庫針對警告之一般原則的例外狀況。 (標準程式庫會是 /W4 clean，但不會嘗試達成 /Wall clean。 許多 off-by-default 警告都極為吵雜，且不應該作為一般用途使用)。
* 已改善 std::list 的偵錯檢查。 List 迭代器現在會檢查 operator->()，且 list::unique() 現在會將迭代器標記為已經失效。
* 已修正元組中的 uses-allocator 中繼程式設計。

#### <a name="performancethroughput-fixes"></a>效能/輸送量修正
* 已避開與 noexcept 的互動，使它無法防止內嵌 std::atomic 針對使用結構化例外狀況處理 (SEH) 的函式進行實作。
* 已變更標準程式庫的 internal _Deallocate() 函式以針對較小的程式碼進行最佳化，使它能內嵌至更多位置。
* 已變更 std::try_lock() 以使用封裝展開，而非遞迴。
* 已改善 std::lock() 的死結迴避演算法以使用 lock() 作業，而不是在 lock 的所有 try_lock() 上旋轉。
* 已啟用 system_category::message() 中的具名傳回值最佳化。
* 結合和分離現在會具現化 N + 1 類型，而非 2N + 2 類型。
* std::function 已不再會針對每個已清除類型的可呼叫項目具現化配置器支援機制，以針對會傳遞許多相異 Lambda 至 std::function 的程式改善輸送量並減少 .obj 大小。
* allocator_traits\<std::allocator\> 會包含手動內嵌的 std::allocator 作業，以降低僅透過 allocator_traits 與 std::allocator 互動之程式碼 (也就是大部分的程式碼) 的程式碼大小。
* C++11 最小配置器介面現已由標準程式庫直接呼叫 allocator_traits 來處理，而非將配置器包裝在內部類別 _Wrap_alloc 之中。 這會減少針對配置器支援所產生的程式碼大小、改善最佳化工具在某些情況下對標準程式庫容器進行判斷的能力，並提供更佳的偵錯體驗 (因為現在您會在偵錯工具中看見您的配置器類型，而非 _Wrap_alloc\<您的配置器類型\>)。
* 已移除針對自訂 allocator::reference 的中繼程式設計，在此之前並不允許對配置器進行自訂。 (配置器可以使容器使用自訂的指標，但不能使用自訂的參考)。
* 編譯器前端被教導在範圍架構的 for 迴圈中解除偵錯迭代器的包裝，以改善偵錯組建的效能。
* basic_string 針對 shrink_to_fit() 和 reserve() 的內部縮小路徑已不再位於重新配置作業的路徑中，以減少所有變動成員的程式碼大小。
* basic_string 的內部成長路徑已不再位於 shrink_to_fit() 的路徑中。
* basic_string 的變動作業現在會納入非配置的快速路徑和配置的慢速路徑函式之中，這使一般的無重新配置案例更容易內嵌至呼叫者。
* basic_string 的變動作業現在會以所需的狀態建構重新配置的緩衝區，而非就地調整大小。 例如，在字串開頭進行插入，現在將會使插入點之後的內容移動一次 (無論是向下移動，或是移動至新配置的緩衝區)，而非有如重新配置案例一般移動兩次 (移動至新配置的緩衝區，然後再向下移動)。
* 在 \<string\> 中呼叫 C 標準程式庫的作業現在會快取 errno 的位址，以移除與 TLS 之間的重複互動。
* 已簡化 is_pointer 的實作。
* 已完成將以函式為基礎的運算式 SFINAE 變更為以 struct/void_t 為基礎。
* 標準程式庫演算法現在會避免會後續累加的迭代器。
* 已修正在 64 位元系統上使用 32 位元配置器時會出現的截斷警告。
* 透過在可以的情況下重複使用緩衝區，使得 std::vector 移動指派在非 POCMA non-equal-allocator 案例中變得更有效率。

#### <a name="readability-and-other-improvements"></a>可讀性和其他改善
* 標準程式庫現在會無條件地使用 C++14 constexpr，而非已定義條件的巨集。
* 標準程式庫現在會於內部使用別名樣板。
* 標準程式庫現在會於內部使用 nullptr，而非 nullptr_t{}。 (已經完全清除 NULL 的內部使用情況。 正在逐步清除 0-as-null 的內部使用情況)。
* 標準程式庫現在會於內部使用 std::move()，而非樣式性地誤用 std::forward()。
* 已將 static_assert(false, "message") 變更為 #error 訊息。 這能改善編譯器診斷，因為 #error 會使編譯立即停止。
* 標準程式庫已不再會將函式標記為 __declspec(dllimport)。 新式的連結器已不再需要這麼做。
* 已將 SFINAE 擷取至預設樣板引數；與傳回類型和函式引數類型相比，這將會減少雜亂的情形。
* \<random\> 中的偵錯檢查現在會使用標準程式庫的一般機制，而非會針對 stderr 呼叫 fputs() 的內部函式 _Rng_abort()。 此函式的實作目前已針對二進位相容性做出保留，但是已在下一個與二進位不相容的標準程式庫版本中移除。 

### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 15.5 版
根據 C++17 標準，已新增、取代或移除數項標準程式庫功能。 如需詳細資訊，請參閱 [Visual Studio 中的 C++ 一致性改善](cpp-conformance-improvements-2017.md#improvements_155)。

#### <a name="new-experimental-features"></a>新的實驗性功能
* 提供對下列平行演算法的實驗性支援：
  * all_of
  * any_of
  * for_each
  * for_each_n
  * none_of
  * reduce
  * replace
  * replace_if
  * sort
* 下列平行演算法已新增簽章但目前未平行化；分析顯示，將只會移動或排列項目的演算法平行化並沒有任何好處：
  * copy
  * copy_n
  * fill
  * fill_n
  * 移動
  * reverse
  * reverse_copy
  * rotate
  * rotate_copy
  * swap_ranges

#### <a name="performance-fixes-and-improvements"></a>效能修正和改善
* basic_string\<char16_t> 現在會採用 basic_string\<wchar_t> 所採用的 memcmp、memcpy 等最佳化。
* Visual Studio 2015 Update 3 中「避免複製函式」工作所顯示的最佳化工具限制會使函式指標無法內嵌。已解決這項限制，並恢復 lower_bound(iter, iter, function pointer) 的效能。
* 迭代器偵錯的輸入順序驗證 (為了包含 set_difference、set_symmetric_difference 和 set_union) 所產生的額外負荷，已透過先解除包裝迭代器再檢查順序而降低。
* std::inplace_merge 現在會略過已在適當位置的項目。
* 建構 std::random_device 不會再建構，然後終結 std::string。
* std::equal 和 std::partition 具有跳躍執行緒最佳化傳遞，可減少迭代器比較。
* 當 std::reverse 傳遞至可完整複製的 T 指標時，現在會分派至手寫的向量化實作。
* 系統會指示 std::fill、std::equal 和 std::lexicographical_compare 如何分派至 std::byte 和 gsl::byte 的 memset/memcmp (及其他 char-ish 列舉和列舉類別)。 請注意，std::copy 使用 is_trivially_copyable 分派，因此不需要任何變更。
* STL 不再包含空的大括弧解構函式，其唯一的行為是將類型設為不可完整解構。

#### <a name="correctness-fixes"></a>正確性修正
* 按照標準規定，std::partition 現在會呼叫述詞 N 次，而不是 N + 1 次。
* 在 15.5 中，已修復 15.3 中嘗試避免使用 Magic 靜態變數的問題。
* std::atomic\<T> 不再要求 T 預設必須是可建構的。
* 採用對數時間的堆積演算法不再執行線性時間判斷提示，因為當啟用迭代器偵錯時，輸入其實就是堆積。
* __declspec(allocator) 現在只會作為 C1XX 的成立條件，以防止 Clang 不了解此 declspec 而發出警告。
* basic_string::npos 現在可作為編譯時間常數。
* std::allocator 現在會適當地處理 C++17 模式中過度對齊類型 (其對齊大於 max_align_t 的類型) 的配置 (除非 /Zc:alignedNew- 已停用)。  例如，具有 16 或 32 位元組對齊的物件向量，現在會正確對齊 SSE / AVX 指令。


## <a name="other-libraries"></a>其他程式庫

### <a name="open-source-library-support"></a>開放原始碼程式庫支援  
Vcpkg 是一種開放原始碼命令列工具，可大幅簡化在 Visual Studio 中取得和建置開放原始碼 C++ 靜態程式庫和 DLL 的程序。 如需詳細資訊，請參閱 [vcpkg：C++ 的套件管理員](vcpkg.md)。

**Visual Studio 2017 15.5 版** 

### <a name="cpprest-sdk-290"></a>CPPRest SDK 2.9.0  
CPPRestSDK 是適用於 C++ 的跨平台 Web API，已更新成 2.9.0 版。 如需詳細資訊，請參閱 [CppRestSDK 2.9.0 is available on GitHub](https://blogs.msdn.microsoft.com/vcblog/2016/10/21/cpprestsdk-2-9-0-is-available-on-github/)(GitHub 上可用的 CppRestSDK 2.9.0)。

### <a name="atl"></a>ATL
* 另一組 name-lookup 一致性修正
* 現有的移動建構函式和移動指派運算子現在已正確標示為非擲回
* 取消隱藏和 atlstr.h 中區域靜態安全執行緒初始化有關的有效警告 C4640
* 區域靜態的安全執行緒初始化已在 [使用 ATL AND 建置 DLL] 時在 XP 工具組中自動關閉。 不過，此情況以已不再適用。 如果需要關閉安全執行緒初始化，您可以在您的專案設定中新增 /Zc:threadSafeInit-。 

### <a name="visual-c-runtime"></a>Visual C++ 執行階段
* 「控制流程防護」符號的新標頭 ‘cfguard.h’。 

## <a name="c-ide"></a>C++ IDE

* C++ 原生專案的組態變更效能現已提升，而 C++/CLI 專案的組態變更效能則更佳。 解決方案組態在首次啟用時將會較快，而它在後續啟用時將能幾乎瞬間完成。

**Visual Studio 2017 15.3 版**：
* 已重寫數個專案和程式碼精靈的簽章對話方塊樣式。
* [加入類別] 現在會直接啟動 [加入類別精靈]。 之前在這裡的所有其他項目，現在會在 [新增] > [新增項目] 下提供。
* Win32 專案現在會在 [新增專案] 對話方塊的 [Windows 桌面] 類別下。
* Windows 主控台和傳統型應用程式範本現在會建立專案，而不顯示精靈。 相同類別下有新的 [Windows Desktop 精靈]，顯示與之前相同的選項。

**Visual Studio 2017 15.5 版**：使用 IntelliSense 引擎進行重構和程式碼瀏覽的數項 C++ 作業執行速度更快。 下列數值是根據含有 3500 個專案的 Visual Studio Chromium 方案而來： 
|||
|-|-|
|功能|效能改善| 
|重新命名|5.3 倍| 
|變更簽章 |4.5 倍| 
|尋找所有參考|4.7 倍| 

 
 
C++ 現在支援 Ctrl+按一下滑鼠左鍵以移至定義，如此可輕鬆使用滑鼠瀏覽至定義。 Productivity Power Tools 套件的 Structure Visualizer 現在預設也會隨附於產品。

## <a name="intellisense"></a>IntelliSense  
現在預設使用新的 SQLite 型資料庫引擎。 這會加速資料庫作業，如「移至定義」和「尋找所有參考」，也會大幅改善初始解決方案剖析階段。 設定已移至 [工具] | [選項] | [文字編輯器] | [C/C++] | [進階] (原位於 [C/C++] | [實驗] 下)。

* 我們已對未使用先行編譯標頭檔的專案及檔案提升 IntelliSense 效能，將會為目前檔案中的標頭建立自動先行編譯標頭檔。

* 我們也為錯誤清單中的 IntelliSense 錯誤新增了錯誤篩選及說明。 現在按一下錯誤資料行即可進行篩選。 此外，按一下特定錯誤或按下 F1 鍵，將會啟動線上搜尋錯誤訊息。

  ![錯誤清單](media/ErrorList1.png "錯誤清單")

  ![篩選出的錯誤清單](media/ErrorList2.png "篩選出的錯誤清單")

* 新增了依種類篩選成員清單項目的功能。

  ![成員清單篩選](media/mlfiltering.png "成員清單篩選")

* 新增了實驗性的預測性 IntelliSense 功能，提供成員清單中出現項目的內容相關篩選。 請參閱 [C++ IntelliSense Improvements - Predictive IntelliSense & Filtering](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/c-intellisense-improvements-predictive-intellisense-filtering/) (C++ IntelliSense 改善 - 預測性 IntelliSense 和篩選)。

* [尋找所有參考]\(Shift+F12) 現在可協助您輕鬆地解決，即使是在複雜的程式碼基底中也是一樣。 它提供進階分組、篩選、排序、在結果內搜尋和顏色標示 (適用於某些語言)，因此您可以清楚了解您的參考。 針對 C++，新的 UI 包含要讀取或寫入變數的相關資訊。

* [點改為箭號] IntelliSense 功能已從實驗性改為進階，現在預設為啟用。 編輯器功能 [展開範圍] 和 [展開優先順序] 也從實驗性改為進階。

* 實驗性的重構功能 [變更簽章] 及 [擷取函式] 現在預設為可用。

* C++ 專案「讓專案更快載入」的實驗性功能。 C++ 專案會在您下次開啟時更快載入，之後即以極快速度載入！

其中有部分功能通用於其他語言，部分功能則是 C++ 的特定功能。 如需這些新功能的詳細資訊，請參閱 [Announcing Visual Studio “15”](https://blogs.msdn.microsoft.com/visualstudio/2016/10/05/announcing-visual-studio-15-preview-5/) (宣告 Visual Studio “15”)。 


## <a name="non-msbuild-projects-with-open-folder"></a>使用開啟資料夾的非 MSBuild 專案
Visual Studio 2017 引進「開啟資料夾」功能，可讓您在包含原始程式碼的資料夾中編寫程式碼、建置和偵錯，而不需要建立任何方案或專案。 如果您的專案不是 MSBuild 專案，則這可讓開始使用 Visual Studio 更為簡單。 運用「開啟資料夾」，即可存取 Visual Studio 已針對 MSBuild 專案所提供的強大程式碼了解、編輯、建置和偵錯功能。 如需詳細資訊，請參閱 [Visual C++ 中的「開啟資料夾」專案](ide/non-msbuild-projects.md)。

* [開啟資料夾] 體驗的改良。 您可以透過這些 JSON 檔案自訂體驗︰
  - CppProperties.json，用以自訂 IntelliSense 及瀏覽體驗。
  - Tasks.json，用以自訂建置步驟。 
  - Launch.json，用以自訂偵錯經驗。

**Visual Studio 2017 15.3 版**： 
* 已改善針對替代編譯器和建置環境 (例如 MinGW 和 Cygwin) 的支援。 如需詳細資訊，請參閱[搭配 Visual C++ 和「開啟資料夾」使用 MinGW 和 Cygwin](https://blogs.msdn.microsoft.com/vcblog/2017/07/19/using-mingw-and-cygwin-with-visual-cpp-and-open-folder/) \(英文\)。
* 已新增在 "CppProperties.json" 和 "CMakeSettings.json" 中定義全域和組態特定環境變數的支援。 這些環境變數可供 "launch.vs.json" 中定義的偵錯組態和 "tasks.vs.json" 中的工作取用。 如需詳細資訊，請參閱 [Customizing your Environment with Visual C++ and Open Folder](https://blogs.msdn.microsoft.com/vcblog/2017/11/02/customizing-your-environment-with-visual-c-and-open-folder/) (使用 Visual C++ 和開啟資料夾來自訂您的環境)。
* 已改善針對 CMake Ninja 產生器的支援，包括能夠輕鬆以 64 位元平台作為目標的能力。

## <a name="cmake-support-via-open-folder"></a>透過開啟資料夾的 CMake 支援
Visual Studio 2017 支援使用 CMake 專案，而不需要轉換為 MSBuild 專案檔 (.vcxproj)。 如需詳細資訊，請參閱 [Visual C++ 中的 CMake 專案](ide/cmake-tools-for-visual-cpp.md)。 使用「開啟資料夾」開啟 CMake 專案將會自動針對 C++ 編輯、建置和偵錯設定環境。

* 無須在根資料夾中建立 CppProperties.json 檔案，C++ IntelliSense 即可運作。 此外，我們新增了下拉式清單，可讓使用者輕易地切換 CMake 和 CppProperties.json 檔案所提供的設定。

* 透過與 CMakeLists.txt 檔案位於相同資料夾的 CMakeSettings.json 檔案，支援進一步設定。

  ![Cmake 開啟資料夾](media/cmake_cpp.png "CMake 開啟資料夾")

**Visual Studio 2017 15.3**：已新增針對 CMake Ninja 產生器的支援。 如需詳細資訊，請參閱 [Visual C++ 中的 CMake 專案](ide/cmake-tools-for-visual-cpp.md)。  

**Visual Studio 2017 15.5 版**：新增對匯入現有 CMake 快取的支援。 如需詳細資訊，請參閱 [Visual C++ 中的 CMake 專案](ide/cmake-tools-for-visual-cpp.md)。  

## <a name="windows-desktop-development-with-c"></a>使用 C++ 進行 Windows 桌面開發  
我們現在提供安裝原始 C++ 工作負載時更細微的安裝體驗。 我們已新增可選取的元件，讓您能夠只安裝所需的工具。  請注意，安裝程式 UI 中所列元件指出的安裝大小，並不準確且低估總大小。

若要在 C++ 桌面工作負載中成功建立 Win32 專案，您必須安裝工具組和 Windows SDK。 安裝建議 (選取) 的元件「VC++ 2017 v141 工具組 (x86、x64)」和 “Windows 10 SDK (10.0.14393)” 可確保這正常運作。 如果未安裝必要工具，將無法成功建立專案，而且精靈將會停止回應。

**Visual Studio 2017 15.5 版**：Visual C++ 建置工具 (先前以獨立產品形式提供) 現在會加入作為 Visual Studio 安裝程式中的工作負載。 此工作負載只會安裝建置 C++ 專案所需的工具，而不會安裝 Visual Studio IDE。 v140 和 v141 工具組都包含在內。 v141 工具組包含 Visual Studio 2015 15.5 版的最新改善。 如需詳細資訊，請參閱 [Visual Studio Build Tools now include the VS2017 and VS2015 MSVC Toolsets](https://blogs.msdn.microsoft.com/vcblog/2017/11/02/visual-studio-build-tools-now-include-the-vs2017-and-vs2015-msvc-toolsets/) (Visual Studio 建置工具現在包含 VS2017 和 VS2015 MSVC 工具組)。

## <a name="linux-development-with-c"></a>使用 C++ 的 Linux 程式開發  
熱門的 [Visual C++ for Linux Development](https://visualstudiogallery.msdn.microsoft.com/725025cf-7067-45c2-8d01-1e0fd359ae6e) 擴充功能現已納入 Visual Studio 中。 這個安裝提供您開發在 Linux 環境上執行的 C++ 應用程式，並進行偵錯所需的一切。  

**Visual Studio 2017 15.2 版**：改善跨平台程式碼共用和類型視覺效果。 如需詳細資訊，請參閱[針對跨平台程式碼共用和類型視覺效果的 Linux C++ 改善](https://blogs.msdn.microsoft.com/vcblog/2017/05/10/linux-cross-platform-and-type-visualization/) \(英文\)。

**Visual Studio 2017 15.5 版**：
1. Linux 工作負載已新增對 rsync 的支援作為 sftp 的替代方案，來將檔案同步處理至遠端 Linux 電腦。  
2. 新增以 ARM 為目標的交互編譯支援。 若要在安裝中啟用這項支援，請選擇 C++ 工作負載的 Linux 開發，並選取 Embedded 和 IoT 開發的選項。 這會將 ARM GCC 交互編譯工具和 Make 新增至您的安裝。 如需詳細資訊，請參閱 [ARM GCC Cross Compilation in Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2017/10/23/arm-gcc-cross-compilation-in-visual-studio/) (Visual Studio 中的 ARM GCC 交互編譯)。
3. 新增對 CMake 的支援。 您現在可以使用現有的 CMake 程式碼基底，而不必將它轉換成 Visual Studio 專案。 如需詳細資訊，請參閱[設定 Linux CMake 專案](linux/cmake-linux-project.md)。
4. 新增對執行遠端工作的支援。 這項功能可讓您在 Visual Studio 的 連線管理員中定義的遠端系統上執行任何命令。 遠端工作也會提供將檔案複製到遠端系統的功能。 


## <a name="game-development-with-c"></a>使用 C++ 的遊戲程式開發  
使用 C++ 的完整功能建置由 DirectX 或 Cocos2d 技術提供的專業遊戲。  

## <a name="mobile-development-with-c-android-and-ios"></a>使用 C++ 進行行動裝置應用程式開發 (Android 與 iOS)  
您現在能夠使用可以 Android 及 iOS 為目標的 Visual Studio 建立行動應用程式並對其偵錯。  

## <a name="universal-windows-apps"></a>通用 Windows App  
C++ 以通用 Windows app 工作負載的選用元件形式提供。  升級 C++ 專案目前必須以手動方式完成。 如果您在 Visual Studio 2017 中開啟以 v140 為目標的 UWP 專案且未安裝 Visual Studio 2015，則需要在專案屬性頁中選取 v141 平台工具組。

## <a name="new-options-for-c-on-universal-windows-platform-uwp"></a>通用 Windows 平台 (UWP) 上 C++ 的新選項
您現在有新的選項，可撰寫和封裝適用於通用 Windows 平台和 Windows 市集的 C++ 應用程式︰您可以使用 Desktop App Converter 來封裝現有傳統型應用程式，以透過 Windows 市集進行部署。 如需詳細資訊，請參閱 [Using Visual C++ Runtime in Centennial project](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project/) (在 Centennial 專案中使用 Visual C++ 執行階段) 和[使用傳統型橋接器將您的傳統型應用程式移轉至通用 Windows 平台 (UWP)](https://msdn.microsoft.com/en-us/windows/uwp/porting/desktop-to-uwp-root)。

**Visual Studio 2017 15.5 版**  
新增 **Windows 應用程式封裝專案**的專案範本，以支援使用傳統型橋接器來封裝傳統型應用程式。 該範本位於 [檔案] | [開新檔案] | [專案] | [已安裝] | [Visual C++] | [通用 Windows 平台] 中。

撰寫新的程式碼時，您現在可以使用 C++/WinRT，它是一種標準 C++ 語言推演，適用於僅在標頭檔中實作的 Windows 執行階段。 它可讓您使用任何符合標準規範的 C++ 編譯器來編寫和使用 Windows 執行階段 API。 C++/WinRT 設計成將現代 Windows API 的第一級存取提供給 C++ 開發人員。 如需詳細資訊，請參閱 [C++/WinRT Available on GitHub](https://moderncpp.com/) (GitHub 上可用的 C++/WinRT)。 

自 [Windows SDK Insider Preview 的組建 17025](https://blogs.windows.com/buildingapps/2017/11/01/windows-10-sdk-preview-build-17025/#ryPH3zAy6yk2cIRX.97) 起，C++/WinRT 會隨附於 Windows SDK。 如需詳細資訊，請參閱 [C++/WinRT is now included the Windows SDK](https://blogs.msdn.microsoft.com/vcblog/2017/11/01/cppwinrt-is-now-included-the-windows-sdk/) (C++/WinRT 現在隨附於 Windows SDK)。

## <a name="clangc2-platform-toolset"></a>Clang/C2 平台工具組
隨附於 [!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] 的 Clang/C2 工具組現在支援 /bigobj 參數，這對建置大型專案很重要。 它也包含數個重要的 Bug 修正，包括編譯器前端和後端。

## <a name="c-code-analysis"></a>C++ 程式碼分析

用於強制 [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines) 的 C++ Core Checkers 現已隨 Visual Studio 散發。 只要在專案的內容頁面的 [程式碼分析擴充功能] 對話方塊中啟用檢查工具，您執行程式碼分析時，擴充功能即包含在其中。 如需詳細資訊，請參閱[使用 C++ 核心指南檢查工具](/visualstudio/code-quality/using-the-cpp-core-guidelines-checkers)。

![CppCoreCheck](media/CppCoreCheck.png "CppCoreCheck 屬性頁面") 

**Visual Studio 2017 15.3 版**：已針對與資源管理相關的規則加入支援。 

**Visual Studio 2017 15.5 版**：新的 C++ Core Guidelines 檢查範圍涵蓋智慧型指標正確性、全域初始設定式是否正確使用，並標示 `goto` 等建構的使用和不正確的轉換。  
某些您可以在 15.3 中找到的警告編號，在 15.5 中已不再使用。 這些警告已取代為更明確的檢查。

## <a name="unit-testing"></a>單元測試

**Visual Studio 2017 15.5 版**：Google Test Adapter 和 Boost.Test Adapter 現在會作為 [使用 C++ 的桌面開發] 的元件，並與**測試總管**整合。 新增對 Cmake 專案的 CTest 支援 (使用 [開啟資料夾])，但尚未與**測試總管**完全整合。 如需詳細資訊，請參閱[撰寫 C/C++ 的單元測試](/visualstudio/test/writing-unit-tests-for-c-cpp)。

## <a name="visual-studio-graphics-diagnostics"></a>Visual Studio 圖形診斷

Visual Studio 圖形診斷是一組工具，用來記錄並分析 Direct3D 應用程式中的轉譯和效能問題。 圖形診斷功能可以與在 Windows 電腦、Windows 裝置模擬器或遠端電腦或裝置上本機執行的應用程式搭配使用。

* **頂點和幾何著色器的輸入和輸出：**檢視頂點和幾何著色器之輸入和輸出的能力已是其中一項最常被要求的功能，現在於工具中也予以支援。 只要在 [管線階段] 檢視中選取 VS 或 GS 階段，即可開始檢查其在下表中的輸入和輸出。

  ![著色器的輸入/輸出](media/io-shaders.png)

* **在物件表格中搜尋和篩選︰**提供快速且輕鬆的方式來尋找所尋找的資源。

  ![搜尋](media/search.png)
   
* **資源歷程記錄：**這個新檢視提供簡化的方式，來查看在轉譯所擷取畫面格期間使用之資源的整個修改歷程記錄。 若要叫用任何資源的歷程記錄，只需要按一下任何資源超連結旁邊的時鐘圖示。

  ![資源歷程記錄](media/resource-history.png)

  這將會顯示已填入資源變更歷程記錄的新資源歷程記錄工具視窗。

  ![資源歷程記錄變更](media/resource-history-change.png)

  請注意，如果啟用完整呼叫堆疊擷取來擷取您的畫面格 ([Visual Studio] | [工具] | [選項] | [圖形診斷])，則可以快速推論和檢查 Visual Studio 專案內之每個變更事件的內容。  

* **API 統計資料︰**檢視畫面格中 API 使用方式的高階摘要。 在探索根本不了解所進行的呼叫或太常進行的呼叫時，這十分有用。 透過 [Visual Studio 圖形分析器] 中的 [檢視] | [API 統計資料] 可以存取此視窗。

  ![API 統計資料](media/api-stats.png)

* **記憶體統計資料︰**檢視驅動程式針對您在畫面格中建立之資源所配置的記憶體數量。 透過 [Visual Studio 圖形分析器] 中的 [檢視] | [記憶體統計資料] 可以存取此視窗。 以滑鼠右鍵按一下並選擇 [全部複製]，即可將資料複製到 CSV 檔案，以在試算表中進行檢視。

  ![記憶體統計資料](media/memory-stats.png)
 
* **畫面格驗證：**新的錯誤和警告清單提供簡單的方法，以根據 Direct3D 偵錯層所偵測到的潛在問題來巡覽事件清單。 按一下 [Visual Studio 圖形分析器] 中的 [檢視] | [畫面格驗證]，開啟此視窗。 然後按一下 [執行驗證] 開始分析。 根據畫面格的複雜性而定，這可能需要幾分鐘的時間才能完成。

  ![畫面格驗證](media/frame-validation.png)
 
* **D3D12 的畫面格分析：**使用畫面格分析，以使用所指示的 “what-if” 實驗來分析繪製呼叫效能。 切換至 [畫面格分析] 索引標籤，然後執行分析以檢視報表。 如需詳細資訊，請觀看 [GoingNative 25: Visual Studio Graphics Frame Analysis](https://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool) (GoingNative 25：Visual Studio 圖形畫面格分析) 視訊。

  ![畫面格分析](media/frame-analysis.png)

* **GPU 使用量改善：**使用 GPU 檢視或 Windows Performance Analyzer (WPA) 工具開啟透過 Visual Studio GPU 使用量分析工具所採取的追蹤，以進行更詳細的分析。 如果您已安裝 Windows 效能工具組，則在工作階段概觀的右下方會有兩個超連結：一個用於 WPA，另一個則用於 GPU 檢視。

  ![GPU 使用量](media/gpu-usage.png)
 
  透過此連結在 GPU 檢視中開啟的追蹤，支援 VS 與 GPU 檢視間之時間軸中的同步縮放和移動瀏覽。 VS 中有一個核取方塊用來控制是否啟用同步處理。 

  ![GPU 檢視](media/gpu-view.png) 


