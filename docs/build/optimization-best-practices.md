---
title: 最佳化最佳做法
ms.date: 05/06/2019
helpviewer_keywords:
- C++, optimization
- optimization, best practices
ms.assetid: f3433148-7255-4ca6-8a4f-7c31aac88508
ms.openlocfilehash: 7b1cea29a782f291f1e85f7a143730825958d91b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229775"
---
# <a name="optimization-best-practices"></a>最佳化最佳做法

本檔說明在 Visual Studio 中優化 c + + 程式的一些最佳作法。

## <a name="compiler-and-linker-options"></a>編譯器和連結器選項

### <a name="profile-guided-optimization"></a>特性指引優化

Visual Studio 支援特性*指引優化*（PGO）。 這項優化會流量分析應用程式之檢測版本的定型執行中的設定檔資料，以提高應用程式的後續優化。 使用 PGO 可能相當耗時，因此不是每個開發人員所使用的專案，但我們建議在產品的最終發行組建中使用 PGO。 如需詳細資訊，請參閱[特性指引最佳化](profile-guided-optimizations.md)。

此外，*整個程式優化*（也知道連結時間程式碼產生）和 **`/O1`** 和優化已經 **`/O2`** 改進。 一般來說，使用其中一個選項編譯的應用程式，將會比使用舊版編譯器編譯的應用程式更快。

如需詳細資訊，請參閱[ `/GL` （整個程式優化）](reference/gl-whole-program-optimization.md)和（ [ `/O1` `/O2` 最小大小、最快速度）](reference/o1-o2-minimize-size-maximize-speed.md)。

### <a name="which-level-of-optimization-to-use"></a>要使用的優化層級

如果可能的話，最後的發行組建應該使用特性指引優化來編譯。 如果無法使用 PGO 來建立，不論是因為沒有足夠的基礎結構來執行已檢測的組建，或是無法存取案例，我們建議您使用整個程式優化來建立。

**`/Gy`** 參數也非常有用。 它會為每個函式產生個別的 COMDAT，並在移除未參考的 Comdat 和 COMDAT 折迭時，讓連結器擁有更多的彈性。 唯一使用的缺點 **`/Gy`** 是，它可能會在進行偵錯工具時造成問題。 因此，通常建議使用它。 如需詳細資訊，請參閱[ `/Gy` （啟用函式層級連結）](reference/gy-enable-function-level-linking.md)。

若要在64位環境中連結，建議使用 **`/OPT:REF,ICF`** 連結器選項，並在32位環境中 **`/OPT:REF`** 建議您使用。 如需詳細資訊，請參閱[/opt （優化）](reference/opt-optimizations.md)。

即使使用優化的發行組建，也強烈建議您產生 debug 符號。 它不會影響所產生的程式碼，因此，如果需要，您可以更輕鬆地對應用程式進行 debug。

### <a name="floating-point-switches"></a>浮點參數

**`/Op`** 編譯器選項已移除，並已新增下列四個處理浮點優化的編譯器選項：

|||
|-|-|
|**`/fp:precise`**|這是預設建議，而且應該在大部分情況下使用。|
|**`/fp:fast`**|如果效能是最重要的，例如在遊戲中，則建議使用。 這會產生最快的效能。|
|**`/fp:strict`**|如果需要精確的浮點例外狀況和 IEEE 行為，則建議使用此選項。 這會導致最慢的效能。|
|**`/fp:except[-]`**|可以與或搭配使用 **`/fp:strict`** **`/fp:precise`** ，但不能用於 **`/fp:fast`** 。|

如需詳細資訊，請參閱[ `/fp` （指定浮點行為）](reference/fp-specify-floating-point-behavior.md)。

## <a name="optimization-declspecs"></a>優化 declspecs

在本節中，我們將探討可在程式中用來協助效能的兩個 declspecs： `__declspec(restrict)` 和 `__declspec(noalias)` 。

`restrict`Declspec 只能套用至傳回指標的函式宣告，例如`__declspec(restrict) void *malloc(size_t size);`

`restrict`Declspec 用於傳回 unaliased 指標的函式。 這個關鍵字是用於的 C 執行時間程式庫的執行 `malloc` ，因為它永遠不會傳回目前程式中已在使用的指標值（除非您執行不合法的動作，例如在釋放記憶體之後使用它）。

`restrict`Declspec 會提供編譯器執行編譯器優化的詳細資訊。 編譯器最難判斷的一件事，就是指標其他指標的別名，而使用這項資訊可説明編譯器。

值得一提的是，這是對編譯器的承諾，而不是編譯器將會驗證的專案。 如果您的程式不當使用此 `restrict` declspec，您的程式可能會有不正確的行為。

如需詳細資訊，請參閱 [`restrict`](../cpp/restrict.md)。

`noalias`Declspec 也只適用于函式，並指出該函式是半純虛擬函數。 半純虛擬函式是指只參考或修改區域變數、引數和第一層間接取值的函數之一。 這個 declspec 是對編譯器的承諾，如果函式參考全域或第二層的指標引數間接取值，則編譯器可能會產生會中斷應用程式的程式碼。

如需詳細資訊，請參閱 [`noalias`](../cpp/noalias.md)。

## <a name="optimization-pragmas"></a>優化 pragma

另外還有數個實用的 pragma 可協助您優化程式碼。 我們將討論的第一個 `#pragma optimize` 步驟是：

```cpp
#pragma optimize("{opt-list}", on | off)
```

此 pragma 可讓您依函數逐一設定給定的優化層級。 當指定的函式是使用優化來編譯時，您的應用程式會當機的少數情況下，這非常適合。 您可以使用此功能來關閉單一函式的優化：

```cpp
#pragma optimize("", off)
int myFunc() {...}
#pragma optimize("", on)
```

如需詳細資訊，請參閱 [`optimize`](../preprocessor/optimize.md)。

內嵌是編譯器所執行的其中一個最重要的優化，這裡我們會討論一些可協助修改此行為的 pragma。

`#pragma inline_recursion`適用于指定您是否要讓應用程式能夠內嵌遞迴呼叫。 預設為關閉。 針對小型函式的淺遞迴，您可以開啟此功能。 如需詳細資訊，請參閱 [`inline_recursion`](../preprocessor/inline-recursion.md)。

限制內嵌深度的另一個有用的 pragma 是 `#pragma inline_depth` 。 當您嘗試限制程式或函式的大小時，這項功能通常很有用。 如需詳細資訊，請參閱 [`inline_depth`](../preprocessor/inline-depth.md)。

## <a name="__restrict-and-__assume"></a>`__restrict` 和 `__assume`

Visual Studio 中有幾個可協助效能的關鍵字： [__restrict](../cpp/extension-restrict.md)和[__assume](../intrinsics/assume.md)。

首先，請注意， **`__restrict`** 和 `__declspec(restrict)` 是兩個不同的專案。 雖然它們有點相關，但其語義並不相同。 **`__restrict`** 是類型限定詞（例如 **`const`** 或 **`volatile`** ），但僅適用于指標類型。

使用修改的指標 **`__restrict`** 稱為 *__restrict 指標*。 __Restrict 指標是只能透過 _restrict 指標存取的指標 \_ 。 換句話說，另一個指標無法用來存取 _restrict 指標所指向的資料 \_ 。

**`__restrict`** 可以是 Microsoft c + + 優化工具的強大工具，但非常小心地使用它。 如果未正確使用，優化工具可能會執行會中斷應用程式的優化。

**`__restrict`** 關鍵字會取代先前版本的 **/Oa**參數。

有了 **`__assume`** ，開發人員可以告訴編譯器對某個變數的值進行假設。

例如 `__assume(a < 5);` ，告訴優化工具該程式程式碼的變數 `a` 小於5。 同樣地，這是對編譯器的承諾。 如果在 `a` 程式中的這個時間點實際上是6，則編譯器在優化之後的行為可能不是您預期的結果。 **`__assume`** 在 switch 語句和（或）條件運算式之前最有用。

有一些限制 **`__assume`** 。 首先，like **`__restrict`** ，這只是建議，因此編譯器可以自由地忽略它。 此外， **`__assume`** 目前僅適用于常數的變數到差異。 它不會傳播符號到差異，例如，假設為（a < b）。

## <a name="intrinsic-support"></a>內建支援

內建函式呼叫編譯器具有關于呼叫的內部知識，而不是呼叫程式庫中的函式，而是發出該函式的程式碼。 標頭檔 \<intrin.h> 包含每個受支援硬體平臺的所有可用內建函式。

內建函式可讓程式設計人員不需要使用元件，就能深入流覽程式碼。 使用內建函式有幾個優點：

- 您的程式碼更具可攜性。 有數個內建函式可用於多個 CPU 架構。

- 您的程式碼較容易閱讀，因為程式碼仍是以 C/c + + 撰寫。

- 您的程式碼會獲得編譯器優化的優點。 當編譯器變得更好時，針對內建函式產生的程式碼也會改善。

如需詳細資訊，請參閱[編譯器內建函式](../intrinsics/compiler-intrinsics.md)。

## <a name="exceptions"></a>例外狀況

使用例外狀況時，會發生與效能的衝擊。 使用禁止編譯器執行特定優化的 try 區塊時，會引進一些限制。 在 x86 平臺上，由於必須在程式碼執行期間產生的其他狀態資訊，因此從 try 區塊得到額外的效能降低。 在64位平臺上，try 區塊不會影響效能，但是一旦擲回例外狀況，尋找處理常式並回溯堆疊的過程可能會很耗費資源。

因此，建議您避免將 try/catch 區塊引入不需要的程式碼中。 如果您必須使用例外狀況，請盡可能使用同步例外狀況。 如需詳細資訊，請參閱 [Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)。

最後，只會針對例外狀況擲回例外狀況。 使用一般控制流程的例外狀況可能會使效能降低。

## <a name="see-also"></a>另請參閱

- [優化您的程式碼](optimizing-your-code.md)
