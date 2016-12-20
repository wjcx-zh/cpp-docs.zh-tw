---
title: "C++11/14/17 功能的支援 (現代 C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: dd2d5cbc-caf5-4a11-a057-8c365decba4e
caps.latest.revision: 59
caps.handback.revision: 56
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C++11/14/17 功能的支援 (現代 C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明 Visual C\+\+ 中的 C\+\+11\/14\/17 功能。  
  
##  <a name="top"></a> 本文內容  
  
-   [C++11 功能清單](#featurelist)  
  
    -   [C++11 核心語言功能表](#corelanguagetable)  
  
    -   [C++11 核心語言功能表：並行](#concurrencytable)  
  
    -   [C++11 核心語言功能：C99](#c99table)  
  
-   [C++14 核心語言功能](#cpp14table)  
  
-   [C++17 提議核心語言功能](#cpp17table)  
  
-   [功能表指南](#tableguide)  
  
    -   [右值參考](#rvref)  
  
    -   [Lambda](#lambdas)  
  
    -   [decltype](#decltype)  
  
    -   [強類型/向前宣告列舉](#stronglytyped)  
  
    -   [對齊](#alignment)  
  
    -   [標準配置和 Trivial 類型](#standardlayout)  
  
    -   [預設和已刪除的函式](#defaultedanddeleted)  
  
    -   [override 和 final](#overrideandfinal)  
  
    -   [Atomics 和其他](#atomics)  
  
    -   [C99 __func__ 及前置處理器規則](#c99)  
  
-   [標準程式庫功能](#stl)  
  
##  <a name="featurelist"></a> C\+\+11 功能清單  
 Visual C\+\+ 可實作 [C\+\+11 核心語言規格](http://go.microsoft.com/fwlink/p/?LinkID=235092)中絕大多數的功能，以及許多 C\+\+14 程式庫功能和部分 C\+\+17 提議功能。 下表列出在 Visual Studio 2010、[!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] 和 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 及 Visual Studio 2015 中，C\+\+11\/14\/17 核心語言功能及其實作情形。  
  
###  <a name="corelanguagetable"></a> C\+\+11 核心語言功能表  
  
|[C\+\+11 核心語言功能](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2009/n2869.html)|Visual Studio 2010|Visual Studio 2012|[!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)]|Visual Studio 2015|  
|------------------------------------------------------------------------------------------|------------------------|------------------------|--------------------------------------------------------------|------------------------|  
|右值參考 [v0.1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2004/n1610.html)、[v1.0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2006/n2118.html)、[v2.0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2009/n2844.html)、[v2.1](http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_defects.html)、[v3.0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2010/n3053.html)|v2.0|v2.1\*|v2.1\*|v3.0|  
|[ref 限定詞](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2439.htm)|否|否|否|是|  
|[非靜態資料成員初始設定式](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2756.htm)|否|否|[是](../cpp/uniform-initialization-and-delegating-constructors.md)|是|  
|Variadic 範本 [v0.9](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2242.pdf)、[v1.0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2555.pdf)|否|否|[是](../cpp/ellipses-and-variadic-templates.md)|是|  
|[初始設定式清單](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2672.htm)|否|否|[是](../cpp/uniform-initialization-and-delegating-constructors.md)|是|  
|[static\_assert](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2004/n1720.html)|是|是|是|是|  
|auto [v0.9](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2006/n1984.pdf)、[v1.0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2546.htm)|v1.0|v1.0|v1.0|是|  
|[尾端傳回類型](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2541.htm)|是|是|是|是|  
|Lambda [v0.9](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2550.pdf)、[v1.0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2658.pdf)、[v1.1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2009/n2927.pdf)|v1.0|v1.1|v1.1|是|  
|decltype [v1.0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2343.pdf)、[v1.1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2011/n3276.pdf)|v1.0|v1.1\*\*|v1.1|是|  
|[右角括弧](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2005/n1757.html)|是|是|是|是|  
|[函式範本的預設範本引數](http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_defects.html)|否|否|是|是|  
|[運算式 SFINAE](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2634.html)|否|否|否|否|  
|[別名範本](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2258.pdf)|否|否|[是](../cpp/aliases-and-typedefs-cpp.md)|是|  
|[Extern 範本](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2006/n1987.htm)|是|是|是|是|  
|[nullptr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2431.pdf)|是|是|是|是|  
|[強類型列舉](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2347.pdf)|Partial|是|是|是|  
|[向前宣告列舉](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2764.pdf)|否|是|是|是|  
|[屬性](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2761.pdf)|否|否|否|是|  
|[constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2235.pdf)|否|否|否|是|  
|[對齊](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2341.pdf)|TR1|Partial|Partial|是|  
|[委派建構函式](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2006/n1986.pdf)|否|否|[是](../cpp/uniform-initialization-and-delegating-constructors.md)|是|  
|[繼承建構函式](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2540.htm)|否|否|否|是|  
|[明確轉換運算子](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2437.pdf)|否|否|是|是|  
|[char16\_t\/char32\_t](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2249.html)|否|否|否|是|  
|[Unicode 字串常值](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2442.htm)|否|否|否|是|  
|[原始字串常值](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2442.htm)|否|否|[是](../cpp/string-and-character-literals-cpp.md)|是|  
|[常值中的通用字元名稱](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2170.html)|否|否|否|是|  
|[使用者定義常值](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2765.pdf)|否|否|否|是|  
|[標準配置和 Trivial 類型](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2342.htm)|否|是|是|是|  
|[預設和已刪除的函式](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2346.htm)|否|否|[是\*](../cpp/explicitly-defaulted-and-deleted-functions.md)|是|  
|[擴充 friend 宣告](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2005/n1791.pdf)|是|是|是|是|  
|[擴充 sizeof](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2253.html)|否|否|否|是|  
|[內嵌命名空間](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2535.htm)|否|否|否|是|  
|[無限制的等位](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2544.pdf)|否|否|否|是|  
|[當做範本引數的區域和未命名類型](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2657.htm)|是|是|是|是|  
|[範圍架構的 for 迴圈](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2009/n2930.html)|否|是|是|是|  
|override 和 final [v0.8](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2009/n2928.htm)、[v0.9](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2010/n3206.htm)、[v1.0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2011/n3272.htm)|Partial|是|是|是|  
|[最小的 GC 支援](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2670.htm)|是|是|是|是|  
|[noexcept](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2010/n3050.html)|否|否|否|是|  
  
 \[[本文內容](#top)\]  
  
###  <a name="concurrencytable"></a> C\+\+11 核心語言功能表：並行  
  
|C\+\+11 核心語言功能：並行|Visual Studio 2010|Visual Studio 2012|[!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)]|Visual Studio 2015|  
|-----------------------|------------------------|------------------------|--------------------------------------------------------------|------------------------|  
|[改寫的序列點](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2239.html)|N\/A|N\/A|N\/A|是|  
|[Atomics](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2427.html)|否|是|是|是|  
|[強式比較和交換](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2748.html)|否|是|是|是|  
|[雙向柵欄](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2752.htm)|否|是|是|是|  
|[記憶體模型](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2429.htm)|N\/A|N\/A|N\/A|是|  
|[資料相依性順序](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2664.htm)|否|是|是|是|  
|[資料相依性順序：函式註釋](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2782.htm)|否|否|否|是|  
|[exception\_ptr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2179.html)|是|是|是|是|  
|[quick\_exit](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2440.htm)|否|否|否|是|  
|[訊號處理常式中的 Atomics](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2547.htm)|否|否|否|否|  
|[執行緒區域儲存區](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2659.htm)|Partial|Partial|Partial|是|  
|[Magic 靜態變數](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2660.htm)|否|否|否|是|  
  
 \[[本文內容](#top)\]  
  
###  <a name="c99table"></a> C\+\+11 核心語言功能：C99  
  
|C\+\+11 核心語言功能：C99|Visual Studio 2010|Visual Studio 2012|[!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)]|Visual Studio 2015|  
|------------------------|------------------------|------------------------|--------------------------------------------------------------|------------------------|  
|[\_\_func\_\_](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2340.htm)|Partial|Partial|Partial|是|  
|[C99 前置處理器](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2004/n1653.htm)|Partial|Partial|Partial|Partial|  
|[long long](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2005/n1811.pdf)|是|是|是|是|  
|[擴充整數類型](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2006/n1988.pdf)|N\/A|N\/A|N\/A|N\/A|  
  
 \[[本文內容](#top)\]  
  
###  <a name="cpp14table"></a> C\+\+14 核心語言功能  
  
||||  
|-|-|-|  
|功能|Visual Studio 2013|Visual Studio 2015|  
|改良的內容轉換 workding|是|是|  
|二進位常值|否|是|  
|auto 和 decltype\(auto\) 傳回類型|否|是|  
|init 擷取|否|是|  
|泛型 lambda|否|是|  
|變數範本|否|否|  
|擴充的 constexpr|否|否|  
|彙總的 NSDMI|否|否|  
|避免\/融合配置|否|否|  
|\[\[deprecated\]\] 屬性|否|否|  
|依大小調整的配置|否|是|  
|數字分隔符號|否|是|  
  
###  <a name="cpp17table"></a> C\+\+17 提議核心語言功能  
  
||||  
|-|-|-|  
|功能|Visual Studio 2013|Visual Studio 2015|  
|新的自動化規則，附有以大括號括住的初始清單|否|否|  
|簡易靜態判斷提示|否|否|  
|範本參數中的類型名稱|否|否|  
|移除三併詞|是|是|  
|巢狀命名空間定義|否|否|  
|N4259 std::uncaught\_exceptions\(\)|否|否|  
|N4261 修正限定性條件轉換|否|否|  
|命名空間和列舉程式的 N4266 屬性|否|否|  
|N4267 u8 字元常值|否|否|  
|N4268 允許多個非類型範本引數|否|否|  
|N4295 摺疊運算式|否|否|  
|等候\/繼續|否|是|  
  
##  <a name="tableguide"></a> 功能表指南  
  
###  <a name="rvref"></a> 右值參考  
  
> [!NOTE]
>  下列描述中的版本編號 \(v0.1、v1.0、v2.0、v2.1、v3.0\) 是用來表示 C\+\+11 的發展程度。 標準本身不使用這些編號。  
  
 [N1610「說明透過右值的類別物件初始化」](http://go.microsoft.com/fwlink/p/?LinkID=235093)是早期不使用右值參考啟用移動語意的嘗試。  在這個討論中，我們將其稱為「右值參考 v0.1」。 之後被「右值參考 [v1.0](http://go.microsoft.com/fwlink/p/?LinkID=235094)」取代。 「右值參考 [v2.0](http://go.microsoft.com/fwlink/p/?LinkID=235095)」是 Visual C\+\+ 在 Visual Studio 2010 中的工作基礎，藉由禁止右值參考繫結至左值的方式，修正主要安全問題。  「右值參考 [v2.1](http://go.microsoft.com/fwlink/p/?LinkID=235096)」則修改了這個規則。  假設 `vector<string>::push_back()` 中具有 `push_back(const string&)` 和 `push_back(string&&)` 多載，以及 `v.push_back("strval")` 呼叫。`"strval"` 運算式是字串常值，而且是左值。  \(整數 1729 等其他常值是右值，但字串常值是特殊的，因為它們是陣列\)。  「右值參考 v2.0」規則規定，`string&&` 無法繫結到 `"strval"`，因為 `"strval"` 是左值，因此 `push_back(const string&)` 是唯一可行的多載。  這會建立暫存 `std::string`，將其複製到向量，然後終結暫存 `std::string`，但不是很有效率。 「右值參考 v2.1」規則認為，`string&&` 繫結至 `"strval"` 會建立暫存的 `std::string`，而且暫存的是右值。  因此，`push_back(const string&)` 和 `push_back(string&&)` 是可行的，而以 `push_back(string&&)` 較為慣用。  會建構暫存 `std::string`，然後將其移至向量。  這會更有效率。  
  
 「右值參考 [v3.0](http://go.microsoft.com/fwlink/p/?LinkID=235097)」加入新規則，會在特定情況下自動產生移動建構函式和移動指派運算子。 這是在 Visual Studio 2015 中進行實作。  
  
 \[[本文內容](#top)\]  
  
###  <a name="lambdas"></a> Lambda  
 在 [lambda 函式](../cpp/lambda-expressions-in-cpp.md)經表決通過納入工作文件 \([版本 "0.9"](http://go.microsoft.com/fwlink/p/?LinkID=235098)\)，並加入可變動 Lambda \([版本 "1.0"](http://go.microsoft.com/fwlink/p/?LinkID=235099)\) 之後，標準化委員會翻修了用字方式。 如此產生了現在完全支援的 Lambda [版本 "1.1"](http://go.microsoft.com/fwlink/p/?LinkID=235100)。  Lambda v1.1 的用字方式可釐清在參考靜態成員或巢狀 Lambda 等隱密案例下應該會發生什麼情況。  這會修正由複雜 Lambda 所觸發的問題。  此外，無狀態 Lambda 現在可轉換為函式指標。  這使用的不是 N2927 用語，但還是視為 Lambda v1.1 的一部分。[C\+\+11](http://go.microsoft.com/fwlink/p/?LinkID=235092)**5.1.2 \[expr.prim.lambda\]\/6** 有這樣的描述：「沒有 `lambda-capture` 之 `lambda-expression` 的結束類型，具有函式至函式指標的公用、非虛擬、非明確的常數轉換函式，而函式指標的參數和傳回類型與結束類型的函式呼叫運算子相同。 這個轉換函式傳回的值將會是函式的位址，叫用該函式與叫用結束類型的函式呼叫運算子有相同的效果」。  \([!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] 實作甚至更好，因為這會讓無狀態 Lambda 得以轉換為有任意呼叫慣例的函式指標。  當您使用需要 `__stdcall` 函式指標的 API 時，這點很重要\)。  
  
 \[[本文內容](#top)\]  
  
###  <a name="decltype"></a> decltype  
 decltype 經表決通過，放入工作文件 \([版本 1.0](http://go.microsoft.com/fwlink/p/?LinkID=235101)\) 之後，它在最後時刻獲得小型但重要的修正 \([版本 1.1](http://go.microsoft.com/fwlink/p/?LinkID=235102)\)。  這對使用 STL 和 Boost 的程式設計人員而言，關係重大。  
  
 \[[本文內容](#top)\]  
  
###  <a name="stronglytyped"></a> 強類型\/向前宣告列舉  
 Visual Studio 2010 中的 Visual C\+\+ 部分支援[強類型列舉](http://go.microsoft.com/fwlink/p/?LinkID=235103) \(特別是有關明確指定的基礎類型部分\)。 這些現在已在 Visual Studio 中完整實作，而且[向前宣告列舉](http://go.microsoft.com/fwlink/p/?LinkID=235104) C\+\+11 語意也完整實作。  
  
 \[[本文內容](#top)\]  
  
###  <a name="alignment"></a> 對齊  
 在 Visual Studio 2015 中實作已表決納入工作文件的[對齊提議](http://go.microsoft.com/fwlink/p/?LinkID=235105)中的核心語言關鍵字`alignas`\/`alignof`。  Visual Studio 2010 中的 Visual C\+\+ 具有 TR1 的 `aligned_storage`。[!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] 已將 `aligned_union` 和 `std::align()` 加入標準程式庫，且重大議題已在 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 中修正。  
  
 \[[本文內容](#top)\]  
  
###  <a name="standardlayout"></a> 標準配置和 Trivial 類型  
 [N2342「POD 重新造訪：解決核心問題 568 \(修訂 5\)」](http://go.microsoft.com/fwlink/p/?LinkID=235106) 中的建議變更是將 `is_trivial` 和 `is_standard_layout` 加入至標準範本資料庫的 `<type_traits>`。  \(N2342 調整了大量的核心語言文字，不過，編譯器變更不是必要的\)。  這些類型特性在 Visual Studio 2010 的 Visual C\+\+ 中有提供，但它們只是重複的 `is_pod`。 因此，文件前面的表格會說「否」表示不支援。  現在這些特徵是由專為提供精確回應而設計的編譯器攔截所支援。  
  
 STL 的 [common\_type\<\>](../standard-library/common-type-class.md) 會在 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 中收到必要的修正。`common_type<>` 的 C\+\+11 規格會產生未預期和不想要的結果，尤其是使 `common_type<int, int>::type` 傳回 `int&&`。 因此，[!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 實作了[程式庫工作小組問題 2141 的建議解決方法](http://go.microsoft.com/fwlink/p/?LinkId=320075)，也就是使 `common_type<int, int>::type` 傳回 `int`。  
  
 這項變更的副作用就是識別案例不再適用 \(`common_type<T>` 不一定會產生 `T` 類型\)。 這個結果符合建議的解決方法，不過它會破壞依賴之前行為的任何程式碼。  
  
 如果您需要識別類型特性，請不要使用 `std::identity` 中定義的非標準 `<type_traits>`，因為它不適用 `<void>`。 請改為依照您的需求，實作自己的識別類型特性。 以下為範例：  
  
```cpp  
template <typename T> struct Identity { typedef T type; };  
  
```  
  
> [!NOTE]
>  如需其他重大變更，請參閱 [Visual C\+\+ 2015 的重大變更](../porting/visual-cpp-change-history-2003-20151.md)。  
  
 \[[本文內容](#top)\]  
  
###  <a name="defaultedanddeleted"></a> 預設和已刪除的函式  
 現在可支援這些函式，除了這個例外狀況：對於預設的函式，不支援使用 `=default` 要求成員移動建構函式和移動指派運算子。 複製和移動無法像標準所規定的那樣精準互動。例如，刪除移動時也會指定要隱藏複製，但 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 則不會如此。  
  
 如需關於使用預設和刪除之函式方式的詳細資訊，請參閱 [函式](../cpp/functions-cpp.md)。  
  
 \[[本文內容](#top)\]  
  
###  <a name="overrideandfinal"></a> override 和 final  
 經歷了短暫但複雜的演變。 原先在 [0.8 版](http://go.microsoft.com/fwlink/p/?LinkID=235108)中，有 \[\[`override`\]\]、\[\[`hiding`\]\] 和 \[\[`base_check`\]\] 屬性。  接著在 [0.9 版](http://go.microsoft.com/fwlink/p/?LinkID=235109)，這些屬性已消失，由內容關鍵字取而代之。  最後，在 [1.0 版](http://go.microsoft.com/fwlink/p/?LinkID=235110)中，它們則降至類別的「`final`」，以及函式的「`override`」和「`final`」。  這使得此版本成為「加強擴充」，因為 Visual Studio 2010 中的 Visual C\+\+ 已經在函式中支援這個 "`override`" 語法，而且其語意相當接近 C\+\+11 的語意。  也支援 "`final` "，不過是在其他拼字 "sealed" 之下。  現在可完全支援「`override`」和「`final`」的標準拼字及語意。 如需詳細資訊，請參閱 [override 規範](../cpp/override-specifier.md) 與 [final 規範](../cpp/final-specifier.md)。  
  
 \[[本文內容](#top)\]  
  
###  <a name="atomics"></a> Atomics 和其他  
 [Atomics](http://go.microsoft.com/fwlink/p/?LinkID=235111)、[強式比較和交換](http://go.microsoft.com/fwlink/p/?LinkID=235112)、[雙向柵欄](http://go.microsoft.com/fwlink/p/?LinkID=235113)和[資料相依性順序](http://go.microsoft.com/fwlink/p/?LinkID=235114)會指定目前已實作的標準程式庫機制。  
  
 **相關 STL 標頭：** [\<atomic\>](../standard-library/atomic.md)、[\<chrono\>](../standard-library/chrono.md)、[\<condition\_variable\>](../standard-library/condition-variable.md)、[\<future\>](../standard-library/future.md)、[\<mutex\>](../standard-library/mutex.md)、[\<ratio\>](../standard-library/ratio.md)、[\<scoped\_allocator\>](../standard-library/scoped-allocator.md) 及 [\<thread\>](../standard-library/thread.md)。  
  
 \[[本文內容](#top)\]  
  
###  <a name="c99"></a> C99 \_\_func\_\_ 及前置處理器規則  
 表格 [C++11 核心語言功能：C99](#c99table) 會列出兩個項目的「部分」實作。 對於預先定義的識別項 `__func__`，會列出「部分」，因為支援會提供給非標準擴充功能 `__FUNCDNAME__`、`__FUNCSIG__` 及 `__FUNCTION__`。 如需詳細資訊，請參閱[預先定義的巨集](../preprocessor/predefined-macros.md)。 對於 C99 前置處理器規則，會列出「部分」，因為支援 *variadic 巨集*。 如需詳細資訊，請參閱[Variadic 巨集](../preprocessor/variadic-macros.md)。  
  
 \[[本文內容](#top)\]  
  
###  <a name="stl"></a> 標準程式庫功能  
 可涵蓋核心語言。 對於 C\+\+11 標準程式庫，我們沒有正式的功能比較表，但是 [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] 會加以實作，其中有兩個例外狀況。  首先，當程式庫功能取決於編譯器中遺漏的功能時，表示程式庫功能為模擬 \(例如，`make_shared<T>()` 的模擬 variadic 範本\) 或並未實作。 \(已在 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 完全實作的案例只有少數幾個，尤其是 `<initializer_list>`\)。  C99 已經在 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 中實作，而且也提供 C\+\+ 包裝函式標頭，其中有極少數的例外狀況。 如需詳細資訊，請參閱 [Visual Studio 2013 中的 C99 程式庫支援](http://go.microsoft.com/fwlink/p/?LinkId=321308)。  
  
 [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] 和 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 中的部分變更清單如下：  
  
 **定位：**根據 C\+\+11 規定，在「任意」引數數目的所有容器中實作 `emplace()`\/`emplace_front()`\/`emplace_back()`\/`emplace_hint()`\/`emplace_after()` \(請參閱＜Simulated variadics＞一節\)。  例如，`vector<T>` 具有 "`template <typename... Args> void emplace_back(Args&&... args)`"，這會直接在向量後面從任意數目的任意引數完全向前建構類型 T 的項目。  這比 `push_back(T&&)` 更有效率，後者需要額外移動建構和解構。  
  
 **Variadics**：[!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] 有模擬 variadic 範本的配置。 在 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 中，模擬已消失，並**完整實作 variadic**。 如果程式碼依賴舊版模擬的 variadic 行為，您必須進行修正。 不過，改用實際的 variadic 樣板後**已縮短編譯時間**並且**減少編譯器記憶體使用量**。  
  
 **明確轉換運算子**：在核心語言中，明確轉換運算子是一般功能，例如，您可以擁有 `explicit operator MyClass()`。 不過，標準程式庫目前只使用一種形式：`explicit operator bool()`，此形式可讓類別安全地進行布林值測試。 \(簡單的「`operator bool()`」非常危險\)。 在過去，Visual C\+\+ 會模擬 `explicit operator bool()` 和 `operator pointer-to-member()`，導致各種問題並且使效率些微不足。 現在已完全移除這個「假的 bool」解決方法。  
  
 **隨機：** `uniform_int_distribution` 現在已經完全無偏誤，而且 `shuffle()` 會在 `<algorithm>` 中實作，可直接接受統一亂數產生器如 `mersenne_twister`。  
  
 **多載傳址運算子抗性：** C\+\+98\/03 已禁止 STL 容器的項目多載其傳址運算子。  像 `CComPtr` 這樣的類別所做的就是此類工作，以便要求諸如 `CAdapt` 的 Helper 類別避免 STL 產生此類多載。  在開發 Visual Studio 2010 中的 Visual C\+\+ 期間，STL 的變更會讓它在更多情況下拒絕多載傳址運算子。 C\+\+11 變更需求以接受已多載的傳址運算子。 C\+\+11 和 Visual Studio 2010 中的 Visual C\+\+ 會提供 Helper 函式 `std::addressof()`，這可以不考慮運算子多載而取得物件真正的位址。  在發行 Visual Studio 2010 中的 Visual C\+\+ 之前，我們嘗試以 "`&elem`" 取代"`std::addressof(elem)`"，這樣也會有抵抗性。[!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] 更進一步之後，多載其傳址運算子的類別就可在整個 STL 中使用。  
  
 **[!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] 多方面超越了 C\+\+11：**  
  
 **SCARY 迭代器：**SCARY 迭代器已依照 C\+\+11 標準所允許 \(但非必要\) 的方式完成實作，如文件 [N2911：＜最小化泛型類別中的相依性，以產生更快速且更小型的程式＞](http://go.microsoft.com/fwlink/p/?LinkID=235115)和 [N2980：＜SCARY 迭代器指派和初始化 \(修訂 1\)＞](http://go.microsoft.com/fwlink/p/?LinkID=235116)所述。  
  
 **檔案系統：**已加入 [TR2 提議](http://go.microsoft.com/fwlink/p/?LinkID=235117)的 `<filesystem>` 標頭。 它提供 `recursive_directory_iterator` 及其他有趣的功能。  在 TR2 的工作因為 C\+\+0x 延遲且即將變更為 C\+\+11 而凍結之前，2006 提案已自 [Boost.Filesystem V2](http://go.microsoft.com/fwlink/p/?LinkID=235118) 衍生而出。 它之後逐漸發展成 Boost.Filesystem V3，實作於 Visual Studio 2015 中。  
  
 而且是主要最佳化！  根據目前的表示，我們所有的容器現在是最佳小型。  這指的是容器物件本身，而非它們所指向的內容。  例如，`std::vector` 會包含三個原始指標。  在 Visual Studio 2010 中的 Visual C\+\+ 中，x86 發行模式的 `std::vector` 為 16 位元組。  在 [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] 中，這是 12 個位元組，也就是最佳的小型。  此事非同小可：如果您的程式中有 100,000 個向量，[!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] 就會為您節省 400,000 個位元組。  降低記憶體使用量可節省空間和時間。  
  
 這是藉由避免儲存空的配置器和比較子的方式達到目的，因為 `std::allocator` 和 `std::less` 是無狀態的。  \(只要是無狀態，自訂配置器\/比較子也啟用這些最佳化。  可設定狀態的配置器\/比較子存放顯然是無法避免的，但這些情況非常罕見\)。  
  
 **[!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 實作了一些重要的 C\+\+14 程式庫功能：**  
  
-   「透明運算子函式」`less<>`、`greater<>`、`plus<>`、`multiplies<>`，依此類推。  
  
-   `make_unique<T>(args...)` 和 `make_unique<T[]>(n)`  
  
-   `cbegin()`\/`cend()`、`rbegin()`\/`rend()` 和 `crbegin()`\/`crend()` 非成員函式。  
  
 \[[本文內容](#top)\]  
  
## 請參閱  
 [歡迎回到 C\+\+](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C\+\+ 語言參考](../cpp/cpp-language-reference.md)   
 [Lambda 運算式](../cpp/lambda-expressions-in-cpp.md)   
 [以範圍為基礎的 for 陳述式 \(C\+\+\)](../cpp/range-based-for-statement-cpp.md)   
 [C\+\+ Standard Library](../standard-library/cpp-standard-library-reference.md)   
 [Visual C\+\+ Team 部落格](http://blogs.msdn.com/b/vcblog/)   
 [What's New for Visual C\+\+](../top/what-s-new-for-visual-cpp-in-visual-studio-2015.md)   
 [Visual C\+\+ 2015 的重大變更](../porting/visual-cpp-change-history-2003-20151.md)