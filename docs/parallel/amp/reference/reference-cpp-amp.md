---
title: 參考 (c + + AMP) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- amp/Concurrency::Reference (C++ AMP)
dev_langs:
- C++
helpviewer_keywords:
- C++ Accelerated Massive Parallelism, reference
ms.assetid: 372a8aed-8a53-48c9-996f-9c3cf09c9fa8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8c39528bf3b1e6c9235e4b2daabcd8bbddd0d52f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="reference-c-amp"></a>參考 (C++ AMP)
本節包含 c + + Accelerated Massive Parallelism (c + + AMP) 執行階段的參考的資訊。  
  
> [!NOTE]
>  C++ 語言標準針對程式庫等實作，保留使用開頭為底線 (`_`) 字元的識別項。 請勿在程式碼中使用開頭為底線的名稱。 我們不保證名稱遵循這個慣例之程式碼項目的行為，而且未來的發行版本可能會變更。 因此，本文件中將省略這類程式碼項目。  
  
## <a name="in-this-section"></a>本節內容  
 [Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)  
 提供類別和函式可讓 c + + 程式碼，在資料平行硬體加速。  
  
 [Concurrency::direct3d 命名空間](concurrency-direct3d-namespace.md)  
 提供支援 D3D 互通性函式。 啟用無縫使用 D3D 資源 AMP 程式碼中的計算和使用的資源中 AMP 建立 D3D 程式碼中，而不需要建立中繼副本。 您可以使用 c + + AMP 以累加方式加速 DirectX 應用程式的需要大量計算的區段，並使用 D3D API 從 AMP 計算所產生的資料。  
  
 [Concurrency::fast_math 命名空間](concurrency-fast-math-namespace.md)  
 中的函式`fast_math`命名空間不符合 C99 標準。 只有每個函式的單精確度版本都會提供。 這些函式使用 DirectX 內建函式，也就是較快中的對應函式`precise_math`命名空間並不需要在加速器上擴充的雙精確度支援，但是可以較不精確。 有兩個版本的來源層級與 C99 程式碼; 的相容性的每個函式這兩個版本採用，並傳回單一的有效位數值。  
  
 [Concurrency::graphics 命名空間](concurrency-graphics-namespace.md)  
 圖形程式設計提供型別和函式所設計。  
  
 [Concurrency::precise_math 命名空間](concurrency-precise-math-namespace.md)  
 中的函式`precise_math`命名空間是 C99 標準。 單精確度和雙精確度的每個函式版本會包含項目。 這些函式 — 這包括單精確度函式，需要在加速器上擴充的雙精確度支援。  
  
## <a name="related-sections"></a>相關章節  
 [C++ AMP (C++ Accelerated Massive Parallelism)](../../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)  
 C + + AMP 利用通常呈現為圖形處理器 (GPU) 上獨立圖形顯示卡的資料平行硬體加速您的 c + + 程式碼執行。





