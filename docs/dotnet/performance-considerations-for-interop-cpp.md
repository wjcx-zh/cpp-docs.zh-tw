---
title: Interop 的效能考量 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- /clr compiler option [C++], interop performance considerations
- platform invoke [C++], interoperability
- interop [C++], performance consideraitons
- mixed assemblies [C++], performance considerations
- interoperability [C++], performance considerations
ms.assetid: bb9a282e-c3f8-40eb-a2fa-45d80d578932
ms.openlocfilehash: c6b4456d9c75061c9a8c93f37f98b58f92adc899
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384747"
---
# <a name="performance-considerations-for-interop-c"></a>Interop 的效能考量 (C++)

本主題會提供指導方針，以降低管理/未受管理的執行階段效能的 interop 轉換的效果。

視覺化C++支援相同的互通性機制，與其他.NET 語言，例如 Visual Basic 和C#(P/Invoke)，但它也提供特定視覺效果的 interop 支援C++(C++ interop)。 針對效能關鍵的應用程式，請務必了解每個 interop 技術的效能含意。

不論所使用的 interop 技巧，特殊的轉換序列，稱為 thunk，都需要每次 managed 函式呼叫 unmanaged 的函式，反之亦然。 視覺效果會自動插入這些 thunkC++編譯器，但它是要牢記在心，累積，這些轉換可能耗用大量效能很重要。

## <a name="reducing-transitions"></a>減少轉換

若要避免或減少的 interop thunk 成本的一個方式是重構所牽涉到 managed/unmanaged 轉換降到最低的介面。 將目標設為多對話介面，是指涉及經常呼叫跨 managed/unmanaged 界限可大幅提升效能。 Managed 函式呼叫 unmanaged 函式在緊密迴圈中，比方說，是很好的候選重構。 如果迴圈本身會移至未受管理端，或如果受管理的替代方案，以建立未受管理的呼叫 （或許是對 unmanaged 端的佇列資料，然後封送處理其 unmanaged api 迴圈後，全部一次），轉換的數目可以降低登ificantly。

## <a name="pinvoke-vs-c-interop"></a>P/Invoke vs。C++ Interop

適用於.NET 的語言，例如 Visual Basic 和 C# 中，以原生元件相互操作的指定的方法是 P/Invoke。 因為.NET Framework 中，視覺效果支援 P/InvokeC++支援它，但 VisualC++也提供自己的互通性支援，指C++Interop。 C++Interop 建議，透過 P/Invoke 因為 P/Invoke 不是類型安全。 如此一來，錯誤主要會報告在執行階段，但C++Interop 也有透過 P/Invoke 的效能優點。

這兩種技術需要時 managed 函式會呼叫 unmanaged 函式的幾件事：

- 函式呼叫引數是以原生類型，封送處理從 CLR。

- 執行 managed 至 unmanaged 的 thunk。

- Unmanaged 函式會呼叫 （使用原生的版本引數）。

- 執行非受控至 managed 的 thunk。

- 傳回的型別和任何 「 發送 」 或 「 在 out 」 引數會從 CLR 類型的原生封送處理。

Managed/unmanaged 的 thunk 所需的 interop 運作，但資料封送處理所需取決於所涉及的資料類型、 函式簽章，以及如何使用資料。

資料封送處理由執行C++Interop 是最簡單的可能形式： 參數只會複製跨 managed/unmanaged 的界限，以位元的方式;在所有不執行任何轉換。 P/invoke，這是僅為 true，如果所有參數都都簡單，blittable 類型。 否則，P/Invoke 會執行非常強大的步驟，將每個受管理的參數轉換成適當的原生型別，而且反之亦然引數會標示為"out"，或"中，out"。

換句話說， C++ Interop 使用的資料封送處理，最快的可能方法，而 P/Invoke 使用的最強大的方法。 這表示， C++ Interop (以一般方式C++) 提供最佳效能，根據預設，程式設計人員是負責處理，這個行為並不安全或不適當的情況。

C++Interop 因此需要封送處理的資料必須明確地提供，但優點是程式設計人員可以自由地決定適當的資料，本質以及它所要使用的方式。 此外，雖然的 P/Invoke 資料封送處理行為可以修改在自訂的程度， C++ Interop 讓封送處理至呼叫藉由呼叫基礎上自訂的資料。 這是不可能使用 P/Invoke。

如需詳細資訊C++Interop，請參閱[Using C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)。

## <a name="see-also"></a>另請參閱

[混合 (原生和 Managed) 組件](../dotnet/mixed-native-and-managed-assemblies.md)
