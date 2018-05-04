---
title: 最佳化最佳作法 |Microsoft 文件
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
ms.openlocfilehash: 4e869a12635117f37f32fad3dcfdd38ed45d401e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="optimization-best-practices"></a>最佳化最佳作法
本文件說明 Visual c + + 最佳化的一些最佳作法。 我們將討論下列主題：  
  
-   編譯器和連結器選項  
  
    -   特性指引最佳化  
  
    -   應該使用的最佳化層級？  
  
    -   浮點參數  
  
-   最佳化 Declspecs  
  
-   最佳化 Pragma  
  
-   __restrict 和\__assume  
  
-   內建支援  
  
-   例外狀況  
  
## <a name="compiler-and-linker-options"></a>編譯器和連結器選項  
  
### <a name="profile-guided-optimization"></a>特性指引最佳化  
 Visual c + + 支援特性指引最佳化 (PGO)。 此最佳化使用從過去的版本已經過檢測的應用程式執行的分析資料來更新應用程式最佳化的磁碟機。 使用 PGO 非常耗時，因此，可能不會有每位開發人員使用，但我們建議使用 PGO 最終發行版本的產品。 如需詳細資訊，請參閱[特性指引最佳化](../../build/reference/profile-guided-optimizations.md)。  
  
 此外，整個程式最佳化 （也稱為連結時間產生程式碼） 和 **/O1**和 **/O2**已經過改良最佳化。 一般情況下，使用其中一個選項編譯的應用程式將會較快，使用舊版的編譯器編譯的相同應用程式。  
  
 如需詳細資訊，請參閱[/GL （整個程式最佳化）](../../build/reference/gl-whole-program-optimization.md)和[/O1、 /O2 （最小化的大小、 最大化的速度）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)。  
  
### <a name="which-level-of-optimization-should-i-use"></a>應該使用的最佳化層級？  
 如果可能的話，應該使用特性指引最佳化進行編譯最終版本組建。 如果不是可以建置使用 PGO 時，無論由於不足，無法執行已檢測的組建，或無法存取案例的基礎結構，我們建議使用整個程式最佳化建置。  
  
 **/Gy**參數也是非常有用。 它會產生個別 COMDAT，每個函數提供連結器更大的彈性時移除未參考的 Comdat 和 COMDAT 摺疊。 使用的唯一缺點 **/Gy**是它可以有些許影響建置時間。 因此，通常建議使用它。 如需詳細資訊，請參閱 [/Gy (啟用函式階層連結)](../../build/reference/gy-enable-function-level-linking.md)。  
  
 在 64 位元環境中的連結，建議使用 **/opt: ref、 ICF**連結器選項和 32 位元環境中 **/opt: ref**建議。 如需詳細資訊，請參閱[/editandcontinue （最佳化）](../../build/reference/opt-optimizations.md)。  
  
 此外，強烈建議產生偵錯符號，即使是使用最佳化的發行組建。 它不會影響所產生的程式碼，而它使得需要是很容易進行偵錯您的應用程式。  
  
### <a name="floating-point-switches"></a>浮點參數  
 **/Op**編譯器選項已被移除，並已新增下列四個浮點數最佳化處理的編譯器選項：  
  
|||  
|-|-|  
|**/fp： 精確**|這是預設建議，並應該在大部分情況下使用。|  
|**/fp: fast**|如果效能是責，例如在遊戲的建議。 這會導致最快的效能。|  
|**/fp: strict**|如果建議精確的浮點例外狀況和 IEEE 想要使用的行為。 這會導致最慢的效能。|  
|**/fp: except [-]**|可以用於搭配 **/fp: strict**或 **/fp： 精確**，但不是 **/fp: fast**。|  
  
 如需詳細資訊，請參閱 [/fp (指定浮點行為)](../../build/reference/fp-specify-floating-point-behavior.md)。  
  
## <a name="optimization-declspecs"></a>最佳化 Declspecs  
 這一節我們將探討兩個 declspecs 可以在程式中用來幫助效能：`__declspec(restrict)`和`__declspec(noalias)`。  
  
 `restrict` Declspec 只能套用至傳回指標，例如的函式宣告 `__declspec(restrict) void *malloc(size_t size);`  
  
 `restrict` Declspec 適用於函式會傳回非別名的指標。 這個關鍵字用 C 執行階段程式庫實作的`malloc`因為它永遠不會傳回已在使用目前程式中 （除非您執行的作業不合法，例如使用後釋放的記憶體） 的指標值。  
  
 `restrict` Declspec 可讓編譯器執行編譯器最佳化的詳細資訊。 其中一個最複雜的項目，讓編譯器能夠判斷哪些指標別名其他指標，並且大量使用這項資訊可協助編譯器。  
  
 很值得，這是不是編譯器會驗證編譯器的承諾。 如果您的程式會使用此`restrict`declspec 不當，您的程式可能有不正確的行為。  
  
 如需詳細資訊，請參閱[限制](../../cpp/restrict.md)。  
  
 `noalias` Declspec 也只會套用至函式，並指出函數是否為半純虛擬函式。 半純虛擬函式是指參考或修改 [區域變數]、 引數，而且第一層間接取值的引數。 此 declspec 可保證一定會給編譯器，以及如果函式會參考全域變數，或第二層間接取值的指標引數，則編譯器可能會產生程式碼，分行符號應用程式。  
  
 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md)。  
  
## <a name="optimization-pragmas"></a>最佳化 Pragma  
 另外還有數個實用的 pragma，可協助最佳化程式碼。 我們將討論的第一個是`#pragma optimize`:  
  
```  
#pragma optimize("{opt-list}", on | off)  
```  
  
 這個 pragma 可讓您指定的最佳化層級設定函式的函式為基礎。 這是理想的罕見時指定的函式以最佳化編譯應用程式損毀。 您可以使用該將單一函式的最佳化關閉：  
  
```  
#pragma optimize("", off)  
int myFunc() {...}  
#pragma optimize("", on)  
```  
  
 如需詳細資訊，請參閱[最佳化](../../preprocessor/optimize.md)。  
  
 內嵌是其中一個最重要的最佳化，編譯器會執行，並在這裡我們將討論一些可修改此行為的 pragma。  
  
 `#pragma inline_recursion` 適用於指定您想要能夠使用內嵌的遞迴呼叫應用程式。 預設為關閉。 淺層遞迴的小型函式，您可開啟此選項。 如需詳細資訊，請參閱[inline_recursion](../../preprocessor/inline-recursion.md)。  
  
 另一個有用的 pragma，來限制深度內嵌是`#pragma inline_depth`。 這是在您正嘗試程式或函式的大小限制的情況下，通常很有用。 如需詳細資訊，請參閱[inline_depth](../../preprocessor/inline-depth.md)。  
  
## <a name="restrict-and-assume"></a>__restrict 和\__assume  
 有幾個有助於提高效能的 Visual c + + 中的關鍵字： [__restrict](../../cpp/extension-restrict.md)和[__assume](../../intrinsics/assume.md)。  
  
 首先，您應該注意，`__restrict`和`__declspec(restrict)`是兩個不同的項目。 雖然它們有些許相關，其語意會有不同。 `__restrict` 已有類型限定詞，like`const`或`volatile`，但專門用於指標類型。  
  
 修改與指標`__restrict`稱為 *__restrict 指標*。 __Restrict 指標是只能透過存取指標\_（_r） 指標。 換句話說，另一個指標無法用來存取資料所指\_（_r） 指標。  
  
 `__restrict` 可以是功能強大的工具，Visual c + + 最佳化工具，但使用十分小心。 如果使用不當，最佳化工具可能會執行會破壞您的應用程式的最佳化。  
  
 `__restrict`關鍵字取代 **/Oa**從舊版切換。  
  
 與`__assume`，開發人員可以告訴編譯器將某個變數的值的相關假設。  
  
 例如`__assume(a < 5);`，告知最佳化，在該變數的程式碼行`a`小於 5。 同樣地，這是編譯器的承諾。 如果`a`實際上為 6 此時在程式中，然後之後編譯器最佳化程式的行為可能不會預期。 `__assume` 便最有用之前 switch 陳述式及/或條件運算式。  
  
 有一些限制`__assume`。 首先，例如`__restrict`，它是只是建議，所以編譯器會釋放將它忽略。 此外，`__assume`目前只適用於針對常數變數不等式。 它無法散佈符號式不等比較，例如 assume(a < b)。  
  
## <a name="intrinsic-support"></a>內建支援  
 內建函式是函式呼叫編譯器有內建函式呼叫的相關知識，而不是文件庫中呼叫函式，它會發出程式碼，該函式。 位於 <Installation_Directory>\VC\include\intrin.h 中的標頭檔 intrin.h 包含了每一個支援平台 (x86、x64 和 ARM) 的所有可用內建。  
  
 內建函式可讓程式設計人員進入深度程式碼而不必使用組件。 有使用內建的幾個好處：  
  
1.  程式碼就更容易移植。 數個內建函式無法在多個 CPU 架構。  
  
2.  您的程式碼很容易閱讀，因為仍 C/c + + 撰寫的程式碼。  
  
3.  您的程式碼取得編譯器最佳化的好處。 因為編譯器變得更好，可改善內建函式的程式碼產生。  
  
 如需詳細資訊，請參閱[編譯器內建](../../intrinsics/compiler-intrinsics.md)。  
  
## <a name="exceptions"></a>例外狀況  
 效能與使用例外狀況相關聯的叫用。 使用編譯器禁止執行某些最佳化功能的 try 區塊時，會產生一些限制。 在 x86 上沒有從其他的效能降低的平台會 try 區塊，因為必須在程式碼執行期間產生的其他狀態資訊。 在 64 位元平台上再次嘗試區塊不會降低效能，但一旦擲回例外狀況後，尋找處理常式，並回溯堆疊的程序可能會耗費資源。  
  
 因此，建議您避免 try/catch 區塊不會真的不需要它的程式碼。 如果您必須使用例外狀況，請盡可能使用同步例外狀況。 如需詳細資訊，請參閱 [Structured Exception Handling (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)。  
  
 最後，會擲回例外狀況的例外的情形。 一般的控制流程中使用例外狀況可能會讓效能變差。  
  
## <a name="see-also"></a>另請參閱  
 [最佳化程式碼](../../build/reference/optimizing-your-code.md)