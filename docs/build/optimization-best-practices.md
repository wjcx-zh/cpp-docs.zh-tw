---
title: 最佳化最佳做法
ms.date: 05/06/2019
helpviewer_keywords:
- C++, optimization
- optimization, best practices
ms.assetid: f3433148-7255-4ca6-8a4f-7c31aac88508
ms.openlocfilehash: 541114b4cbf7d3d063e48b50ab265b4c95c6237c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328444"
---
# <a name="optimization-best-practices"></a>最佳化最佳做法

本文檔介紹了在 Visual Studio 中優化C++程式的一些最佳實踐。

## <a name="compiler-and-linker-options"></a>編譯器和連結器選項

### <a name="profile-guided-optimization"></a>設定檔案導向最佳化

可視化工作室支援*配置檔導向優化*(PGO)。 此優化使用應用程式檢測版本的訓練執行中的設定檔數據來驅動應用程式以後的優化。 使用 PGO 可能非常耗時,因此可能不是每個開發人員都使用的內容,但我們確實建議在產品的最終版本生成中使用 PGO。 如需詳細資訊，請參閱[特性指引最佳化](profile-guided-optimizations.md)。

此外,*整個程式優化*(也稱為連結時間代碼生成)和 **/O1**和 **/O2**優化也得到了改進。 通常,使用這些選項之一編譯的應用程式將比使用早期編譯器編譯的同一應用程式更快。

有關詳細資訊,請參閱[/GL(整個程式優化)](reference/gl-whole-program-optimization.md)和[/O1、/O2(最小化大小、最大化速度)](reference/o1-o2-minimize-size-maximize-speed.md)。

### <a name="which-level-of-optimization-to-use"></a>要使用的優化層級

如果可能,最終版本版本應使用配置檔引導優化進行編譯。 如果無法使用 PGO 進行構建,無論是由於運行檢測生成的基礎結構不足,還是無法訪問方案,我們建議使用整個程式優化進行構建。

**/Gy**開關也非常有用。 它為每個函數生成單獨的 COMDAT,在刪除未引用的 COMDAT 和 COMDAT 摺疊時,鏈路器具有更大的靈活性。 使用 **/Gy**的唯一缺點是,在調試時可能會導致問題。 因此,通常建議使用它。 如需詳細資訊，請參閱 [/Gy (啟用函式階層連結)](reference/gy-enable-function-level-linking.md)。

對於在 64 位元環境中的連結,建議使用 **/OPT:REF、ICF**連結器選項,並在 32 位元環境中建議**使用 /OPT:REF。** 有關詳細資訊,請參閱[/OPT (優化)](reference/opt-optimizations.md)。

強烈建議生成調試符號,即使使用優化的發佈版本也是如此。 它不會影響生成的代碼,如果需要,它使調試應用程式變得更加容易。

### <a name="floating-point-switches"></a>浮點開關

已刪除 **/Op**編譯器選項,並新增了以下四個處理浮點優化的編譯器選項:

|||
|-|-|
|**/fp:精確**|這是默認建議,在大多數情況下應使用。|
|**/fp:快速**|如果性能是最重要的,例如在遊戲中,則建議使用。 這將導致最快的性能。|
|**/fp:嚴格**|如果需要精確的浮點異常和 IEEE 行為,則建議這樣做。 這將導致性能最慢。|
|**/fp:除*-***|可與 **/fp:嚴格**或 **/fp:精確**,但不能與 **/fp:fast**結合使用。|

如需詳細資訊，請參閱 [/fp (指定浮點行為)](reference/fp-specify-floating-point-behavior.md)。

## <a name="optimization-declspecs"></a>優化分點

在本節中,我們將介紹兩個可用於程式以説明性能的分項:`__declspec(restrict)``__declspec(noalias)`和 。

`restrict`宣告只能應用於返回指標的函數聲明,例如`__declspec(restrict) void *malloc(size_t size);`

delspec`restrict`用於返回未別名指標的函數。 此關鍵字用於 C-Runtime 函式`malloc`庫的實現, 因為它永遠不會傳回目前程式中已在使用的指標值(除非您正在執行非法的事情,例如在釋放記憶體後使用記憶體)。

delspec`restrict`為編譯器提供了用於執行編譯器優化的詳細資訊。 編譯器最難確定的事情之一是哪些指標別名其他指標,使用此資訊對編譯器有很大説明。

值得指出的是,這是編譯器的承諾,而不是編譯器將驗證的內容。 如果程式不適當地使用此`restrict`declspec,則程式可能有不正確的行為。

有關詳細資訊,請參閱[限制](../cpp/restrict.md)。

`noalias` delspec 也僅適用於函數,並指示函數是半純函數。 半純函數是僅引用或修改局部變數、參數和參數的第一級方向函數。 此 delspec 是編譯器的承諾,如果函數引用全域或指標參數的二級方向,則編譯器可能會生成破壞應用程式的代碼。

如需詳細資訊，請參閱 [noalias](../cpp/noalias.md)。

## <a name="optimization-pragmas"></a>優化雜注

還有一些有用的實用主義者來幫助優化代碼。 我們將討論的第一個是`#pragma optimize`:

```cpp
#pragma optimize("{opt-list}", on | off)
```

此雜注允許您在函數的基礎上設置給定的優化級別。 這是應用程式在編譯給定函數時通過優化編譯時崩潰的罕見場合的理想選擇。 您可以使用它關閉單個函數的優化:

```cpp
#pragma optimize("", off)
int myFunc() {...}
#pragma optimize("", on)
```

有關詳細資訊,請參閱[優化](../preprocessor/optimize.md)。

內聯是編譯器執行的最重要優化之一,在這裡,我們討論幾個有助於修改此行為的雜注。

`#pragma inline_recursion`用於指定是否希望應用程式能夠內聯遞歸調用。 默認情況下,它處於關閉狀態。 對於小函數的淺遞歸,您可以打開此功能。 有關詳細資訊,請參閱[inline_recursion](../preprocessor/inline-recursion.md)。

另一個有用的雜注,以限制內聯的深度是`#pragma inline_depth`。 這在嘗試限制程式或函數大小的情況下通常很有用。 有關詳細資訊,請參閱[inline_depth](../preprocessor/inline-depth.md)。

## <a name="__restrict-and-__assume"></a>__restrict和\__assume

Visual Studio 中有幾個關鍵字可以説明性能[:__restrict](../cpp/extension-restrict.md)和[__assume。](../intrinsics/assume.md)

首先,應該指出,`__restrict``__declspec(restrict)`這是兩碼事。 雖然它們有些相關,但它們的語義是不同的。 `__restrict`是類型限定符,如`const``volatile`或 ,但僅限於指標類型。

變更的`__restrict`指標稱為 *__restrict指標*。 __restrict指標是只能通過\__restrict指標訪問的指標。 換句話說,另一個指標不能用於訪問\__restrict指標指向的數據。

`__restrict`對於 Microsoft C++優化器來說,它可以是一個強大的工具,但使用時要非常小心。 如果使用不當,優化器可能會執行一個優化,這將破壞您的應用程式。

關鍵字`__restrict`將替換以前版本的 **/Oa**開關。

使用`__assume`,開發人員可以告訴編譯器對某個變數的值做出假設。

例如`__assume(a < 5);`,告訴優化器,在代碼行中,變數`a`小於 5。 這也是對編譯器的承諾。 如果`a`程式此時實際為 6,則編譯器優化後程序的行為可能不是您所期望的。 `__assume`在切換語句和/或條件表達式之前最有用。

對有一些`__assume`限制。 首先,就像`__restrict`,它只是一個建議,所以編譯器可以自由地忽略它。 此外,`__assume`目前僅適用於針對常量的可變不等式。 它不傳播符號不等式,例如,假設(a<b)。

## <a name="intrinsic-support"></a>內支援

內部函數是函數調用,其中編譯器對調用有內在知識,而不是在庫中調用函數,而是為該函數發出代碼。 標頭檔\<intrin.h>包含每个受支持的硬件平台的所有可用内部函数。

內部函數使程式員能夠深入代碼,而無需使用程式集。 使用內在功能有幾個好處:

- 您的代碼更加便攜。 多個內部函數可用於多個 CPU 體系結構。

- 代碼更易於閱讀,因為代碼仍以 C/C++編寫。

- 您的代碼受益於編譯器優化。 隨著編譯器的更好,內部函數的代碼生成也會得到改善。

有關詳細資訊,請參閱[編譯器內部函數](../intrinsics/compiler-intrinsics.md)。

## <a name="exceptions"></a>例外狀況

使用異常會受到性能影響。 使用禁止編譯器執行某些優化的 try 塊時,會引入一些限制。 在 x86 平臺上,由於在代碼執行期間必須生成的其他狀態資訊,try 塊的性能會進一步下降。 在 64 位平臺上,try 塊不會降低性能,但一旦引發異常,查找處理程序和展開堆疊的過程可能非常昂貴。

因此,建議避免在並不真正需要的代碼中引入 try/catch 塊。 如果必須使用異常,請使用同步異常(如果可能)。 如需詳細資訊，請參閱 [Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)。

最後,僅針對例外情況引發異常。 對常規控制流使用異常可能會使性能受到影響。

## <a name="see-also"></a>另請參閱

- [最佳化程式碼](optimizing-your-code.md)
