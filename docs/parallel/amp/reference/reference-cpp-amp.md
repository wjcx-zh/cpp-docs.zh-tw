---
title: 參考 (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::Reference (C++ AMP)
helpviewer_keywords:
- C++ Accelerated Massive Parallelism, reference
ms.assetid: 372a8aed-8a53-48c9-996f-9c3cf09c9fa8
ms.openlocfilehash: ff7c2b0894a2fa3de7674a72bc93dd3f781398b9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126405"
---
# <a name="reference-c-amp"></a>參考 (C++ AMP)

本節包含C++加速大量平行處理原則（C++ AMP）執行時間的參考資訊。

> [!NOTE]
> C++ 語言標準針對程式庫等實作，保留使用開頭為底線 (`_`) 字元的識別項。 請勿在程式碼中使用開頭為底線的名稱。 我們不保證名稱遵循這個慣例之程式碼項目的行為，而且未來的發行版本可能會變更。 因此，本文件中將省略這類程式碼項目。

## <a name="in-this-section"></a>本節內容

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)<br/>
提供類別和函式，可讓您C++加速資料平行硬體的程式碼。

[Concurrency::direct3d 命名空間](concurrency-direct3d-namespace.md)<br/>
提供支援 D3D 互通性的功能。 針對 AMP 程式碼中的計算，以及使用在 D3D 程式碼中建立的資源，無需建立多餘的中繼複本，即可順暢地使用 D3D 資源。 您可以使用C++ amp 以累加方式加速 DirectX 應用程式的計算密集型區段，並針對 AMP 計算所產生的資料使用 D3D API。

[Concurrency::fast_math 命名空間](concurrency-fast-math-namespace.md)<br/>
`fast_math` 命名空間中的函數不符合 C99 規範。 只提供每個函數的單精確度版本。 這些函式使用 DirectX 內建函式，其速度比 `precise_math` 命名空間中的對應函式還快，而且不需要加速器的擴充雙精確度支援，但較不精確。 每個函式都有兩個版本，以便與 C99 程式碼進行來源層級相容性;這兩個版本都採用並傳回單精確度值。

[Concurrency::graphics 命名空間](concurrency-graphics-namespace.md)<br/>
提供的類型和函式是針對圖形程式設計所設計。

[Concurrency::precise_math 命名空間](concurrency-precise-math-namespace.md)<br/>
`precise_math` 命名空間中的函式符合 C99 規範。 其中包含每個函式的單精確度和雙精確度版本。 這些函式（包括單精確度函數）在加速器上需要擴充的雙精確度支援。

## <a name="related-sections"></a>相關章節

[C++ AMP (C++ Accelerated Massive Parallelism)](../../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
C++AMP 利用在離散圖形配接器C++上通常呈現為圖形處理器（GPU）的資料平行硬體，加速程式碼的執行。
