---
title: 純粹的和可驗證的程式碼 (C + + /CLI) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c4f4b9bd590ad873d0b241d2c095be53ad1dacb4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="pure-and-verifiable-code-ccli"></a>純粹的和可驗證的程式碼 (C++/CLI)
對於.NET 程式設計，Visual c + + 在 Visual Studio 2017 支援混合的組件建立使用[/clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)編譯器選項。 **/Clr: pure**和 **: safe**選項已被取代為準，Visual Studio 2015 和編譯器的未來版本將移除。 如果必須驗證您的程式碼，我們建議您將其移植到 C#。
  
## <a name="mixed-clr"></a>混合 (/ clr)  
 混合的組件 (以編譯 **/clr**)、 包含 unmanaged 和 managed 組件，讓它們使用.NET 功能，但仍然包含原生程式碼。 這可讓應用程式和元件更新，而不需要重寫整個專案中使用.NET 功能。 使用 Visual c + + 混合這種方式中的 managed 和原生程式碼會呼叫 c + + Interop。 如需詳細資訊，請參閱[混合 （原生和 Managed） 組件](../dotnet/mixed-native-and-managed-assemblies.md)和[原生和.NET 互通性](../dotnet/native-and-dotnet-interoperability.md)。  
  
  
從 managed 組件對原生 Dll，透過 P/Invoke 的呼叫將會編譯，但可能無法在執行階段視安全性設定而定。  
  
一個程式碼撰寫的狀況，將會通過編譯器，但會導致無法驗證的組件： 呼叫虛擬函式，透過使用範圍解析運算子的物件執行個體。  例如：`MyObj -> A::VirtualFunction();`。  
  
## <a name="see-also"></a>另請參閱  
 [以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
