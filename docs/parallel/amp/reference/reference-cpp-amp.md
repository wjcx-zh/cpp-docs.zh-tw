---
title: 參考 (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::Reference (C++ AMP)
helpviewer_keywords:
- C++ Accelerated Massive Parallelism, reference
ms.assetid: 372a8aed-8a53-48c9-996f-9c3cf09c9fa8
ms.openlocfilehash: a334c7873675183dc06abfc2fe51472190996bf3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351166"
---
# <a name="reference-c-amp"></a>參考 (C++ AMP)

此章節包含的參考資訊C++Accelerated Massive Parallelism (C++ AMP) 執行階段。

> [!NOTE]
>  C++ 語言標準針對程式庫等實作，保留使用開頭為底線 (`_`) 字元的識別項。 請勿在程式碼中使用開頭為底線的名稱。 我們不保證名稱遵循這個慣例之程式碼項目的行為，而且未來的發行版本可能會變更。 因此，本文件中將省略這類程式碼項目。

## <a name="in-this-section"></a>本節內容

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)<br/>
提供類別和函式，讓兩端的加速度C++在資料平行硬體上的程式碼。

[Concurrency::direct3d 命名空間](concurrency-direct3d-namespace.md)<br/>
提供支援 D3D 互通性的函式。 能夠充分運用 D3D 資源在 AMP 程式碼中的計算以及使用的資源在 AMP 中 D3D 程式碼建立，而不需要建立中繼複本。 您可以使用C++以累加方式加速 DirectX 應用程式的大量運算區段，並對資料使用 D3D API AMP 計算所產生的 P。

[Concurrency::fast_math 命名空間](concurrency-fast-math-namespace.md)<br/>
中的函式`fast_math`命名空間不符合 C99 標準。 只有每個函式的單精確度版本提供。 這些函式使用 DirectX 內建函式，也就是較快，對應的函式中`precise_math`命名空間並不需要擴充的雙精確度支援快速鍵，但較不精確。 有兩個版本的來源層級與 C99 程式碼; 的相容性的每個函式這兩個版本會接受並傳回單精確度值。

[Concurrency::graphics 命名空間](concurrency-graphics-namespace.md)<br/>
提供型別和函式專為圖形程式設計。

[Concurrency::precise_math 命名空間](concurrency-precise-math-namespace.md)<br/>
中的函式`precise_math`命名空間會符合 C99 標準。 每個函式的單精確度和雙精確度版本會包含項目。 這些函式 — 包括單精確度函式，需要在加速器上的擴充的雙精確度支援。

## <a name="related-sections"></a>相關章節

[C++ AMP (C++ Accelerated Massive Parallelism)](../../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
C++AMP 加速執行您C++利用資料平行硬體，通常是圖形處理單元 (GPU) 在獨立圖形顯示卡上的程式碼。
