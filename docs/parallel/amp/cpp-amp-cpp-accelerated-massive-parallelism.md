---
title: C++ AMP (C++ Accelerated Massive Parallelism)
ms.date: 11/04/2016
helpviewer_keywords:
- C++ AMP (see C++ Accelerated Massive Parallelism)
- C++ Accelerated Massive Parallelism, getting started
ms.assetid: e27824cb-3167-409b-8c3f-a0e476d8f349
ms.openlocfilehash: 243c476b6536278eb09b26b24becb65276d6e48a
ms.sourcegitcommit: 093f49b8b69daf86661adc125b1d2d7b1f0e0650
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2020
ms.locfileid: "89427630"
---
# <a name="c-amp-c-accelerated-massive-parallelism"></a>C++ AMP (C++ Accelerated Massive Parallelism)

C++ AMP (C++ Accelerated Massive Parallelism) 會利用通常以圖形處理單位呈現的資料平行硬體，來加速 c + + 程式碼的執行，而在離散的圖形配接器上， (GPU) 。 C++ AMP 程式設計模型包含多維度陣列、索引編制、記憶體傳輸和圖格的支援。 它也包含數學函數程式庫。 您可以使用 C++ AMP 語言延伸模組，來控制如何將資料從 CPU 移回 GPU。

## <a name="related-topics"></a>[相關主題]

|Title|說明|
|-----------|-----------------|
|[C++ AMP 總覽](../../parallel/amp/cpp-amp-overview.md)|描述 C++ AMP 和數學程式庫的主要功能。|
|[使用 Lambda、函式物件和限制函數](../../parallel/amp/using-lambdas-function-objects-and-restricted-functions.md)|描述如何在呼叫 [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) 方法時，使用 lambda 運算式、函式物件和限制函數。|
|[使用磚](../../parallel/amp/using-tiles.md)|說明如何使用磚來加速 C++ AMP 程式碼。|
|[使用快速鍵和 accelerator_view 物件](../../parallel/amp/using-accelerator-and-accelerator-view-objects.md)|說明如何使用快速鍵自訂在 GPU 上執行程式碼。|
|[在 UWP 應用程式中使用 C++ AMP](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)|說明如何使用通用 Windows 平臺 (UWP) 使用 Windows 執行階段類型的應用程式中的 C++ AMP。|
|[圖形 (C++ AMP)](../../parallel/amp/graphics-cpp-amp.md)|說明如何使用 C++ AMP 圖形程式庫。|
|[逐步解說：矩陣乘法](../../parallel/amp/walkthrough-matrix-multiplication.md)|示範使用 C++ AMP 程式碼和並排顯示的矩陣乘法。|
|[逐步解說： C++ AMP 應用程式的偵錯工具](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)|說明如何建立及偵測使用平行減少來加總大型整數陣列的應用程式。|

## <a name="reference"></a>參考

[參考 (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)<br/>
[tile_static 關鍵字](../../cpp/tile-static-keyword.md)<br/>
[restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md)

## <a name="other-resources"></a>其他資源

[原生程式碼中的平行程式設計](/archive/blogs/nativeconcurrency/)<br/>
[C++ AMP 下載的範例專案](/archive/blogs/nativeconcurrency/c-amp-sample-projects-for-download)<br/>
[使用平行存取視覺化程式分析 C++ AMP 程式碼](/archive/blogs/nativeconcurrency/analyzing-c-amp-code-with-the-concurrency-visualizer)
