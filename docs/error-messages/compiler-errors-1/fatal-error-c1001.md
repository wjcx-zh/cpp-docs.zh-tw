---
title: 嚴重錯誤 C1001
ms.date: 11/04/2016
f1_keywords:
- C1001
helpviewer_keywords:
- C1001
ms.assetid: 5736cdb3-22c8-4fad-aa85-d5e0d2b232f4
ms.openlocfilehash: e1255578883c8d2bc278184a02575a0a51ed9b6c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204954"
---
# <a name="fatal-error-c1001"></a>嚴重錯誤 C1001

> 編譯器內部錯誤（編譯器檔案*檔案，* 行*號*）

編譯器無法產生結構的正確程式碼，通常是因為特定運算式和優化選項的組合，或剖析中的問題所造成。 如果列出的編譯器檔案有 utc 或 C2 路徑區段，則可能是優化錯誤。 如果檔案具有 cxxfe 或 c1xx 而防護路徑區段，或為 msc1.cpp .cpp，可能是剖析器錯誤。 如果名為的檔案是 cl .exe，則沒有其他可用的資訊。

您通常可以藉由移除一或多個優化選項來修正優化問題。 若要判斷哪一個選項處於錯誤狀態，請一次移除一個選項，並重新編譯，直到錯誤訊息消失為止。 最常負責的選項是[/og （全域優化）](../../build/reference/og-global-optimizations.md)和[/Oi （產生內建函式）](../../build/reference/oi-generate-intrinsic-functions.md)。 一旦您決定要負責哪一個優化選項之後，就可以使用[optimize](../../preprocessor/optimize.md) pragma 在發生錯誤的函式中停用它，並繼續在其餘的模組中使用此選項。 如需優化選項的詳細資訊，請參閱[優化最佳作法](../../build/optimization-best-practices.md)。

如果優化不負責錯誤，請嘗試重寫回報錯誤的行，或是該行周圍的幾行程式碼。 若要查看程式碼在前置處理之後，編譯器所看到的程式碼，您可以使用[/p （](../../build/reference/p-preprocess-to-a-file.md)前置處理至檔案）選項。

如需如何隔離錯誤來源以及如何向 Microsoft 回報內部編譯器錯誤的詳細資訊，請參閱[如何回報視覺效果C++工具](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md)組的問題。
