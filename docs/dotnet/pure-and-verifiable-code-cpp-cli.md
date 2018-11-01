---
title: 純粹的和可驗證的程式碼 (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- /clr compiler option [C++], verifiable assemblies
- /clr compiler option [C++], mixed assemblies
- pure MSIL [C++]
- verifiable assemblies [C++]
- verifiably type-safe code [C++]
- /clr compiler option [C++], pure assemblies
- .NET Framework [C++], pure and verifiable code
- assemblies [C++], mixed code
- verifiable assemblies [C++], about verifiable assemblies
- mixed assemblies [C++], about mixed assemblies
- pure MSIL [C++], about pure code
- assemblies [C++], verifiable code
- mixed assemblies [C++]
- assemblies [C++], pure code
ms.assetid: 9050e110-fa11-4356-b56c-665187ff871c
ms.openlocfilehash: 11cccc082d5b9e467f5fafce6f2128aa50d33879
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512788"
---
# <a name="pure-and-verifiable-code-ccli"></a>純粹的和可驗證的程式碼 (C + + /cli CLI)

如需.NET 程式設計，Visual Studio 2017 中 Visual c + + 支援混合的組件的建立使用[/clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)編譯器選項。 **/Clr: pure**並 **: safe**選項是在 Visual Studio 2015 中已被取代，而且不支援的 Visual Studio 2017 中。 如果您的程式碼必須是安全或驗證的則我們建議您移植到C#。

## <a name="mixed-clr"></a>混合 (/ clr)

混合組件 (以編譯 **/clr**)、 包含非受控和受控組件，讓他們能夠使用.NET 功能，但仍然包含原生程式碼。 這可讓應用程式和元件更新，而不需要重寫整個專案中使用.NET 功能。 使用 Visual c + + 混合 managed 和原生程式碼，以這種方式被呼叫 c + + Interop。 如需詳細資訊，請參閱 <<c0> [ 混合 （原生和 Managed） 組件](../dotnet/mixed-native-and-managed-assemblies.md)並[原生和.NET 互通性](../dotnet/native-and-dotnet-interoperability.md)。

從 managed 組件對原生 Dll 透過 P/Invoke 的呼叫會進行編譯，但在執行階段根據安全性設定可能會失敗。

還有一個程式碼撰寫案例，將會通過編譯器，但會導致無法驗證的組件： 呼叫虛擬函式，透過使用範圍解析運算子的物件執行個體。  例如：`MyObj -> A::VirtualFunction();`。

## <a name="see-also"></a>另請參閱

- [以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

