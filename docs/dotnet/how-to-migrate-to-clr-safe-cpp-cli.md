---
title: 如何： 移轉至 clr： 安全 (C + + /CLI) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- migration [C++], verifiable assemblies
- upgrading Visual C++ applications, verifiable assemblies
- verifiable assemblies [C++], migrating to
- /clr compiler option [C++], migrating to /clr:safe
ms.assetid: 75f9aae9-1dcc-448a-aa11-2d96f972f9d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d72be19eb893a74a17a988e8c14c6bdaba766cbc
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704510"
---
# <a name="how-to-migrate-to-clrsafe-ccli"></a>如何：移轉至 /clr:safe (C++/CLI)

> [!IMPORTANT]
> **/Clr: pure**和 **/clr: safe**編譯器選項都是 Visual Studio 2015 中已被取代，並不支援的 Visual Studio 2017 中。 如果您需要安全的 CLR 組件時，我們建議您將移植到 C# 程式碼。

如果您使用舊版的 Visual c + + 編譯器工具組，從 Visual Studio 2017 之前，您可以使用產生可驗證的元件 **/clr: safe**，因而導致編譯器錯誤產生每個非可驗證程式碼建構。

## <a name="remarks"></a>備註

下列問題會產生可驗證性錯誤：

- 原生類型。 即使不使用原生類別、 結構、 指標或陣列的宣告會造成編譯。

- 全域變數

- 任何未受管理的媒體櫃，包括通用語言執行階段函式呼叫的函式呼叫

- 可驗證的函式不能包含[static_cast 運算子](../cpp/static-cast-operator.md)的向下轉型。 [Static_cast 運算子](../cpp/static-cast-operator.md)可用於基本類型之間轉型，但向下轉型[safe_cast](../windows/safe-cast-cpp-component-extensions.md) C-style 轉換或 (這會實作為[safe_cast](../windows/safe-cast-cpp-component-extensions.md))必須使用。

- 可驗證的函式不能包含[reinterpret_cast 運算子](../cpp/reinterpret-cast-operator.md)（或任何 c-style 轉換的對等項目）。

- 可驗證的函式無法執行算術運算[interior_ptr (C + + /CLI)](../windows/interior-ptr-cpp-cli.md)。 它可能只指派給它，並取值 （dereference） 它。

- 可驗證的函式只可以擲回或攔截參考類型的指標，因此必須 boxed 實值型別，擲回之前。

- 可驗證的函式只可以呼叫可驗證的函式 (，例如不允許呼叫 common language runtime，包含`AtEntry` / `AtExit`，因此不允許使用全域建構函式)。

- 可驗證的類別不能使用<xref:System.Runtime.InteropServices.LayoutKind>。

- 如果建置 EXE，main 函式不能宣告任何參數，因此<xref:System.Environment.GetCommandLineArgs%2A>必須用來擷取命令列引數。

- 非虛擬呼叫虛擬函式。 例如: 

   ```cpp
   // not_verifiable.cpp
   // compile with: /clr
   ref struct A {
      virtual void Test() {}
   };

   ref struct B : A {};

   int main() {
      B^ b1 = gcnew B;
      b1->A::Test();   // Non-virtual call to virtual function
   }
   ```

此外，下列關鍵字不能在可驗證程式碼：

- [unmanaged](../preprocessor/managed-unmanaged.md)和[套件](../preprocessor/pack.md)pragma

- [naked](../cpp/naked-cpp.md)和[對齊](../cpp/align-cpp.md) [__declspec](../cpp/declspec.md)修飾詞

- [__asm](../assembler/inline/asm.md)

- [__based](../cpp/based-grammar.md)

- [__try](../cpp/try-except-statement.md)和 `__except`

## <a name="see-also"></a>另請參閱

- [純粹的和可驗證的程式碼 (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)
