---
title: 編譯器錯誤 C3084 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3084
dev_langs:
- C++
helpviewer_keywords:
- C3084
ms.assetid: 0362cb70-e24e-476f-a24d-8f5bb97c3afd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 44bab3f43efa186c83134a6b40e7cb3fcbcbd51d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027228"
---
# <a name="compiler-error-c3084"></a>編譯器錯誤 C3084

'function': 完成項/解構函式不能是 'keyword'

不正確地宣告完成項或解構函式。

例如，解構函式不應該標示為密封。  衍生類型將無法存取解構函式。  如需詳細資訊，請參閱 <<c0> [ 明確覆寫](../../windows/explicit-overrides-cpp-component-extensions.md)並[解構函式和完成項中如何： 定義和使用類別和結構 (C + + /cli CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)。

## <a name="example"></a>範例

下列範例會產生 C3084。

```
// C3084.cpp
// compile with: /clr /c
ref struct R {
protected:
   !R() sealed;   // C3084
   !R() abstract;   // C3084
   !R();
};
```