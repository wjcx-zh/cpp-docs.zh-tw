---
title: C++ AMP (C++ Accelerated Massive Parallelism)
ms.date: 11/04/2016
helpviewer_keywords:
- C++ AMP (see C++ Accelerated Massive Parallelism)
- C++ Accelerated Massive Parallelism, getting started
ms.assetid: e27824cb-3167-409b-8c3f-a0e476d8f349
ms.openlocfilehash: 516b69a0371ceb9365e79d5465879711289076c0
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404856"
---
# <a name="c-amp-c-accelerated-massive-parallelism"></a>C++ AMP (C++ Accelerated Massive Parallelism)

C++ AMP （C++ Accelerated Massive Parallelism）藉由在離散的圖形配接器上利用通常呈現為圖形處理器（GPU）的資料平行硬體，加速 c + + 程式碼的執行。 C++ AMP 程式設計模型包含多維陣列、編制索引、記憶體傳輸和並排平的支援。 它也包含數學函式程式庫。 您可以使用 C++ AMP 的語言延伸模組來控制如何將資料從 CPU 移至 GPU 並返回。

## <a name="related-topics"></a>相關主題

|Title|描述|
|-----------|-----------------|
|[C++ AMP 總覽](../../parallel/amp/cpp-amp-overview.md)|說明 C++ AMP 和數學程式庫的主要功能。|
|[使用 Lambda、函數物件和限制函式](../../parallel/amp/using-lambdas-function-objects-and-restricted-functions.md)|描述如何在對[parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each)方法的呼叫中使用 lambda 運算式、函式物件和限制函式。|
|[使用磚](../../parallel/amp/using-tiles.md)|說明如何使用磚來加速 C++ AMP 程式碼。|
|[使用快速鍵和 accelerator_view 物件](../../parallel/amp/using-accelerator-and-accelerator-view-objects.md)|說明如何使用加速器自訂 GPU 上的程式碼執行。|
|[在 UWP 應用程式中使用 C++ AMP](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)|說明如何在使用 Windows 執行階段類型的通用 Windows 平臺（UWP）應用程式中使用 C++ AMP。|
|[圖形 (C++ AMP)](../../parallel/amp/graphics-cpp-amp.md)|描述如何使用 C++ AMP 圖形庫。|
|[逐步解說：矩陣乘法](../../parallel/amp/walkthrough-matrix-multiplication.md)|示範使用 C++ AMP 程式碼和並排顯示的矩陣乘法。|
|[逐步解說： C++ AMP 應用程式的偵錯工具](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)|說明如何建立和偵測使用平行縮減的應用程式，以加總大型整數陣列。|

## <a name="reference"></a>參考資料

[參考 (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)<br/>
[tile_static 關鍵字](../../cpp/tile-static-keyword.md)<br/>
[restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md)

## <a name="other-resources"></a>其他資源

[原生程式碼的平行程式設計 Blog](https://go.microsoft.com/fwlink/p/?linkid=238472)<br/>
[C++ AMP 下載的範例專案](https://go.microsoft.com/fwlink/p/?linkid=248508)<br/>
[使用並行視覺化來分析 C++ AMP 程式碼](/archive/blogs/nativeconcurrency/analyzing-c-amp-code-with-the-concurrency-visualizer)
