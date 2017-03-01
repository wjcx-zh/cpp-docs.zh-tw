---
title: "參考 (c + + AMP) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp/Concurrency::Reference (C++ AMP)
dev_langs:
- C++
helpviewer_keywords:
- C++ Accelerated Massive Parallelism, reference
ms.assetid: 372a8aed-8a53-48c9-996f-9c3cf09c9fa8
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 22ba62ab8b3b4f9d14953dbab3edd8228ea85193
ms.openlocfilehash: cc654cedd8639377ab7011c91454f1508c730247
ms.lasthandoff: 02/24/2017

---
# <a name="reference-c-amp"></a>參考 (C++ AMP)
本節包含 c + + Accelerated Massive Parallelism (c + + AMP) 執行階段的參考資訊。  
  
> [!NOTE]
>  C++ 語言標準針對程式庫等實作，保留使用開頭為底線 (`_`) 字元的識別項。 請勿在程式碼中使用開頭為底線的名稱。 我們不保證名稱遵循這個慣例之程式碼項目的行為，而且未來的發行版本可能會變更。 因此，本文件中將省略這類程式碼項目。  
  
## <a name="in-this-section"></a>本章節內容  
 [Concurrency 命名空間 (c + + AMP)](concurrency-namespace-cpp-amp.md)  
 提供類別和函式可讓 c + + 程式碼，在資料平行硬體加速。  
  
 [Concurrency:: direct3d 命名空間](concurrency-direct3d-namespace.md)  
 提供支援 D3D 互通性的函式。 可讓順暢地將 D3D 資源 AMP 程式碼中的計算並且使用所建立的資源 AMP D3D 程式碼中，而不需建立中繼副本。 您可以使用 c + + AMP 累加加速運算密集的部份 DirectX 應用程式，並使用 D3D API AMP 計算所產生的資料。  
  
 [Concurrency:: fast_math 命名空間](concurrency-fast-math-namespace.md)  
 函式的`fast_math`命名空間不符合 C99 標準。 只有每個函式的單精確度版本都會提供。 這些函式會使用 DirectX 內建函式，也就是比對應的函式中`precise_math`命名空間並不需要擴充的雙精確度支援加速器上，但它們是較不精確。 有兩個版本的來源層級相容性的 C99 程式碼; 每個函式這兩個版本使用，並傳回單精確度值。  
  
 [Concurrency:: graphics 命名空間](concurrency-graphics-namespace.md)  
 圖形程式設計提供型別和函式所設計。  
  
 [Concurrency:: precise_math 命名空間](concurrency-precise-math-namespace.md)  
 函式的`precise_math`命名空間是 C99 標準。 每個函式的單精確度和雙精度版本隨附。 這些函式，包括單精確度函式 — 需要擴充的雙精確度支援加速器上。  
  
## <a name="related-sections"></a>相關章節  
 [C++ AMP (C++ Accelerated Massive Parallelism)](../../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)  
 C + + AMP 利用通常呈現為離散的圖形卡上的圖形處理單元 (GPU) 的資料平行硬體加速您的 c + + 程式碼的執行。






