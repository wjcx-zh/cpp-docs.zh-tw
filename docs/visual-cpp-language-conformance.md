---
title: Visual C++ 語言一致性
ms.date: 11/15/2017
ms.technology: cpp-language
ms.assetid: 475da6e9-0d78-4b4e-bd23-f41c406c4efe
author: corob-msft
ms.author: corob
ms.openlocfilehash: 17a830238e21a5ef231285b5be9bfa6ae39183f4
ms.sourcegitcommit: 42e65c171aaa17a15c20b155d22e3378e27b4642
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2019
ms.locfileid: "58356266"
---
# <a name="visual-c-language-conformance"></a>Visual C++ 語言一致性

本主題摘要說明 Visual Studio 2017 及較舊版 C++ 編譯器功能和標準程式庫功能之 ISO C++03、C++11、C++14、C++17 和 C++20 草案的語言標準一致性。 每個編譯器和標準程式庫功能的名稱皆可連結至說明該項功能的 ISO C++ 標準提案計畫書 (若在發行時有提供該計畫書)。 支援的資料行會列出最先出現該功能支援的 Visual Studio 版本。

如需 Visual Studio 2017 一致性改善及其他變更的詳細資料，請參閱 [Visual Studio 2017 中的 C++ 編譯器一致性改善](cpp-conformance-improvements-2017.md)及 [Visual Studio 2017 中 Visual C++ 的新功能](what-s-new-for-visual-cpp-in-visual-studio.md)。 如需舊版的一致性變更，請參閱 [Visual C++ 變更歷程記錄](porting/visual-cpp-change-history-2003-2015.md)和[從 2003 到 2015 的 Visual C++ 新功能](porting/visual-cpp-what-s-new-2003-through-2015.md)。 如需 C++ 小組發出的最新消息，請瀏覽 [Visual C++ Team Blog](https://blogs.msdn.microsoft.com/vcblog/) (Visual C++ 小組部落格)。

> [!NOTE]
> Visual Studio 2015 與 Visual Studio 2017 之間沒有二進位檔重大變更。

## <a name="compiler-features"></a>編譯器功能

|功能範圍| |
|----|---|
|__C++03/11 核心語言功能__|__支援__|
|&nbsp;&nbsp;其他所有項目|VS 2015 <sup>[A](#note_A)</sup>|
|&nbsp;&nbsp;兩階段名稱查詢|VS 2017 15.7 <sup>[B](#note_B)</sup>|
|&nbsp;&nbsp;[N2634 運算式 SFINAE](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2634.html)|VS 2017 15.7|
|&nbsp;&nbsp;[N1653 C99 前置處理器](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2004/n1653.htm)|部分 <sup>[D](#note_D)</sup>|
|&nbsp;&nbsp;[N1988 擴充整數類型](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2006/n1988.pdf)|不適用 <sup>[E](#note_E)</sup>|
|__C++14 核心語言功能__|__支援__|
|&nbsp;&nbsp;[N3323 調整內容轉換的描述](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3323.pdf)|VS 2013|
|&nbsp;&nbsp;[N3472 二進位常值](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3472.pdf)|VS 2015|
|&nbsp;&nbsp;[N3638 auto 和 decltype(auto) 傳回型別](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3638.html)|VS 2015|
|&nbsp;&nbsp;[N3648 init 擷取](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3648.html)|VS 2015|
|&nbsp;&nbsp;[N3649 泛型 Lambda](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3649.html)|VS 2015|
|&nbsp;&nbsp;[N3760 [[deprecated]] 屬性](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3760.html)|VS 2015|
|&nbsp;&nbsp;[N3778 依大小調整的解除配置](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3778.html)|VS 2015|
|&nbsp;&nbsp;[N3781 數字分隔符號](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3781.pdf)|VS 2015|
|&nbsp;&nbsp;[N3651 變數範本](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3651.pdf)|VS 2015.2|
|&nbsp;&nbsp;[N3652 擴充的 constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3652.html)|VS 2017|
|&nbsp;&nbsp;[N3653 彙總的 NSDMI](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3653.html)|VS 2017|
|&nbsp;&nbsp;[N3664 避免/融合配置](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3664.html)|不適用 <sup>[F](#note_F)</sup>|
|__C++17 核心語言功能__|__支援__|
|&nbsp;&nbsp;[N4086 移除三併詞](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4086.html)|VS 2010 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N3922 使用 braced-init-list 的 auto 新規則](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3922.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4051 範本 template 參數中的 typename](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4051.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4266 命名空間和列舉程式的屬性](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4266.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4267 u8 字元常值](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4267.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4230 巢狀命名空間定義](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4230.html)|VS 2015.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N3928 Terse static_assert](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3928.pdf)|VS 2017 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0184R0 通用的範圍架構 for 迴圈](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html)|VS 2017 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0188R1 [[fallthrough]] 屬性](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0188r1.pdf)|VS 2017 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0001R1 移除 register 關鍵字](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0001r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0002R1 移除 bool 的 operator++](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0002r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0018R3 依據值擷取 *this](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0018r3.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0028R4 使用不重複的屬性命名空間](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0028r4.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0061R1 __has_include](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0061r1.html)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0138R2 整數的固定列舉直接清單初始化](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0138r2.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0170R1 constexpr Lambda](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0170r1.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0189R1 [[nodiscard]] 屬性](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0189r1.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0212R1 [[maybe_unused]] 屬性](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0212r1.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0217R3 結構化的繫結](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0217r3.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0292R2 constexpr if 陳述式](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0292r2.html)|VS 2017 15.3 <sup>[G](#note_G)</sup>|
|&nbsp;&nbsp;[P0305R1 使用初始設定式的選取範圍陳述式](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0305r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0245R1 Hexfloat 常值](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0245r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N4268 允許多個非類型範本引數](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4268.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N4295 摺疊運算式](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4295.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0003R5 移除動態例外狀況規格](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0012R1 新增 noexcept 型別系統](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0012r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0035R4 過度對齊的動態記憶體配置](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0035r4.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0386R2 內嵌變數](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0386r2.pdf)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0522R0 範本 template 參數與相容引數的比對](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0522r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0036R0 移除部分空白一元摺疊](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0036r0.pdf)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N4261 修正限定性條件轉換](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4261.html)|VS 2017 15.7  <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0017R1 擴充的彙總初始化](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0017r1.html)|VS 2017 15.7  <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0091R3 類別範本的範本引數推斷](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html)<br />&nbsp;&nbsp;[P0512R0 類別樣板引數推斷問題](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0512r0.pdf) \(英文\)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0127R2 使用 auto 宣告非類型範本參數](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r2.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0135R1 保證的複製省略](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0135r1.html)|VS 2017 15.6|
|&nbsp;&nbsp;[P0136R1 改寫繼承建構函式](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0136r1.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0137R1 std::launder](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0137r1.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0145R3 調整運算式評估順序](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0145r3.pdf)<br />&nbsp;&nbsp;[P0400R0 函式引數的評估順序](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0400r0.html) \(英文\)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0195R2 using-declaration 的套件延伸模組](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0195r2.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0283R2 略過無法辨認的屬性](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0283r2.html)|VS 2015 <sup>[14](#note_14)</sup>|

|功能範圍| |
|----|---|
|__C++17 核心語言功能 (缺失報表)__|__支援__|
|&nbsp;&nbsp;[P0702R1 修正初始設定式清單 ctor 的類別樣板引數推斷](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0702r1.html) \(英文\)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0588R1 簡化隱含的 Lambda 擷取](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0588r1.html)|否|
|&nbsp;&nbsp;[CWG 1581：何時會定義 constexpr 成員函式？](https://wg21.cmeerw.net/cwg/issue1581)|否|
|&nbsp;&nbsp;[P0962R1 放寬結構化繫結的自訂點尋找規則](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0961r1.html)|否|
|&nbsp;&nbsp;[P0962R2 放寬 range-for 迴圈的自訂點尋找規則](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0962r1.html)|否|
|&nbsp;&nbsp;[P0969R0 允許可存取成員進行結構化繫結](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0969r0.pdf)|否|

|功能範圍| |
|----|---|
|__C++20 核心語言功能__|__支援__|
|&nbsp;&nbsp;[P0306R4 新增 &#95;&#95;VA_OPT&#95;&#95; 以進行逗號省略和逗號刪除](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0306r4.html)|否|
|&nbsp;&nbsp;[P0329R4 指定的初始化](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0329r4.pdf) \(英文\)|否|
|&nbsp;&nbsp;[P0409R2 允許 Lambda 擷取 [=, this]](http://open-std.org/JTC1/SC22/WG21/docs/papers/2017/p0409r2.html) \(英文\)|否|
|&nbsp;&nbsp;[P0428R2 針對泛型 Lambda 的熟悉範本語法](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0428r2.pdf) \(英文\)|否|
|&nbsp;&nbsp;[P0683R1 針對位元欄位的預設成員初始設定式](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0683r1.html) \(英文\)|否|
|&nbsp;&nbsp;[P0704R1 修正針對成員的常數左值 ref 限定指標](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0704r1.html) \(英文\)|否|
|&nbsp;&nbsp;[P0734R0 概念](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0734r0.pdf) \(英文\)|否|

## <a name="standard-library-features"></a>標準程式庫功能

|功能範圍| |
|---|---|
|__C++20 標準程式庫功能__|__支援__|
|&nbsp;&nbsp; [P0777R1 避免不必要的 Decay](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0777r1.pdf)|VS 2017 15.7 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0463R1 位元組順序](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0463r1.html) \(英文\)|否|
|&nbsp;&nbsp;[P0674R1 適用於陣列的 make_shared()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0674r1.html) \(英文\)|否|
|&nbsp;&nbsp;[P0858R0 Constexpr 迭代器需求](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0858r0.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0809R0 比較未排序的容器](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0809r0.pdf)| VS 2010 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp; [P0020R3 atomic\<float>、atomic\<double>、atomic\<long double>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0020r6.html)|否|
|&nbsp;&nbsp; [P0053R7 \<syncstream>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0053r7.pdf)<br />&nbsp;&nbsp; [P0753R2 osyncstream 操作工具](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0753r2.pdf)|否|
|&nbsp;&nbsp; [P0122R7 \<span>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0122r7.pdf)|否|
|&nbsp;&nbsp; [P0202R3 \<algorithm> 和 exchange() 的 constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0202r3.html)|否|
|&nbsp;&nbsp; [P0355R7 \<chrono> 行事曆和時區](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0355r7.html)|否|
|&nbsp;&nbsp; [P0415R1 \<complex> 的 constexpr (再次)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0415r1.html)|否|
|&nbsp;&nbsp; [P0439R0 列舉類別 memory_order](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0439r0.html)|否|
|&nbsp;&nbsp; [P0457R2 basic_string/basic_string_view 的 starts_with()/ends_with()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0457r2.html)|否|
|&nbsp;&nbsp; [P0550R2 remove_cvref](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0550r2.pdf)|否|
|&nbsp;&nbsp; [P0551R3 您不應該特製化 std 函式範本！](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0551r3.pdf)|否|
|&nbsp;&nbsp; [P0600R1 \[\[nodiscard\]\] 適用於 STL 第一部分](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0600r1.pdf)|否|
|&nbsp;&nbsp; [P0616R0 在 \<numeric> 中使用 move()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0616r0.pdf)|否|
|&nbsp;&nbsp; [P0653R2 to_address()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0653r2.html)|否|
|&nbsp;&nbsp; [P0718R2 atomic\<shared_ptr\<T>>、atomic\<weak_ptr\<T>>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0718r2.html)|否|
|&nbsp;&nbsp; [P0754R2 \<version>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0754r2.pdf)|否|
|&nbsp;&nbsp; [P0767R1 淘汰 is_pod](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0767r1.html)|否|
|&nbsp;&nbsp; [P0768R1 太空船比較運算子 \<=> 的程式庫支援](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0768r1.pdf)|否|
|&nbsp;&nbsp; [P0966R1 string::reserve() 不應該壓縮](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0966r1.html)|否|
|__C++17 標準程式庫功能__|__支援__|
|&nbsp;&nbsp;[P0433R2 將針對類別樣板的樣板推斷整合至標準程式庫](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0433r2.html) \(英文\)<br />&nbsp;&nbsp;[P0739R0 改善針對標準程式庫的類別樣板引數推斷整合](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0739r0.html) \(英文\)|VS 2017 15.7|
|&nbsp;&nbsp;[P0426R1 char_traits 的 constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0426r1.html)|VS 2017 15.7|
|&nbsp;&nbsp;[P0030R1 hypot(x, y, z)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0030r1.pdf)|VS 2017 15.7|
|&nbsp;&nbsp;[P0220R1 程式庫基本概念 V1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html)|VS 2017 15.6 <sup>[J](#note_J)</sup>|
|&nbsp;&nbsp;[P0067R5 基礎字串轉換](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0067r5.html)|VS 2017 15.7 <sup>[charconv](#note_charconv)</sup>|
|&nbsp;&nbsp;[N4562 程式庫基本概念︰\<memory_resource>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#memory.resource.synop)<br />&nbsp;&nbsp;[P0337R0 刪除 polymorphic_allocator 指派](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0337r0.html)|VS 2017 15.6|
|&nbsp;&nbsp;[P0024R2 平行演算法](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0024r2.html)<br />&nbsp;&nbsp;[P0336R1 重新命名平行執行原則](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0336r1.pdf)<br />&nbsp;&nbsp;[P0394R4 針對例外狀況，平行演算法應使用 terminate()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0394r4.html)<br />&nbsp;&nbsp;[P0452R1 統一 \<numeric> 平行演算法](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0452r1.html) \(英文\)|VS 2017 15.7|
|&nbsp;&nbsp;[P0226R1 數學特殊函式](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0226r1.pdf)|VS 2017 15.7|
|&nbsp;&nbsp;[P0218R1 \<filesystem>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0218r1.html)<br />&nbsp;&nbsp;[P0219R1 適用於 Filesystem 的相對路徑](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0219r1.html)<br />&nbsp;&nbsp;[P0317R1 針對檔案系統的目錄項目快取](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0317r1.html) \(英文\)<br />&nbsp;&nbsp;[P0392R0 支援 Filesystem 路徑的 string_view](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0392r0.pdf)<br />&nbsp;&nbsp;[P0430R2 支援非 POSIX 檔案系統](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0430r2.pdf) \(英文\)<br />&nbsp;&nbsp;[P0492R2 解決檔案系統的 NB 註解](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0492r2.html) \(英文\)|VS 2017 15.7 <sup>[K](#note_K)</sup>|
|&nbsp;&nbsp;[P0003R5 移除動態例外狀況規格](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0005R4 not_fn()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0005r4.html)<br />&nbsp;&nbsp;[P0358R1 not_fn() 的修正](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0358r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0033R1 改寫 enable_shared_from_this](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0033r1.html)|VS 2017 15.5 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0083R3 接合對應和集合](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf)<br />&nbsp;&nbsp;[P0508R0 釐清 insert_return_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0508r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0174R2 取代不必要的程式庫組件](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0174r2.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0302R1 移除 std::function 中的配置器支援](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0302r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0414R2 shared_ptr\<T[]>、shared_ptr\<T[N]>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0414r2.html)<br />&nbsp;&nbsp;[P0497R0 修正陣列的 shared_ptr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0497r0.html)|VS 2017 15.5 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0521R0 取代 shared_ptr::unique()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0521r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0607R0 適用於標準程式庫的內嵌變數](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0607r0.html) \(英文\)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0618R0 取代 \<codecvt>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0618r0.html) \(英文\)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N4562 程式庫基本概念︰Boyer-Moore search()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#func.searchers.boyer_moore)<br/>&nbsp;&nbsp;[P0253R1 修正搜尋程式傳回型別](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0253r1.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0031R0 \<array> (再次說明) 和 \<iterator> 的 constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0031r0.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0040R3 擴充記憶體管理工具](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0040r3.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0084R2 Emplace 傳回型別](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0084r2.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0152R1 atomic::is_always_lock_free](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0152r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0154R1 hardware_destructive_interference_size 等等](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0154r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0156R2 將 Variadic lock\_guard 重新命名為 scoped\_lock](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0156r2.html) \(英文\)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0258R2 has_unique_object_representations](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0258r2.html)|VS 2017 15.3 <sup>[L](#note_L)</sup>|
|&nbsp;&nbsp;[P0295R0 gcd()、lcm()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0295r0.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0298R3 std::byte](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0298r3.pdf) \(英文\)|VS 2017 15.3 <sup>[17](#note_17)、[byte](#note_byte)</sup>|
|&nbsp;&nbsp;[P0403R1 適用於 \<string_view> ("meow"sv 等) 的 UDL](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0403r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0418R2 不可部分完成的 compare_exchange memory_order 需求](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0418r2.html)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0435R1 檢修 common_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0435r1.pdf)<br />&nbsp;&nbsp;[P0548R1 調校 common\_type 和 duration](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0548r1.pdf) \(英文\)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0505R0 \<chrono> (再次說明) 的 constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0505r0.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0513R0 停用 hash](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0513r0.pdf)<br />&nbsp;&nbsp;[P0599R1 noexcept 雜湊](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0599r1.pdf) \(英文\)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0516R0 將 shared_future 複製標記為 noexcept](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0516r0.html)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0517R0 從 future_errc 建構 future_error](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0517r0.html)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0558R1 解決不可部分完成<T>具名基底類別不一致](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0558r1.pdf) \(英文\)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0604R0 將 is\_callable/result\_of 變更為 invoke\_result、is\_invocable、is\_nothrow\_invocable](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0604r0.html) \(英文\)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N4562 程式庫基本概念︰\<algorithm> sample()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#alg.random.sample)|VS 2017|
|&nbsp;&nbsp;[N4562 程式庫基本概念︰\<any>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#any)|VS 2017|
|&nbsp;&nbsp;[N4562 程式庫基本概念︰\<optional>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#optional)|VS 2017 |
|&nbsp;&nbsp;[N4562 程式庫基本概念︰\<string_view>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#string.view)|VS 2017|
|&nbsp;&nbsp;[N4562 程式庫基本概念︰\<tuple> apply()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#tuple)|VS 2017|
|&nbsp;&nbsp;[P0032R3 variant/any/optional 的同質性介面](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0032r3.pdf)|VS 2017|
|&nbsp;&nbsp;[P0077R2 is_callable、is_nothrow_callable](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0077r2.html)|VS 2017|
|&nbsp;&nbsp;[P0088R3 \<variant>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0088r3.html)|VS 2017|
|&nbsp;&nbsp;[P0163R0 shared_ptr::weak_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0163r0.html)|VS 2017|
|&nbsp;&nbsp;[P0209R2 make_from_tuple()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0209r2.pdf)|VS 2017|
|&nbsp;&nbsp;[P0254R2 整合 string_view 和 std::string](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0254r2.pdf)|VS 2017|
|&nbsp;&nbsp;[P0307R2 再次說明如何使用 Optional >=](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0307r2.pdf)|VS 2017|
|&nbsp;&nbsp;[P0393R3 如何使用 Variant >=](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0393r3.html)|VS 2017|
|&nbsp;&nbsp;[P0504R0 重新認識 in_place_t/in_place_type_t\<T>/in_place_index_t\<I>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0504r0.html)|VS 2017|
|&nbsp;&nbsp;[P0510R0 拒絕空白變異、陣列、參考和不完整類型](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0510r0.html)|VS 2017|
|&nbsp;&nbsp;[P0025R1 clamp()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0025r1.html)|VS 2015.3|
|&nbsp;&nbsp;[P0185R1 is_swappable、is_nothrow_swappable](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0185r1.html)|VS 2015.3|
|&nbsp;&nbsp;[P0272R1 非常數 basic_string::data()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0272r1.html)|VS 2015.3|
|&nbsp;&nbsp;[N4387 改善 pair 和 tuple](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4387.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4508 shared_mutex (Untimed)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4508.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0004R1 移除已取代的 Iostreams 別名](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0004r1.html)|VS 2015.2 <sup>[rem](#note_rem)</sup>|
|&nbsp;&nbsp;[P0006R0 類型特性的變數範本 (is_same_v 等等)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0006r0.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0007R1 as_const()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0007r1.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0013R1 邏輯運算子類型特性 (conjunction 等等)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0013r1.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0074R0 owner_less\<>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0074r0.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0092R1 \<chrono> floor()、ceil()、round()、abs()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0092r1.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0156R0 Variadic lock_guard](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0156r0.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N3911 void_t](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3911.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4089 unique_ptr\<T[]> 中的安全轉換](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4089.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4169 invoke()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4169.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4190 移除 auto_ptr、random_shuffle() 以及舊的 \<functional> 項目](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4190.htm)|VS 2015 <sup>[rem](#note_rem)</sup>|
|&nbsp;&nbsp;[N4258 清除 noexcept](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4258.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4259 uncaught_exceptions()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4259.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4277 完整可複製的 reference_wrapper](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4277.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4279 map/unordered_map 的 insert_or_assign()/try_emplace()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4279.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4280 size()、empty()、data()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4280.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4366 精確地限制 unique_ptr 指派](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4366.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4389 bool_constant](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4389.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0063R3 C11 標準程式庫](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0063r3.html)|VS 2015 <sup>[C11](#note_C11)、[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4510 vector/list/forward_list 中的不完整類型支援](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4510.html)|VS 2013 <sup>[14](#note_14)</sup>|
|__C++14 標準程式庫功能__|__支援__|
|&nbsp;&nbsp;[N3462 適合 SFINAE 的 result_of](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3462.html)|VS 2015.2|
|&nbsp;&nbsp;[N3302 \<complex> 的 constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2011/n3302.html)|VS 2015|
|&nbsp;&nbsp;[N3469 \<chrono> 的 constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3469.html)|VS 2015|
|&nbsp;&nbsp;[N3470 \<array> 的 constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3470.html)|VS 2015|
|&nbsp;&nbsp;[N3471 \<initializer_list>、\<tuple>、\<utility> 的 constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3471.html)|VS 2015|
|&nbsp;&nbsp;[N3545 integral_constant::operator()()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3545.pdf)|VS 2015|
|&nbsp;&nbsp;[N3642 適用於 \<chrono>、\<string> 的 UDL (1729ms、"meow"s 等等)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3642.pdf)|VS 2015|
|&nbsp;&nbsp;[N3644 Null 正向迭代器](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3644.pdf)|VS 2015|
|&nbsp;&nbsp;[N3654 quoted()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3654.html)|VS 2015|
|&nbsp;&nbsp;[N3657 異質關聯查閱](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3657.htm)|VS 2015|
|&nbsp;&nbsp;[N3658 integer_sequence](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3658.html)|VS 2015|
|&nbsp;&nbsp;[N3659 shared_mutex (Timed)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3659.html)|VS 2015|
|&nbsp;&nbsp;[N3668 exchange()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3668.html)|VS 2015|
|&nbsp;&nbsp;[N3669 修正未含 const 的 constexpr 成員函式](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3669.pdf)|VS 2015|
|&nbsp;&nbsp;[N3670 get\<T>()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3670.html)|VS 2015|
|&nbsp;&nbsp;[N3671 雙重範圍 equal()、is_permutation()、mismatch()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3671.html)|VS 2015|
|&nbsp;&nbsp;[N3778 依大小調整的解除配置](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3778.html)|VS 2015|
|&nbsp;&nbsp;[N3779 適用於 \<complex> 的 UDL (3.14i 等等)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3779.pdf)|VS 2015|
|&nbsp;&nbsp;[N3789 \<functional> 的 constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3789.htm)|VS 2015|
|&nbsp;&nbsp;[N3887 tuple_element_t](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3887.pdf)|VS 2015|
|&nbsp;&nbsp;[N3891 重新命名 shared_mutex (Timed) 為 shared_timed_mutex](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3891.htm)|VS 2015|
|&nbsp;&nbsp;[N3346 容器元素的最低需求](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3346.pdf)|VS 2013|
|&nbsp;&nbsp;[N3421 透明運算子函式 (less\<> 等等)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3421.htm)|VS 2013|
|&nbsp;&nbsp;[N3655 適用於 \<type_traits> 的別名範本 (decay_t 等等)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3655.pdf)|VS 2013|
|&nbsp;&nbsp;[N3656 make_unique()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3656.htm)|VS 2013|
|&nbsp;&nbsp;[N3924 不鼓勵使用 rand()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3924.pdf)|N/A|

一起提列的報告表示該項功能已表決納入標準，而改善或該擴展功能的一或多項報告也已表決納入標準。 這些功能皆會一起實作。

### <a name="supported-values"></a>支援的值

__否__：表示尚未實作。<br/>
__部份__：表示 Visual Studio 2017 的實作不完整。 如需詳細資料，請參閱＜附註＞一節。<br/>
__N/A__：表示提案報告未描述這些功能。 這些報告已更改標準的語言，但未建立任何實作者的工作。 為求完整性，將它們一併列出。<br/>
__VS 2010__：表示 Visual Studio 2010 所支援的功能。<br/>
__VS 2013__：表示 Visual Studio 2013 所支援的功能。<br/>
__VS 2015__：表示 Visual Studio 2015 RTM 所支援的功能。<br/>
__VS 2015.2__ 和 __VS 2015.3__：表示 Visual Studio 2015 Update 2 和 Visual Studio 2015 Update 3 分別支援的功能。<br/>
__VS 2017__：表示 Visual Studio 2017 RTM 所支援的功能。<br/>
__VS 2017 15.3__：表示 Visual Studio 2017 15.3 版所支援的功能。<br/>
__VS 2017 15.5__表示 Visual Studio 2017 15.5 版所支援的功能。<br/>
__VS 2017 15.7__ 表示 Visual Studio 2017 15.7 版所支援的功能。<br/>

### <a name="notes"></a>注意

<a name="note_A"></a>__A__ 在 /std:c++14 模式中，動態例外狀況規格保持未實作，而 throw() 仍被視為 \_\_declspec(nothrow) 的同義字。 在 C++17 中，P0003R5 移除了大部分的動態例外狀況規格，並保留一個殘留項目：throw() 將會被淘汰，而且必須作為 noexcept 的同義字。 在 /std:c++17 模式中，MSVC 現在藉由賦與 throw() 與 noexcept 相同的行為 (也就是透過終止強制執行) 來符合標準。

編譯器選項 /Zc:noexceptTypes- 會要求 \_\_declspec(nothrow) 的舊行為。 很可能會在 C++20 中移除 throw()。 為了協助移轉程式碼以回應標準及我們實作中的這些變更，已在 **/std:c++17** 和 **/permissive-** 下新增例外狀況規格問題的編譯器警告。

<a name="note_B"></a>__B__ 在 Visual Studio 2017 15.7 版的 /permissive- 模式下支援。 如需詳細資訊，請參閱 [MSVC 推出兩階段名稱查閱支援](https://blogs.msdn.microsoft.com/vcblog/2017/09/11/two-phase-name-lookup-support-comes-to-msvc/)。

<a name="note_C"></a>__C__ 自 Visual Studio 2015 Update 2 起，編譯器的運算式 SFINAE 支援對標準程式庫而言已足夠。 不論是否設定了/permissive- 模式，Visual Studio 2017 15.7 均可支援。 有一些 Bug 仍待修正。 「唯一的標記類型」因應措施已不再需要，因此我們已從 STL 實作中移除這個因應措施。

<a name="note_D"></a>__D__ 編譯器的 C99 前置處理器規則支援在 Visual Studio 2017 中仍未完善。 支援 Variadic 巨集，但在前置處理器的行為方面有很多 Bug。  我們正在檢修前置處理器，並且即將以實驗方式在 **/permissive-** 模式下遞送這些變更。

<a name="note_E"></a>__E__ 編譯器可以支援擴充的整數類型，但並沒有這個必要，因此將其標示為不適用。  我們也決定不提供支援 (如同 GCC 和 Clang)。

<a name="note_F"></a>__F__ 同樣地，編譯器可以實作此最佳化，但並沒有這個必要，因此將其標示為不適用。

<a name="note_G"></a>__G__ 於 [/std:c++14](./build/reference/std-specify-language-standard-version.md) 底下受到支援，並具有可隱藏的警告。

<a name="note_J"></a>__J__ Visual Studio 2015 中未完成的功能分別列於此表各處。

<a name="note_K"></a>__K__ 這是全新的實作，與舊版 std::experimental 不相容，符號連結支援、Bug 修正，以及標準必要行為的變更都需要此實作。 目前，包括 \<filesystem> 可提供新的 std::filesystem 和之前的 std::experimental::filesystem，而包括 \<experimental/filesystem> 只會提供舊的實驗性實作。 實驗性實作將會在程式庫的下一個 ABI 重大版本中「移除」。

<a name="note_L"></a>__L__ 由編譯器內建支援。

<a name="note_14"></a>__14__ 這些 C++17/20 功能一律會啟用，就算在指定 [/std:c++14](build/reference/std-specify-language-standard-version.md) (預設值) 的情況下也一樣。 這是因為該功能已在 **/std** 選項推出之前實作，或是因為條件式實作過於複雜。

<a name="note_17"></a>__17__ 這些功能是由 [/std:c++17](./build/reference/std-specify-language-standard-version.md) (或 [/std:c++latest](./build/reference/std-specify-language-standard-version.md)) 編譯器選項啟用。

<a name="note_byte"></a>__byte__ `std::byte` 是由 [/std:c++17](./build/reference/std-specify-language-standard-version.md) (或 [/std:c++latest](./build/reference/std-specify-language-standard-version.md)) 啟用，但它在某些情況下可能會與 Windows SDK 標頭發生衝突，並具有可微調的退出巨集。 可以透過將 `_HAS_STD_BYTE` 定義為 `0`來停用它。

<a name="note_C11"></a>__C11__ 通用 CRT 已實作 C++17 所需的 C11 標準程式庫組件，除了 C99 `strftime()` E/O 替代轉換規範、C11 `fopen()` 獨佔模式，以及 C11 `aligned_alloc()`之外。 最後一個項目最有可能尚未實作，因為 C11 指定 `aligned_alloc()` 的方式與 Microsoft 的 `free()` 實作並不相容，亦即 `free()` 必須能夠處理高度對齊的配置。

<a name="note_rem"></a>__rem__ 當指定 [/std:c++17](./build/reference/std-specify-language-standard-version.md) (或 [/std:c++latest](./build/reference/std-specify-language-standard-version.md)) 編譯器選項時，將會移除這些功能。 這些功能具有退出巨集：`_HAS_AUTO_PTR_ETC`、`_HAS_FUNCTION_ALLOCATOR_SUPPORT`、`_HAS_OLD_IOSTREAMS_MEMBERS`，以及 `_HAS_UNEXPECTED`。

<a name="note_charconv"></a>__charconv__ 的 from_chars() 和 to_chars() 可用於整數。 我們目前正在處理浮點 from_chars()，接下來會處理浮點 to_chars()。

<a name ="note_parallel"></a> __parallel__ C++17 的平行演算法程式庫已完成。 請注意，這並不表示每個演算法都會在每種情況下進行平行處理；最重要的演算法已進行平行處理，因此即使演算法未進行平行處理，也會提供執行原則的簽章。 我們 STL 實作的中央內部標頭 (yvals.h) 包含下列「平行演算法注意事項」：C++ 允許實作在呼叫序列演算法時實作平行演算法。   這項實作會平行處理數個常見的演算法呼叫，但並非全部。

下列演算法已平行處理：

- adjacent_difference、adjacent_find、all_of、any_of、count、count_if、equal、exclusive_scan、find、find_end、find_first_of、find_if、for_each、for_each_n、inclusive_scan、mismatch、none_of、reduce、remove、remove_if、search、search_n、sort、stable_sort、transform、transform_exclusive_scan、transform_inclusive_scan、transform_reduce。

下列各項目前未平行處理：

- 目標硬體上沒有明顯的平行處理效能改善；只對沒有分支的元素進行複製或置換的所有演算法通常會受到記憶體頻寬限制：
  - copy、copy_backward、copy_n、fill、fill_n、move、move_backward、remove、remove_if、replace、replace_if、reverse、reverse_copy、rotate、rotate_copy、swap_ranges
- 使用者平行處理原則的需求存在混淆。仍可能在上述類別目錄中：
  - generate、generate_n
- 有效的平行處理可能不可行：
  - partial_sort、partial_sort_copy
- 尚未評估；平行處理也許會在未來版本中實作，而且可能有幫助：
  - copy_if、includes、inplace_merge、is_heap、is_heap_until、is_partitioned、is_sorted、is_sorted_until、lexicographical_compare、max_element、merge、min_element、minmax_element、nth_element、partition_copy、remove_copy、remove_copy_if、replace_copy、replace_copy_if、set_difference、set_intersection、set_symmetric_difference、set_union、stable_partition、unique、unique_copy

## <a name="see-also"></a>另請參閱

[C++ 語言參考](cpp/cpp-language-reference.md)<br/>
[C++ 標準程式庫](standard-library/cpp-standard-library-reference.md)<br/>
[Visual Studio 2017 中的 C++ 一致性改善](cpp-conformance-improvements-2017.md)<br/>
[Visual Studio 2017 中 Visual C++ 的新功能](what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
[從 2003 到 2015 的 Visual C++ 變更歷程記錄](porting/visual-cpp-change-history-2003-2015.md)<br/>
[從 2003 到 2015 的 Visual C++ 新功能](porting/visual-cpp-what-s-new-2003-through-2015.md)<br/>
[Visual C++ Team Blog](https://blogs.msdn.microsoft.com/vcblog/) (Visual C++ 小組部落格)
