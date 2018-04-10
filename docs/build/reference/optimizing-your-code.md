---
title: 最佳化程式碼 |Microsoft 文件
ms.custom: ''
ms.date: 12/28/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- performance, optimizing code
- optimization
- cl.exe compiler, performance
- optimization, C++ code
- code, optimizing
- performance, compiler
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4306f825b9925dbdcdc994d287a2c4287ea7bfc2
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="optimizing-your-code"></a>最佳化程式碼

藉由最佳化可執行檔，可讓您快速的執行速度和小的程式碼大小之間取得平衡。 本主題會討論一些可協助您最佳化程式碼的 Visual c + + 提供的機制。

## <a name="language-features"></a>語言功能

下列主題說明的某些最佳化功能，在 C/c + + 語言中。

[最佳化 Pragma 和關鍵字](../../build/reference/optimization-pragmas-and-keywords.md)  
關鍵字和 pragma，您可以使用程式碼中以改善效能的清單。

[依分類排列的編譯器選項](../../build/reference/compiler-options-listed-by-category.md)  
一份**/O**編譯器選項會明確影響執行速度或程式碼大小。

[右值參考宣告子：&&](../../cpp/rvalue-reference-declarator-amp-amp.md)  
右值參考支援實作*移動語意*。 如果移動語意可用於實作樣板程式庫，使用這些範本的應用程式的效能可大幅改善。

### <a name="the-optimize-pragma"></a>最佳化 pragma

如果最佳化的段程式碼會導致錯誤或速度變慢，您可以使用[最佳化](../../preprocessor/optimize.md)pragma，來關閉該區段的最佳化。

將兩個 pragma，之間的程式碼，如下所示：

```cpp
#pragma optimize("", off)
// some code here
#pragma optimize("", on)
```

## <a name="programming-practices"></a>程式設計做法

當您編譯程式碼最佳化的情況，可能會注意到額外的警告訊息。 因為有些警告只與最佳化程式碼，就會發生此行為。 如果您注意這些警告，您可以避免許多最佳化問題。

矛盾，最佳化的程式速度可能會導致執行速度變慢的程式碼。 這是因為某些速度最佳化作業增加的程式碼大小。 例如，內嵌函式消除函式呼叫的額外負荷。 不過，內嵌太多程式碼可能會使您的程式大虛擬記憶體分頁的數目錯誤會增加。 因此，排除函式呼叫中所獲得的速度可能會遺失記憶體交換。

下列主題討論的良好程式設計作法。

[改善時間關鍵程式碼的秘訣](../../build/reference/tips-for-improving-time-critical-code.md)  
進一步編碼技術，可產生較佳的效能。 本主題建議編碼可協助您確保程式碼的時間很重要的部分令人滿意的技術。

[最佳化最佳做法](../../build/reference/optimization-best-practices.md)  
提供有關如何最佳化您的應用程式以最佳的一般指導方針。

## <a name="debugging-optimized-code"></a>偵錯最佳化程式碼

因為最佳化可能會變更由編譯器所建立的程式碼，我們建議您偵錯應用程式，並測量其效能，並接著最佳化您的程式碼。

下列主題提供有關如何偵錯的基本資訊。

- [Visual Studio 偵錯](/visualstudio/debugger/debugging-in-visual-studio)

- [建立發行組建時的常見問題](../../build/reference/common-problems-when-creating-a-release-build.md)

下列主題提供有關如何偵錯更進階的資訊。

- [如何：偵錯最佳化程式碼](/visualstudio/debugger/how-to-debug-optimized-code)

- [浮點數會失去精確度的原因](../../build/reference/why-floating-point-numbers-may-lose-precision.md)

下列主題提供有關如何建立、 載入，及執行您的程式碼最佳化的資訊。

- [改善編譯器輸送量](../../build/reference/improving-compiler-throughput.md)

- [使用不帶 () 的函式名稱不會產生程式碼](../../build/reference/using-function-name-without-parens-produces-no-code.md)

- [最佳化內嵌組譯碼](../../assembler/inline/optimizing-inline-assembly.md)

- [指定 ATL 專案的編譯器最佳化](../../atl/reference/specifying-compiler-optimization-for-an-atl-project.md)

- [若要改善用戶端應用程式的效能，載入時應該使用何項最佳化技術？](../../build/dll-frequently-asked-questions.md#mfc_optimization)

## <a name="see-also"></a>另請參閱

[C/C++ 建置參考](../../build/reference/c-cpp-building-reference.md)  
