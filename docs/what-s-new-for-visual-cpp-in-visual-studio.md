---
title: "Visual Studio 中 Visual C++ 的新功能 | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: BrianPeek
ms.author: brpeek
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 71ae904790532cde7ffe559648ccd13a59b88051
ms.contentlocale: zh-tw
ms.lasthandoff: 04/01/2017

---

# <a name="whats-new-for-visual-c-in-includevsdev15mdmiscincludesvsdev15mdmd"></a>[!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] 中 Visual C++ 的新功能

[!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] 帶來 Visual C++ 環境的多個更新與修正。 我們修正了編譯器及工具中超過 250 個 Bug 與回報的問題，其中多為客戶透過 [Microsoft Connect](https://connect.microsoft.com/VisualStudio "Microsoft Connect") 所提交。 感謝您回報 Bug！  如需所有 Visual Studio 中之新功能的詳細資訊，請瀏覽 [[!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] 的新功能](https://go.microsoft.com/fwlink/?linkid=834481)。

<!--The compiler and tools version number in [!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] is 14.10.24629. -->


## <a name="c-compiler"></a>C++ 編譯器

### <a name="c-conformance-improvements"></a>C++ 一致性改善
我們在本版中更新了 C++ 編譯器和標準程式庫，加強對 C++11 和 C++14 功能的支援，以及對 C++17 標準某些預期功能的基本支援。 如需詳細資訊，請參閱 [Visual Studio 2017 中的 C++ 一致性改善](cpp-conformance-improvements-2017.md)。

### <a name="new-compiler-switches"></a>新的編譯器參數  

 -**/std:c++14** 和 **/std:c++latest**︰這些編譯器參數可讓您在專案中選擇加入特定版本的 ISO C++ 程式設計語言。 如需詳細資訊，請參閱 [Standards version switches in the compiler](https://blogs.msdn.microsoft.com/vcblog/2016/06/07/standards-version-switches-in-the-compiler) (編譯器中的標準版本參數)。 大部分的新草稿標準功能是由 /std:c++latest 參數所防護。 

-[/permissive-](build/reference/permissive-standards-conformance.md)︰啟用所有嚴格標準一致性編譯器選項，並停用大部分 Microsoft 特定編譯器延伸模組 (舉例來說，不是 __declspec(dllimport)) (預設為關閉，但在未來的某個時間點將會預設為開啟)。

-[/diagnostics](build/reference/diagnostics-compiler-diagnostic-options.md)︰啟用顯示行號、行號和資料行，或行號和資料行以及找到診斷錯誤或警告之程式碼下方的插入點。

-[/debug:fastlink](build/reference/debug-generate-debug-info.md)：  
啟用最多 30% 更快的累加連結時間 (與Visual Studio 2015)，方法是不要將所有偵錯資訊複製到 PDB 檔案。 PDB 檔案改為指向用來建立可執行檔之物件和程式庫檔案的偵錯資訊。 請參閱 [Faster C++ build cycle in VS “15” with /Debug:fastlink](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/faster-c-build-cycle-in-vs-15-with-debugfastlink/) (VS “15” 中使用 /Debug:fastlink 的較快 C++ 組建循環) 和 [Recommendations to speed C++ builds in Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2016/10/26/recommendations-to-speed-c-builds-in-visual-studio/) (Visual Studio 中加速 C++ 建置的建議)。

[!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] 允許搭配使用 /sdl 與 /await。 我們已移除協同程式的 /RTC 限制。 

### <a name="codegen-security-diagnostics-and-versioning"></a>Codegen、安全性、診斷和版本控制
此版本為最佳化、程式碼產生、工具組版本控制和診斷方面帶來多項改善。 其中幾項值得注意的改善內容包括：  

- 改善重複的程式碼產生：支援常數整數除法的自動向量化，更容易識別 memset 模式。
- 改善的程式碼安全性：改善發出緩衝區溢位編譯器診斷，而且 /guard:cf 現在會防護產生跳躍表的 switch 陳述式。
- 版本控制：現在，每次 Visual C++ 工具組更新時，都只會更新內建前置處理器巨集 _MSC_VER 的值。 如需詳細資訊，請參閱 [Visual C++ Compiler Version](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/visual-c-compiler-version/) (Visual C++ 編譯器版本)。
- 新的工具組版面配置︰編譯器和相關建置工具在開發電腦上具有新的位置和目錄結構。 新的版面配置可並存安裝多個版本的編譯器。 如需詳細資訊，請參閱 [Compiler Tools Layout in Visual Studio "15"](https://blogs.msdn.microsoft.com/vcblog/2016/10/07/compiler-tools-layout-in-visual-studio-15/) (Visual Studio "15" 中的編譯器工具版面配置)。
- 改善的診斷：輸出視窗現在會顯示發生錯誤的資料行。 如需詳細資訊，請參閱 [C++ compiler diagnostics improvements in VS "15" Preview 5](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/c-compiler-diagnostics-improvements-in-vs-15-rc/) (VS "15" Preview 5 中的 C++ 編譯器診斷改善)。
- 使用共同常式時，已移除實驗關鍵字 "yield" (在 /await 參數下)。 您應該更新程式碼以改用 "co_yield"。 如需詳細資訊，請參閱 Visual C++ 小組部落格。 

## <a name="c-libraries"></a>C++ 程式庫

### <a name="standard-library-improvements"></a>標準程式庫改善：

* 次要 basic_string _ITERATOR_DEBUG_LEVEL != 0 診斷改良功能。 字串機制中的 IDL 檢查若出錯，現在將會回報導致該錯誤的特定行為。 例如，您會看見「無法為字串迭代器取值，因為它超出範圍 (例如結尾迭代器)」，而不是「無法為字串迭代器取值」。
* 效能改進︰讓 basic_string::find(char) 多載只呼叫 traits::find 一次。 先前已為長度為 1 的字串將其作為一般字串搜尋實作。
* 效能改進︰basic_string::operator== 現在會先檢查字串的大小，再比較字串的內容。
* 效能改進︰已移除 basic_string 中的控制項結合程度，編譯器最佳化工具很難加以分析。 解決 VSO # 262848「<string>: reserve() 做太多的工作」。 請注意，對於所有的短字串，呼叫保留仍有非零的正整數成本，且不會執行任何動作。
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
* 如需完整的 STL 改善清單，請參閱 [STL Fixes In VS 2017 RTM](https://blogs.msdn.microsoft.com/vcblog/2017/02/06/stl-fixes-in-vs-2017-rtm/) (VS 2017 RTM 中的 STL 修正)。

### <a name="open-source-library-support"></a>開放原始碼程式庫支援  
Vcpkg 是一種開放原始碼命令列工具，可大幅簡化在 Visual Studio 中取得和建置開放原始碼 C++ 靜態程式庫和 DLL 的程序。 如需詳細資訊，請參閱 [Vcpkg updates: Static linking is now available](https://blogs.msdn.microsoft.com/vcblog/2016/11/01/vcpkg-updates-static-linking-is-now-available/) (Vcpkg 更新︰現在已提供靜態連結)。

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

### <a name="intellisense"></a>Intellisense  
* 現在預設使用新的 SQLite 型資料庫引擎。 這會加速資料庫作業，如「移至定義」和「尋找所有參考」，也會大幅改善初始解決方案剖析階段。 設定已移至 [工具] > [選項] > [文字編輯器] > [C/C++] > [進階]\(原位於 [C/C++] > [實驗] 下)。

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

* 啟用了 C++ 專案「讓專案更快載入」的新實驗性功能。 C++ 專案會在您下次開啟時更快載入，之後即以極快速度載入！

其中有部分功能通用於其他語言，部分功能則是 C++ 的特定功能。 如需這些新功能的詳細資訊，請參閱 [Announcing Visual Studio “15”](https://blogs.msdn.microsoft.com/visualstudio/2016/10/05/announcing-visual-studio-15-preview-5/) (宣告 Visual Studio “15”)。 

### <a name="support-for-non-msbuild-projects-with-open-folder"></a>使用開啟資料夾的非 MSBuild 專案支援
Visual Studio 2017 引進「開啟資料夾」功能，可讓您在包含原始程式碼的資料夾中編寫程式碼、建置和偵錯，而不需要建立任何方案或專案。 如果您的專案不是 MSBuild 專案，則這可讓開始使用 Visual Studio 更為簡單。 運用「開啟資料夾」，即可存取 Visual Studio 已針對 MSBuild 專案所提供的強大程式碼了解、編輯、建置和偵錯功能。 如需詳細資訊，請參閱 [Bring your C++ codebase to Visual Studio with “Open Folder”](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/bring-your-c-codebase-to-visual-studio-with-open-folder/) (使用「開啟資料夾」將您的 C++ 程式碼基底移轉至 Visual Studio)。

* [開啟資料夾] 體驗的改良。 您可以透過這些 JSON 檔案自訂體驗︰
  -    CppProperties.json，用以自訂 IntelliSense 及瀏覽體驗。
  -    Tasks.json，用以自訂建置步驟。 
  -    Launch.json，用以自訂偵錯經驗。

### <a name="cmake-support-via-open-folder"></a>透過開啟資料夾的 CMake 支援
Visual Studio 2017 支援使用 CMake 專案，而不需要轉換為 MSBuild 專案檔 (.vcxproj)。 如需詳細資訊，請參閱 [CMake support in Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/cmake-support-in-visual-studio/) (Visual Studio 中的 CMake 支援) 和 [CMake support in Visual Studio 2017 - what’s new in the RC.2 update](https://blogs.msdn.microsoft.com/vcblog/2016/12/20/cmake-support-in-visual-studio-2017-whats-new-in-the-rc-update/) (Visual Studio 2017 中的 CMake 支援 - RC.2 更新的新功能)。 使用「開啟資料夾」開啟 CMake 專案將會自動針對 C++ 編輯、建置和偵錯設定環境。

* 無須在根資料夾中建立 CppProperties.json 檔案，C++ IntelliSense 即可運作。 此外，我們新增了下拉式清單，可讓使用者輕易地切換 CMake 和 CppProperties.json 檔案所提供的設定。

* 透過與 CMakeLists.txt 檔案位於相同資料夾的 CMakeSettings.json 檔案，支援進一步設定。

  ![Cmake 開啟資料夾](media/cmake_cpp.png "CMake 開啟資料夾")


## <a name="c-installation-workloads"></a>C++ 安裝工作負載 

### <a name="windows-desktop-development-with-c"></a>使用 C++ 進行 Windows 桌面開發：  
我們現在提供安裝原始 C++ 工作負載時更細微的安裝體驗。 我們已新增可選取的元件，讓您能夠只安裝所需的工具。  請注意，安裝程式 UI 中所列元件指出的安裝大小，並不準確且低估總大小。

若要在 C++ 桌面工作負載中成功建立 Win32 專案，您必須安裝工具組和 Windows SDK。 安裝建議 (選取) 的元件「VC++ 2017 v141 工具組 (x86、x64)」和 “Windows 10 SDK (10.0.14393)” 可確保這正常運作。 如果未安裝必要工具，將無法成功建立專案，而且精靈將會停止回應。

### <a name="linux-development-with-c"></a>使用 C++ 進行 Linux 開發：  
熱門的 [Visual C++ for Linux Development](https://visualstudiogallery.msdn.microsoft.com/725025cf-7067-45c2-8d01-1e0fd359ae6e) 擴充功能現已納入 Visual Studio 中。 這個安裝提供您開發在 Linux 環境上執行的 C++ 應用程式，並進行偵錯所需的一切。  

### <a name="game-development-with-c"></a>使用 C++ 進行遊戲開發：  
使用 C++ 的完整功能建置由 DirectX 或 Cocos2d 技術提供的專業遊戲。  

### <a name="mobile-development-with-c-android-and-ios"></a>使用 C++ 進行行動裝置開發 (Android 與 iOS)：  
您現在能夠使用可以 Android 及 iOS 為目標的 Visual Studio 建立行動應用程式並對其偵錯。  

### <a name="universal-windows-apps"></a>通用 Windows 應用程式：  
C++ 以通用 Windows app 工作負載的選用元件形式提供。  升級 C++ 專案目前必須以手動方式完成。 如果您在 Visual Studio 2017 中開啟以 v140 為目標的 UWP 專案且未安裝 Visual Studio 2015，則需要在專案屬性頁中選取 v141 平台工具組。

## <a name="new-options-for-c-on-universal-windows-platform"></a>通用 Windows 平台上 C++ 的新選項
您現在有新的選項，可撰寫和封裝適用於通用 Windows 平台和 Windows 市集的 C++ 應用程式︰您可以使用 Desktop App Converter 來封裝現有傳統型應用程式，以透過 Windows 市集進行部署。 如需詳細資訊，請參閱 [Using Visual C++ Runtime in Centennial project](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project/) (在 Centennial 專案中使用 Visual C++ 執行階段) 和[使用傳統型橋接器將您的傳統型應用程式移轉至通用 Windows 平台 (UWP)](https://msdn.microsoft.com/en-us/windows/uwp/porting/desktop-to-uwp-root)。

撰寫新的程式碼時，您現在可以使用 C++/WinRT，它是一種標準 C++ 語言推演，適用於僅在標頭檔中實作的 Windows 執行階段。 它可讓您使用任何符合標準規範的 C++ 編譯器來編寫和使用 Windows 執行階段 API。 C++/WinRT 設計成將現代 Windows API 的第一級存取提供給 C++ 開發人員。 如需詳細資訊，請參閱 [C++/WinRT Available on GitHub](https://moderncpp.com/) (GitHub 上可用的 C++/WinRT)。


## <a name="clangc2-platform-toolset"></a>Clang/C2 平台工具組
隨附於 [!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] 的 Clang/C2 工具組現在支援 /bigobj 參數，這對建置大型專案很重要。 它也包含數個重要的 Bug 修正，包括編譯器前端和後端。

## <a name="c-code-analysis"></a>C++ 程式碼分析

用於強制 [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines) 的 C++ Core Checkers 現已隨 Visual Studio 散發。 只要在專案的內容頁面的 [程式碼分析擴充功能] 對話方塊中啟用檢查工具，您執行程式碼分析時，擴充功能即包含在其中。 

![CppCoreCheck](media/CppCoreCheck.png "CppCoreCheck 屬性頁面") 

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

  請注意，如果啟用完整呼叫堆疊擷取來擷取您的畫面格 ([Visual Studio] > [工具] > [選項] > [圖形診斷])，則可以快速推論和檢查 Visual Studio 專案內的每個變更事件的內容。  

* **API 統計資料︰**檢視畫面格中 API 使用方式的高階摘要。 在探索根本不了解所進行的呼叫或太常進行的呼叫時，這十分有用。 透過 [Visual Studio 圖形分析器] 中的 [檢視] > [API 統計資料] 可以存取此視窗。

  ![API 統計資料](media/api-stats.png)

* **記憶體統計資料︰**檢視驅動程式針對您在畫面格中建立之資源所配置的記憶體數量。 透過 [Visual Studio 圖形分析器] 中的 [檢視] > [記憶體統計資料] 可以存取此視窗。 以滑鼠右鍵按一下並選擇 [全部複製]，即可將資料複製到 CSV 檔案，以在試算表中進行檢視。

  ![記憶體統計資料](media/memory-stats.png)
 
* **畫面格驗證：**新的錯誤和警告清單提供簡單的方法，以根據 Direct3D 偵錯層所偵測到的潛在問題來巡覽事件清單。 按一下 [Visual Studio 圖形分析器] 中的 [檢視] -> [畫面格驗證]，開啟此視窗。 然後按一下 [執行驗證] 開始分析。 根據畫面格的複雜性而定，這可能需要幾分鐘的時間才能完成。

  ![畫面格驗證](media/frame-validation.png)
 
* **D3D12 的畫面格分析：**使用畫面格分析，以使用所指示的 “what-if” 實驗來分析繪製呼叫效能。 切換至 [畫面格分析] 索引標籤，然後執行分析以檢視報表。 如需詳細資訊，請觀看 [GoingNative 25: Visual Studio Graphics Frame Analysis](https://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool) (GoingNative 25：Visual Studio 圖形畫面格分析) 視訊。

  ![畫面格分析](media/frame-analysis.png)

* **GPU 使用量改善：**使用 GPU 檢視或 Windows Performance Analyzer (WPA) 工具開啟透過 Visual Studio GPU 使用量分析工具所採取的追蹤，以進行更詳細的分析。 如果您已安裝 Windows 效能工具組，則在工作階段概觀的右下方會有兩個超連結：一個用於 WPA，另一個則用於 GPU 檢視。

  ![GPU 使用量](media/gpu-usage.png)
 
  透過此連結在 GPU 檢視中開啟的追蹤，支援 VS 與 GPU 檢視間之時間軸中的同步縮放和移動瀏覽。 VS 中有一個核取方塊用來控制是否啟用同步處理。 

  ![GPU 檢視](media/gpu-view.png) 


 

