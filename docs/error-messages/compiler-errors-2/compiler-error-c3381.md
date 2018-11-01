---
title: 編譯器錯誤 C3381
ms.date: 11/04/2016
f1_keywords:
- C3381
helpviewer_keywords:
- C3381
ms.assetid: d276c89f-8377-4cb6-a8d4-7770885f06c4
ms.openlocfilehash: ae416d68831d1964c89d938dfcddd364e521195c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50440270"
---
# <a name="compiler-error-c3381"></a>編譯器錯誤 C3381

'assembly': 組件存取規範才可在使用 /clr 選項編譯的程式碼

原生類型可以是組件外部可見，但您只能指定組件中的原生類型的存取權 **/clr**編譯。

如需詳細資訊，請參閱 <<c0> [ 輸入可視性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility)並[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="example"></a>範例

下列範例會產生 C3381。

```
// C3381.cpp
// compile with: /c
public class A {};   // C3381
```