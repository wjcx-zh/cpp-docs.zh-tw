---
title: 最佳化程式碼
ms.date: 05/06/2019
helpviewer_keywords:
- performance, optimizing code
- optimization
- cl.exe compiler, performance
- optimization, C++ code
- code, optimizing
- performance, compiler
ms.openlocfilehash: 00356cf50ca8e50c80e8a1142adf654816490c9b
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078498"
---
# <a name="optimizing-your-code"></a>最佳化程式碼

藉由優化可執行檔，您可以在快速執行速度和小型程式碼大小之間取得平衡。 本主題討論一些 Visual Studio 提供的機制，可協助您優化程式碼。

## <a name="language-features"></a>語言功能

下列主題將說明 C/c + + 語言中的一些優化功能。

[優化 Pragma 和關鍵字](optimization-pragmas-and-keywords.md) \
您可以在程式碼中用來改善效能的關鍵字和 pragma 清單。

[依分類列出的編譯器選項](reference/compiler-options-listed-by-category.md) \
**/O**編譯器選項的清單，其會特別影響執行速度或程式碼大小。

[右值參考宣告子：  &&](../cpp/rvalue-reference-declarator-amp-amp.md) \
右值參考支援*move 語義*的執行。 如果使用 move 語義來執行範本庫，使用這些範本的應用程式效能可能會大幅改善。

### <a name="the-optimize-pragma"></a>Optimize pragma

如果程式碼的優化區段導致錯誤或速度變慢，您可以使用[optimize](../preprocessor/optimize.md) pragma 來關閉該區段的優化。

將程式碼括在兩個 pragma 之間，如下所示：

```cpp
#pragma optimize("", off)
// some code here
#pragma optimize("", on)
```

## <a name="programming-practices"></a>程式設計實務

當您使用優化編譯器代碼時，您可能會發現額外的警告訊息。 這是預期的行為，因為有些警告只與優化的程式碼有關。 如果您注意這些警告，可以避免許多優化問題。

卻又顯得，將程式優化以加快速度可能會使程式碼的執行速度變慢。 這是因為對速度增加程式碼大小的某些優化。 例如，內嵌函數可免除函式呼叫的額外負荷。 不過，內嵌太多程式碼可能會使您的程式變得很大，以致虛擬記憶體分頁錯誤數目增加。 因此，從排除函式呼叫取得的速度可能會遺失到記憶體交換。

下列主題將討論良好的程式設計作法。

[改善時間關鍵程式碼的秘訣](tips-for-improving-time-critical-code.md) \
較佳的程式碼撰寫技巧可以產生較佳的效能。 本主題建議的程式碼撰寫技巧，可協助您確保程式碼的時間緊迫部分執行得非常滿意。

[優化最佳作法](optimization-best-practices.md) \
提供如何最佳地優化應用程式的一般指導方針。

## <a name="debugging-optimized-code"></a>優化程式碼的偵錯工具

因為優化可能會變更編譯器所建立的程式碼，所以我們建議您先對應用程式進行 debug 並測量其效能，然後將您的程式碼優化。

下列主題提供如何偵測發行組建的相關資訊。

- [Visual Studio 偵錯](/visualstudio/debugger/debugging-in-visual-studio)

- [如何：偵錯工具優化程式碼](/visualstudio/debugger/how-to-debug-optimized-code)

- [浮點數會失去精確度的原因](why-floating-point-numbers-may-lose-precision.md)

下列主題提供如何優化建立、載入和執行程式碼的相關資訊。

- [改善編譯器處理量](improving-compiler-throughput.md)

- [使用不帶 () 的函式名稱不會產生程式碼](using-function-name-without-parens-produces-no-code.md)

- [最佳化內嵌組譯碼](../assembler/inline/optimizing-inline-assembly.md)

- [指定 ATL 專案的編譯器最佳化](../atl/reference/specifying-compiler-optimization-for-an-atl-project.md)

- [載入時，我應該使用何項最佳化技術來改善用戶端應用程式的效能？](../build/dll-frequently-asked-questions.md#mfc_optimization)

## <a name="in-this-section"></a>本節內容

[優化 Pragma 和關鍵字](optimization-pragmas-and-keywords.md) \
[改善編譯器輸送量](improving-compiler-throughput.md) \
[浮點數可能失去精確度的原因](why-floating-point-numbers-may-lose-precision.md) \
[IEEE 浮點標記法](ieee-floating-point-representation.md) \
[改善時間關鍵程式碼的秘訣](tips-for-improving-time-critical-code.md) \
[使用不含（）的函數名稱不會產生任何程式碼](using-function-name-without-parens-produces-no-code.md) \
[優化最佳作法](optimization-best-practices.md) \
[特性指引優化](profile-guided-optimizations.md) \
[特性指引優化的環境變數](environment-variables-for-profile-guided-optimizations.md) \
[PgoAutoSweep](pgoautosweep.md) \
[pgomgr](pgomgr.md) \
[pgosweep](pgosweep.md) \
[如何：將多個 PGO 設定檔合併至單一設定檔](how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)

## <a name="see-also"></a>請參閱

[C/C++ 建置參考](reference/c-cpp-building-reference.md)
