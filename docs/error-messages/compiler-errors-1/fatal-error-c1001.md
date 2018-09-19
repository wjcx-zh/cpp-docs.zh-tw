---
title: 嚴重錯誤 C1001 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1001
dev_langs:
- C++
helpviewer_keywords:
- C1001
ms.assetid: 5736cdb3-22c8-4fad-aa85-d5e0d2b232f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6363694dbd7f1a7ebfcd58cad030dfecf7f38397
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098195"
---
# <a name="fatal-error-c1001"></a>嚴重錯誤 C1001

> 內部編譯器 ERROR(compiler file *file*, line *number*)

編譯器無法剖析中產生正確的程式碼建構，通常都是因為特定運算式和最佳化選項或發生問題的組合。 如果列出的編譯器檔案具有 utc 或 C2 路徑區段，它可能是最佳化時發生錯誤。 如果檔案具有 cxxfe 或 c1xx 的路徑區段或 msc1.cpp，它可能是剖析器錯誤。 如果名為的檔案是 cl.exe，沒有任何其他資訊可用。

您通常可以移除一或多個最佳化選項，以修正未最佳化的問題。 若要判斷哪一個選項是錯誤，請移除選項一的時間與重新編譯之前的錯誤訊息就會消失。 選項最常負責[/Og （全域最佳化）](../../build/reference/og-global-optimizations.md)並[/Oi （產生內建函式）](../../build/reference/oi-generate-intrinsic-functions.md)。 一旦您判斷哪一個最佳化選項負責，您可以停用它使用發生錯誤的函式周圍[最佳化](../../preprocessor/optimize.md)pragma，並繼續使用模組的其餘部分的選項。 如需有關最佳化選項的詳細資訊，請參閱[最佳化的最佳做法](../../build/reference/optimization-best-practices.md)。

如果未對錯誤負責的最佳化，請嘗試重新撰寫的行，其中會報告錯誤或幾行程式碼周圍的那一行。 若要查看程式碼編譯器所看到的是它在前置處理之後的方式，您可以使用[/P （前置處理至檔案）](../../build/reference/p-preprocess-to-a-file.md)選項。

如需有關如何找出錯誤的來源以及如何向 Microsoft 報告編譯器內部錯誤的詳細資訊，請參閱 <<c0> [ 如何回報 Visual c + + 工具組問題](../../how-to-report-a-problem-with-the-visual-cpp-toolset.md)。