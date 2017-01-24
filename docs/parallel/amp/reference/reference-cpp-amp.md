---
title: "參考 (C++ AMP) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp/Concurrency::Reference (C++ AMP)"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++ Accelerated Massive Parallelism, 參考"
ms.assetid: 372a8aed-8a53-48c9-996f-9c3cf09c9fa8
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 參考 (C++ AMP)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

本節包含 C\+\+ Accelerated Massive Parallelism \(C\+\+ AMP\) 執行階段的參考資訊。  
  
> [!NOTE]
>  C\+\+ 語言標準針對程式庫等實作保留了以底線 \(`_`\) 字元為開頭之識別碼的用法。  請勿在您的程式碼中使用以底線為開頭的名稱。  我們不保證名稱遵循這個慣例之程式碼項目的行為，而且未來的發行版本可能會變更。  基於這些原因，本文件省略了這類程式碼項目。  
  
## 在本節中  
 [Concurrency 命名空間 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)  
 提供為在資料平行硬體上執行的 C\+\+ 程式碼加速的類別和函式。  
  
 [Concurrency::direct3d 命名空間](../../../parallel/amp/reference/concurrency-direct3d-namespace.md)  
 提供支援 D3D 互通性的函式。  啟用緊密整合用於 AMP 程式碼中的 D3D 資源計算，您毋需建立多餘的中間複本即可使用 AMP 程式碼在 D3D 模式下建立的資源。  您可以使用 C\+\+ AMP，以累加方式加速 DirectX 應用程式的大量運算區段，並將 D3D 應用程式開發介面用於 AMP 計算所產生的資料。  
  
 [Concurrency::fast\_math 命名空間](../../../parallel/amp/reference/concurrency-fast-math-namespace.md)  
 `fast_math` 命名空間中的函式不符合 C99 標準。  僅提供每個函式的單精確度版本。  這些函式使用 DirectX 內建函式，比 `precise_math` 命名空間的對應函式更快速，而且不需要加速器的擴充雙精確度支援，不過它們比較不精確。  每個函式有兩個版本，以便在來源層級與 C99 程式碼相容；兩個版本會接受並傳回單精確度值。  
  
 [Concurrency::graphics 命名空間](../../../parallel/amp/reference/concurrency-graphics-namespace.md)  
 提供專為圖形程式設計而設計的類型與函式。  
  
 [Concurrency::precise\_math 命名空間](../../../parallel/amp/reference/concurrency-precise-math-namespace.md)  
 `precise_math` 命名空間中的函式符合 C99 標準。  每個函式的單精確度與雙精確度版本都有包含。  這些函式包括單精確度函式，在加速器上需要擴充的雙精確度支援。  
  
## 相關章節  
 [C\+\+ AMP \(C\+\+ Accelerated Massive Parallelism\)](../../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)  
 C\+\+ AMP 利用通常是獨立圖形顯示卡上的圖形處理器 \(GPU\) 等資料平行硬體來加速您的 C\+\+ 程式碼的執行。