---
title: "嚴重錯誤 C1001 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1001
dev_langs:
- C++
helpviewer_keywords:
- C1001
ms.assetid: 5736cdb3-22c8-4fad-aa85-d5e0d2b232f4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4a72a99e566474145857e265edde548ebf38e180
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1001"></a>嚴重錯誤 C1001

> 內部編譯器 ERROR(compiler file *file*, line *number*)  
  
編譯器無法產生的建構，通常都是因為特定的運算式和最佳化選項或發生問題的組合的正確程式碼剖析。 如果列出編譯器檔案的 utc 或 C2 路徑區段，它可能是最佳化時發生錯誤。 如果檔案已經在 cxxfe 或 c1xx 路徑區段中，或 msc1.cpp，可能是剖析器錯誤。 如果 cl.exe 名為的檔案，沒有其他資訊可用。  

您經常可以移除一或多個最佳化選項，以修正最佳化問題。 若要判斷哪一個選項是錯誤之前的錯誤訊息會隨即消失,，在時間並重新編譯移除其中一個選項。 選項最常造成[/Og （全域最佳化）](../../build/reference/og-global-optimizations.md)和[/Oi （產生內建函式）](../../build/reference/oi-generate-intrinsic-functions.md)。 一旦您判斷哪個最佳化選項，您可以停用它使用發生錯誤的函式[最佳化](../../preprocessor/optimize.md)pragma，並繼續使用模組的其餘部分的選項。 如需最佳化選項的詳細資訊，請參閱[最佳化最佳作法](../../build/reference/optimization-best-practices.md)。

如果最佳化不負責錯誤，請再試一次重寫的此行報告此錯誤的位置或幾行程式碼。 若要查看程式碼編譯器則會在前置處理之後查看它的方式，您可以使用[/P （前置處理至檔案）](../../build/reference/p-preprocess-to-a-file.md)選項。

如需有關如何找出錯誤的來源以及如何向 Microsoft 報告內部編譯器錯誤的詳細資訊，請參閱[如何報告問題，以搭配 Visual c + + 工具組](../../how-to-report-a-problem-with-the-visual-cpp-toolset.md)。