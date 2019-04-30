---
title: C++ AMP (C++ Accelerated Massive Parallelism)
ms.date: 11/04/2016
helpviewer_keywords:
- C++ AMP (see C++ Accelerated Massive Parallelism)
- C++ Accelerated Massive Parallelism, getting started
ms.assetid: e27824cb-3167-409b-8c3f-a0e476d8f349
ms.openlocfilehash: f8ac71023f66868a66fb8c54a5e86678225378a1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400691"
---
# <a name="c-amp-c-accelerated-massive-parallelism"></a>C++ AMP (C++ Accelerated Massive Parallelism)

C++P (C++ Accelerated Massive Parallelism) 加速的執行程式C++利用通常是圖形處理單元 (GPU) 在獨立圖形顯示卡上的資料平行硬體的程式碼。 C++ AMP 程式撰寫模型包含多維陣列時，編製索引、 記憶體傳輸和並排顯示的支援。 它也包含數學函式庫。 您可以使用C++AMP 語言擴充功能，來控制資料如何從 CPU 移至 GPU 和上一步。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[C++ AMP 概觀](../../parallel/amp/cpp-amp-overview.md)|說明的重要功能的C++AMP 和數學程式庫。|
|[使用 Lambda、函式物件和限制函式](../../parallel/amp/using-lambdas-function-objects-and-restricted-functions.md)|描述如何使用 lambda 運算式、 函式物件和限制函式在呼叫[parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each)方法。|
|[使用磚](../../parallel/amp/using-tiles.md)|描述如何使用 tile 來加速您C++AMP 程式碼。|
|[使用 accelerator 和 accelerator_view 物件](../../parallel/amp/using-accelerator-and-accelerator-view-objects.md)|描述如何使用加速器來自訂您的程式碼在 GPU 上執行。|
|[在 UWP 應用程式中使用 C++ AMP](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)|描述如何使用C++使用 Windows 執行階段類型的通用 Windows 平台 (UWP) 應用程式中的 P。|
|[圖形 (C++ AMP)](../../parallel/amp/graphics-cpp-amp.md)|描述如何使用C++AMP 圖形程式庫。|
|[逐步解說：矩陣乘法](../../parallel/amp/walkthrough-matrix-multiplication.md)|示範矩陣乘法使用C++AMP 程式碼和並排顯示。|
|[逐步解說：針對 C++ AMP 應用程式進行偵錯](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)|說明如何建立和偵錯使用平行約化來加總大型整數陣列的應用程式。|

## <a name="reference"></a>參考資料

[參考 (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)<br/>
[tile_static 關鍵字](../../cpp/tile-static-keyword.md)<br/>
[restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md)

## <a name="other-resources"></a>其他資源

[機器碼部落格中的平行程式設計](http://go.microsoft.com/fwlink/p/?linkid=238472)<br/>
[C++AMP 範例專案下載](http://go.microsoft.com/fwlink/p/?linkid=248508)<br/>
[分析C++AMP 程式碼，使用並行視覺化檢視](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/03/09/analyzing-c-amp-code-with-the-concurrency-visualizer/)