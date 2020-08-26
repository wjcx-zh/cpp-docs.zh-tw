---
title: 最佳化最佳做法
ms.date: 05/06/2019
helpviewer_keywords:
- C++, optimization
- optimization, best practices
ms.assetid: f3433148-7255-4ca6-8a4f-7c31aac88508
ms.openlocfilehash: 425fa0bb6b7aab502ce493ced8b587fad8ce59a8
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833344"
---
# <a name="optimization-best-practices"></a>最佳化最佳做法

本檔說明在 Visual Studio 中優化 c + + 程式的一些最佳作法。

## <a name="compiler-and-linker-options"></a>編譯器和連結器選項

### <a name="profile-guided-optimization"></a>特性指引優化

Visual Studio 支援 (PGO) 的特性 *指引優化* 。 這項優化會使用設定檔資料，從訓練執行的應用程式版本定型，以加速應用程式之後的優化。 使用 PGO 可能相當耗時，因此它可能不是每個開發人員所使用的內容，但我們建議您在產品的最終發行組建中使用 PGO。 如需詳細資訊，請參閱[特性指引最佳化](profile-guided-optimizations.md)。

此外， *整個程式優化* (也知道連結時間產生程式碼) ，而且 **`/O1`** **`/O2`** 已改善和優化。 一般而言，使用其中一個選項所編譯的應用程式，將會比使用舊版編譯器編譯的應用程式更快。

如需詳細資訊，請參閱[ `/GL` (整個程式優化) ](reference/gl-whole-program-optimization.md)和[ `/O1` ， `/O2` (最小化大小，) 最大化速度](reference/o1-o2-minimize-size-maximize-speed.md)。

### <a name="which-level-of-optimization-to-use"></a>要使用的優化層級

如果有可能的話，應該使用特性指引優化來編譯最終發行組建。 如果無法使用 PGO 建立，不論是否因為沒有足夠的基礎結構來執行已檢測的組建，或無法存取案例，我們建議使用整個程式優化來建立。

**`/Gy`** 參數也非常有用。 它會針對每個函式產生個別的 COMDAT，讓連結器在移除未參考的 Comdat 和 COMDAT 折迭時有更多的彈性。 使用的唯一缺點 **`/Gy`** 是，它可能會在進行偵錯工具時發生問題。 因此，通常建議使用它。 如需詳細資訊，請參閱[ `/Gy` (啟用函數層級連結) ](reference/gy-enable-function-level-linking.md)。

針對64位環境中的連結，建議使用 **`/OPT:REF,ICF`** 連結器選項，而在32位環境中則 **`/OPT:REF`** 建議使用。 如需詳細資訊，請參閱 [/opt (優化) ](reference/opt-optimizations.md)。

此外，也強烈建議您即使使用優化的發行組建，也會產生 debug 符號。 它不會影響產生的程式碼，而且如果需要的話，可讓您更輕鬆地將應用程式進行調試。

### <a name="floating-point-switches"></a>浮點參數

**`/Op`** 編譯器選項已移除，並新增了下列四個處理浮點優化的編譯器選項：

|選項|描述|
|-|-|
|**`/fp:precise`**|這是預設建議，在大部分情況下都應該使用。|
|**`/fp:fast`**|如果效能是最重要的，例如在遊戲中，則建議使用。 這會導致最快的效能。|
|**`/fp:strict`**|如果需要精確的浮點例外狀況和 IEEE 行為，則建議使用。 這會導致最慢的效能。|
|**`/fp:except[-]`**|可以搭配 **`/fp:strict`** 或使用 **`/fp:precise`** ，但無法搭配使用 **`/fp:fast`** 。|

如需詳細資訊，請參閱[ `/fp` (指定浮點數行為) ](reference/fp-specify-floating-point-behavior.md)。

## <a name="optimization-declspecs"></a>優化 declspecs

在本節中，我們將探討兩個可在程式中用來協助效能的 declspecs： `__declspec(restrict)` 和 `__declspec(noalias)` 。

`restrict`Declspec 只能套用至傳回指標的函式宣告，例如`__declspec(restrict) void *malloc(size_t size);`

`restrict`Declspec 會在傳回 unaliased 指標的函式上使用。 這個關鍵字是用來進行的 C 執行時間程式庫， `malloc` 因為它永遠不會傳回目前程式中已使用的指標值 (除非您執行的是不合法的專案，例如在釋放) 之後使用記憶體。

`restrict`Declspec 會提供編譯器更多有關執行編譯器優化的資訊。 編譯器所能判斷的最困難的事情之一，就是指標別名其他指標，而使用這項資訊可大幅協助編譯器。

值得一提的是，這是編譯器的保證，而不是編譯器會驗證的內容。 如果您的程式不當使用此 `restrict` declspec，您的程式可能會有不正確的行為。

如需詳細資訊，請參閱 [`restrict`](../cpp/restrict.md)。

`noalias`Declspec 也只會套用至函式，並指出函式是半純虛擬函數。 半純虛擬函式是指只參考或修改引數的區域變數、引數和第一層間接取值的函數。 此 declspec 是對編譯器的承諾，而且如果函式參考全域或第二層的指標引數間接取值，則編譯器可能會產生會中斷應用程式的程式碼。

如需詳細資訊，請參閱 [`noalias`](../cpp/noalias.md)。

## <a name="optimization-pragmas"></a>優化 pragma

另外還有幾個實用的 pragma 可協助您將程式碼優化。 我們要討論的第一個是 `#pragma optimize` ：

```cpp
#pragma optimize("{opt-list}", on | off)
```

這個 pragma 可讓您以函式為基礎，設定指定的優化層級。 這適用于在特定函式以優化方式編譯時，您的應用程式會當機的罕見情況。 您可以使用此功能來關閉單一函式的優化：

```cpp
#pragma optimize("", off)
int myFunc() {...}
#pragma optimize("", on)
```

如需詳細資訊，請參閱 [`optimize`](../preprocessor/optimize.md)。

內嵌是編譯器所執行的其中一項最重要的優化，我們會在此討論一些可協助修改此行為的 pragma。

`#pragma inline_recursion` 適用于指定您是否要讓應用程式能夠內嵌遞迴呼叫。 預設為關閉。 針對小型函式的淺層遞迴，您可以開啟此功能。 如需詳細資訊，請參閱 [`inline_recursion`](../preprocessor/inline-recursion.md)。

另一個用來限制內嵌深度的有用 pragma 是 `#pragma inline_depth` 。 這在您嘗試限制程式或函式大小的情況下很有用。 如需詳細資訊，請參閱 [`inline_depth`](../preprocessor/inline-depth.md)。

## <a name="__restrict-and-__assume"></a>`__restrict` 和 `__assume`

Visual Studio 中有幾個可協助效能的關鍵字： [__restrict](../cpp/extension-restrict.md) 和 [__assume](../intrinsics/assume.md)。

首先，請注意， **`__restrict`** `__declspec(restrict)` 有兩個不同的專案。 雖然它們有點相關，但其語義不同。 **`__restrict`** 是類型限定詞（例如 **`const`** 或 **`volatile`** ），但僅適用于指標類型。

以修改的指標 **`__restrict`** 稱為 *__restrict 指標*。 __Restrict 指標是只能透過 _restrict 指標存取的指標 \_ 。 換句話說，您無法使用另一個指標來存取 _restrict 指標所指向的資料 \_ 。

**`__restrict`** 可以是 Microsoft c + + 優化工具的強大工具，但請謹慎使用。 如果使用不正確，優化工具可能會執行會中斷您應用程式的優化。

**`__restrict`** 關鍵字會取代舊版的 **/Oa**參數。

**`__assume`** 在中，開發人員可以告知編譯器對某個變數的值進行假設。

例如， `__assume(a < 5);` 告訴優化工具該程式程式碼的變數 `a` 小於5。 同樣地，這是對編譯器的承諾。 如果在 `a` 程式中的這個時間點實際上是6，則編譯器優化之後，程式的行為可能不是您預期的。 **`__assume`** 在 switch 語句和/或條件運算式之前最有用。

有一些限制 **`__assume`** 。 首先， **`__restrict`** 它只是一個建議，因此編譯器可以自由地忽略它。 此外， **`__assume`** 目前僅適用于常數的變數到差異。 例如，它不會傳播符號到差異，例如假設 (a < b) 。

## <a name="intrinsic-support"></a>內建支援

內建是函式呼叫，其中編譯器具有有關呼叫的內部知識，而不是呼叫程式庫中的函式，它會發出該函式的程式碼。 標頭檔 \<intrin.h> 包含每個支援硬體平臺的所有可用內建函式。

內建可讓程式設計人員無需使用元件，即可深入流覽程式碼。 使用內建函式有幾個優點：

- 您的程式碼更具可攜性。 多個 CPU 架構上有數個內建函式可供使用。

- 您的程式碼比較容易閱讀，因為程式碼仍是以 C/c + + 撰寫。

- 您的程式碼會獲得編譯器優化的優點。 當編譯器變得更好時，內建函式的程式碼產生也會改善。

如需詳細資訊，請參閱 [編譯器內建函式](../intrinsics/compiler-intrinsics.md)。

## <a name="exceptions"></a>例外狀況

有與使用例外狀況相關聯的效能衝擊。 使用禁止編譯器執行特定優化的 try 區塊時，會引進一些限制。 在 x86 平臺上，由於必須在程式碼執行期間產生額外的狀態資訊，因此 try 區塊會產生額外的效能降低。 在64位平臺上，try 區塊並不會降低效能，但是一旦擲回例外狀況，尋找處理常式並回溯堆疊的程式可能會很耗費資源。

因此，建議您避免將 try/catch 區塊引入不需要的程式碼中。 如果您必須使用例外狀況，請盡可能使用同步例外狀況。 如需詳細資訊，請參閱 [Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)。

最後，只會在例外狀況的例外狀況下擲回例外狀況。 使用一般控制流程的例外狀況可能會導致效能降低。

## <a name="see-also"></a>另請參閱

- [優化您的程式碼](optimizing-your-code.md)
