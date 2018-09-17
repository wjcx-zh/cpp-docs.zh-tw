---
title: 最佳化的最佳做法 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, optimization
- optimization, best practices
ms.assetid: f3433148-7255-4ca6-8a4f-7c31aac88508
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d224f2551de968cef5dea5698099ad564b7894fb
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717440"
---
# <a name="optimization-best-practices"></a>最佳化的最佳做法

本文件說明 Visual c + + 最佳化的一些最佳作法。

## <a name="compiler-and-linker-options"></a>編譯器和連結器選項

### <a name="profile-guided-optimization"></a>特性指引最佳化

Visual c + + 支援*特性指引最佳化*(PGO)。 此最佳化會使用從定型執行已檢測版的應用程式的設定檔資料來驅動應用程式的更新版本的最佳化。 使用 PGO 可能很耗費時間，因此它不可能是每位開發人員使用，但我們建議使用 PGO 產品的最終版本組建。 如需詳細資訊，請參閱 <<c0> [ 特性指引最佳化](../../build/reference/profile-guided-optimizations.md)。

颾魤 ㄛ*整個程式最佳化*（也稱為連結時間產生程式碼） 和 **/o1**並 **/o2**最佳化已經有所改進。 一般情況下，使用其中一個選項所編譯的應用程式會較快，使用舊版的編譯器編譯相同的應用程式。

如需詳細資訊，請參閱 < [/GL （整個程式最佳化）](../../build/reference/gl-whole-program-optimization.md)並[/o1，/o2 （最小大小、 最快速度）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)。

### <a name="which-level-of-optimization-to-use"></a>若要使用的最佳化的層級

如果可能的話，最終版本組建應該使用特性指引最佳化進行編譯。 如果不是能夠建置運用 PGO，無論是由於不足，無法執行已檢測的組建，或無法存取案例的基礎結構，我們會建議使用整個程式最佳化的建置。

**/Gy**交換器功能也很有用。 它會產生個別的 COMDAT，每個函數讓連結器更大的彈性，就移除未參考的 Comdat 和 COMDAT 摺疊。 若要使用唯一的缺點 **/Gy**是，它可能會導致問題進行偵錯時。 因此，通常建議使用它。 如需詳細資訊，請參閱 [/Gy (啟用函式階層連結)](../../build/reference/gy-enable-function-level-linking.md)。

連結在 64 位元環境中，最好是使用 **/opt: ref，ICF**連結器選項，並在 32 位元環境中， **/opt: ref**建議。 如需詳細資訊，請參閱 < [/OPT （最佳化）](../../build/reference/opt-optimizations.md)。

此外，強烈建議您產生偵錯符號，即使使用最佳化的發行組建。 它不會影響所產生的程式碼，它可讓您更輕鬆地偵錯您的應用程式，如果很多需要。

### <a name="floating-point-switches"></a>浮點數參數

**/Op**編譯器選項已被移除，而且已加入下列四個浮動點最佳化處理的編譯器選項：

|||
|-|-|
|**/fp： 精確**|這是預設的建議，並應用於大部分的情況。|
|**/fp: fast**|如果效能是非常重要，例如在遊戲中的建議。 這會導致最快的效能。|
|**/fp: strict**|建議的 if 精確的浮點例外狀況和 IEEE 預期的行為。 這會導致最慢的效能。|
|**/fp: except [-]**|可以用於搭配 **/fp: strict**或是 **/fp： 精確**，而非 **/fp: fast**。|

如需詳細資訊，請參閱 [/fp (指定浮點行為)](../../build/reference/fp-specify-floating-point-behavior.md)。

## <a name="optimization-declspecs"></a>最佳化 declspecs

這一節我們將探討兩種可以在程式中用來協助效能的 declspecs:`__declspec(restrict)`和`__declspec(noalias)`。

`restrict` Declspec 只能套用至傳回指標，例如函式宣告 `__declspec(restrict) void *malloc(size_t size);`

`restrict` Declspec 適用於傳回非別名指標的函式。 這個關鍵字用於 C 執行階段程式庫實作`malloc`因為它永遠不會傳回已在使用目前程式中 （除非您執行的作業不合法的例如使用的記憶體之後釋出） 的指標值。

`restrict` Declspec 而發出可讓編譯器執行的編譯器最佳化的詳細資訊。 其中一個最困難的事情，讓編譯器能夠判斷是哪些指標別名其他指標，以及使用這項資訊可大幅協助編譯器。

它是值得一提，這是一項承諾的編譯器，不是像編譯器會驗證。 如果您的程式使用此`restrict`declspec 不當，您的程式可能有不正確的行為。

如需詳細資訊，請參閱 <<c0> [ 限制](../../cpp/restrict.md)。

`noalias` Declspec 也只會套用至函式，並指出函式是半純虛擬函式。 半純虛擬函式是指參考或修改只有 區域變數、 引數和 引數的第一層間接取值。 此 declspec 而發出給編譯器，承諾，如果函式會參考全域變數，或第二層間接取值的指標引數，則編譯器可能會產生程式碼，就會中斷應用程式。

如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md)。

## <a name="optimization-pragmas"></a>最佳化 pragma

另外還有數個實用的 pragma，可協助最佳化程式碼。 我們將討論的第一個是`#pragma optimize`:

```cpp
#pragma optimize("{opt-list}", on | off)
```

這個 pragma 可讓您設定指定的最佳化層級函式的函式為基礎。 這是理想的這些極少數的情況下指定的函式會以最佳化編譯時您的應用程式當機。 您可以使用此關閉單一函式的最佳化：

```cpp
#pragma optimize("", off)
int myFunc() {...}
#pragma optimize("", on)
```

如需詳細資訊，請參閱 <<c0> [ 最佳化](../../preprocessor/optimize.md)。

內嵌是 pragma 的其中一個最重要的最佳化，編譯器會執行與這裡討論幾個幫助您修改此行為。

`#pragma inline_recursion` 可用於指定您想要能夠使用內嵌的遞迴呼叫應用程式。 根據預設，它是。 小型函式的淺層遞迴，您可以開啟這項功能。 如需詳細資訊，請參閱 < [inline_recursion](../../preprocessor/inline-recursion.md)。

另一個有用的 pragma，來限制深度內嵌是`#pragma inline_depth`。 這是在您要嘗試程式 」 或 「 函式的大小限制的情況下，通常很有用。 如需詳細資訊，請參閱 < [inline_depth](../../preprocessor/inline-depth.md)。

## <a name="restrict-and-assume"></a>__restrict 和\__assume

有幾個有助於效能的 Visual c + + 中的關鍵字： [__restrict](../../cpp/extension-restrict.md)並[__assume](../../intrinsics/assume.md)。

首先，您應該注意可`__restrict`和`__declspec(restrict)`是兩個不同的項目。 雖然它們有些許相關，其語意不相同。 `__restrict` 是類型限定詞，如`const`或`volatile`，但是專為指標類型。

指標修飾`__restrict`指 *__restrict 指標*。 __Restrict 指標是只能透過存取指標\__restrict 指標。 換句話說，另一個指標無法用來存取資料所指的\__restrict 指標。

`__restrict` 可以是功能強大的工具，Visual c + + 最佳化工具，但使用十二萬分地謹慎。 如果不當使用，最佳化工具可能會執行，就會破壞您的應用程式的最佳化。

`__restrict`關鍵字取代 **/Oa**從舊版切換。

使用`__assume`，開發人員可以告知編譯器要假設某個變數的值。

比方說`__assume(a < 5);`在該行程式碼的變數，告知最佳化`a`小於 5。 同樣地，這是編譯器的承諾。 如果`a`實際上為 6 此時程式中，則之後編譯器最佳化程式的行為可能不會預期。 `__assume` 是 switch 陳述式及/或條件運算式之前最有用。

有一些限制`__assume`。 首先，例如`__restrict`它只是建議，因此編譯器是免費忽略它。 此外，`__assume`目前僅適用於針對常數變數的差異。 它無法散佈符號式不等比較，例如 assume(a < b)。

## <a name="intrinsic-support"></a>內建支援

內建函式是函式呼叫編譯器有內建函式呼叫、 的知識，而不是文件庫中呼叫函式，它會發出該函式的程式碼。 標頭檔\<intrin.h > 包含所有可用的內建函式的每個支援的硬體平台。

內建函式會讓程式設計師能夠深入程式碼而不需要使用組件。 有幾個好處，若要使用內建函式：

- 您的程式碼是可攜性。 數個內建函式可在多重 CPU 架構。

- 您的程式碼較容易閱讀，因為程式碼仍會撰寫 C/c + +。

- 您的程式碼取得編譯器最佳化的好處。 因為編譯器變得更好的可改善的內建函式的程式碼產生。

如需詳細資訊，請參閱 <<c0> [ 編譯器內建](../../intrinsics/compiler-intrinsics.md)。

## <a name="exceptions"></a>例外狀況

效能與使用例外狀況相關聯的叫用。 使用從執行特定的最佳化阻礙編譯器的 try 區塊時，會介紹一些限制。 在 x86 上沒有其他的效能降低情形的平台會嘗試因為必須在程式碼執行期間產生的其他狀態資訊的區塊。 在 64 位元平台上嘗試區塊不會降低效能，最多，但之後擲回例外狀況，尋找處理常式，以及回溯堆疊程序可能會耗費資源。

因此，建議您避免將不會真的不需要它的程式碼中引入 try/catch 區塊。 如果您必須使用例外狀況，請盡可能使用同步例外狀況。 如需詳細資訊，請參閱 [Structured Exception Handling (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)。

最後，會擲回例外的情形的例外狀況。 使用一般的控制流程的例外狀況可能會讓效能會受到影響。

## <a name="see-also"></a>另請參閱

- [最佳化程式碼](../../build/reference/optimizing-your-code.md)
