---
title: "C++ AMP (C++ Accelerated Massive Parallelism) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++ Accelerated Massive Parallelism, 使用者入門"
  - "C++ AMP (請參閱 C++ Accelerated Massive Parallelism)"
ms.assetid: e27824cb-3167-409b-8c3f-a0e476d8f349
caps.latest.revision: 22
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C++ AMP (C++ Accelerated Massive Parallelism)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

C\+\+ AMP \(C\+\+ Accelerated Massive Parallelism\) 利用通常是獨立圖形顯示卡上的圖形處理器 \(GPU\) 等資料平行硬體來加速您的 C\+\+ 程式碼的執行。  C\+\+ AMP 程式撰寫模型包含對多維陣列、索引、記憶體傳輸和並排的支援。  此外，它還包含數學函式庫。  您可以使用 C\+\+ AMP 語言擴充來控制資料在 CPU 和 GPU 之間的移動。  
  
## 相關主題  
  
|標題|描述|  
|--------|--------|  
|[C\+\+ AMP 概觀](../../parallel/amp/cpp-amp-overview.md)|描述 C\+\+ AMP 和數學程式庫主要功能。|  
|[使用 Lambda、函式物件和限制函式](../../parallel/amp/using-lambdas-function-objects-and-restricted-functions.md)|說明如何使用 Lambda 運算式、函式物件，以及呼叫 [parallel\_for\_each](../Topic/parallel_for_each%20Function%20\(C++%20AMP\).md) 方法時受限制的函式。|  
|[使用磚](../../parallel/amp/using-tiles.md)|說明如何使用 Tile 來加速您的 C\+\+ AMP 程式碼。|  
|[使用 accelerator 和 accelerator\_view 物件](../../parallel/amp/using-accelerator-and-accelerator-view-objects.md)|說明如何使用加速器來自訂程式碼在 GPU 上的執行。|  
|[在 Windows 市集應用程式中使用 C\+\+ AMP](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)|說明如何在使用 Windows 執行階段類型的 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式中使用 C\+\+ AMP。|  
|[圖形 \(C\+\+ AMP\)](../../parallel/amp/graphics-cpp-amp.md)|說明如何使用 C\+\+ AMP 圖形程式庫。|  
|[逐步解說：矩陣乘法](../../parallel/amp/walkthrough-matrix-multiplication.md)|使用 C\+\+ AMP 程式碼和 Tile 劃分示範矩陣乘法。|  
|[逐步解說：偵錯 C\+\+ AMP 應用程式](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)|說明如何建立和偵錯使用平行約化來加總大型整數陣列的應用程式。|  
  
## 參考資料  
 [參考 \(C\+\+ AMP\)](../../parallel/amp/reference/reference-cpp-amp.md)  
  
 [tile\_static 關鍵字](../../cpp/tile-static-keyword.md)  
  
 [restrict \(C\+\+ AMP\)](../../cpp/restrict-cpp-amp.md)  
  
## 其他資源  
 [機器碼平行程式設計部落格](http://go.microsoft.com/fwlink/p/?LinkId=238472)  
  
 [下載 C\+\+ AMP 範例專案](http://go.microsoft.com/fwlink/p/?LinkId=248508)  
  
 [使用並行視覺化檢視分析 C\+\+ AMP 程式碼](http://go.microsoft.com/fwlink/?LinkID=253987&clcid=0x409) \(英文\)