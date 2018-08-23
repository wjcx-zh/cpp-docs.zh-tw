---
title: C + + AMP (c + + Accelerated Massive Parallelism) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- C++ AMP (see C++ Accelerated Massive Parallelism)
- C++ Accelerated Massive Parallelism, getting started
ms.assetid: e27824cb-3167-409b-8c3f-a0e476d8f349
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a990acd8f27be476ce35d682a19912dcc85bbeed
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2018
ms.locfileid: "42540972"
---
# <a name="c-amp-c-accelerated-massive-parallelism"></a>C++ AMP (C++ Accelerated Massive Parallelism)
C + + AMP (c + + Accelerated Massive Parallelism) 利用通常是獨立圖形顯示卡上的圖形處理單元 (GPU) 的資料平行硬體來加速您的 c + + 程式碼的執行。 C + + AMP 程式撰寫模型包含多維陣列時，編製索引、 記憶體傳輸和並排顯示的支援。 它也包含數學函式庫。 您可以使用 c + + AMP 語言擴充功能來控制資料如何從 CPU 移至 GPU 和。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[C++ AMP 概觀](../../parallel/amp/cpp-amp-overview.md)|描述 c + + AMP 和數學程式庫的主要功能。|  
|[使用 Lambda、函式物件和限制函式](../../parallel/amp/using-lambdas-function-objects-and-restricted-functions.md)|描述如何使用 lambda 運算式、 函式物件和限制函式在呼叫[parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each)方法。|  
|[使用磚](../../parallel/amp/using-tiles.md)|描述如何使用 tile 來加速您的 c + + AMP 程式碼。|  
|[使用 accelerator 和 accelerator_view 物件](../../parallel/amp/using-accelerator-and-accelerator-view-objects.md)|描述如何使用加速器來自訂您的程式碼在 GPU 上執行。|  
|[在 UWP 應用程式中使用 C++ AMP](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)|描述如何使用 Windows 執行階段類型的通用 Windows 平台 (UWP) 應用程式中使用 c + + AMP。|  
|[圖形 (C++ AMP)](../../parallel/amp/graphics-cpp-amp.md)|描述如何使用 c + + AMP 圖形程式庫。|  
|[逐步解說：矩陣乘法](../../parallel/amp/walkthrough-matrix-multiplication.md)|示範如何使用 c + + AMP 程式碼和 tile 劃分的矩陣相乘。|  
|[逐步解說：偵錯 C++ AMP 應用程式](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)|說明如何建立和偵錯使用平行約化來加總大型整數陣列的應用程式。|  
  
## <a name="reference"></a>參考資料  

[參考 (c + + AMP)](../../parallel/amp/reference/reference-cpp-amp.md)    
[tile_static 關鍵字](../../cpp/tile-static-keyword.md)    
[restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md)  
  
## <a name="other-resources"></a>其他資源  
 
[機器碼部落格中的平行程式設計](http://go.microsoft.com/fwlink/p/?linkid=238472)  
[C + + AMP 範例專案下載](http://go.microsoft.com/fwlink/p/?linkid=248508)  
[使用並行視覺化檢視分析 c + + AMP 程式碼](http://go.microsoft.com/fwlink/p/?linkid=253987&clcid=0x409)