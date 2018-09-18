---
title: 編譯器警告 （層級 1） C4674 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4674
dev_langs:
- C++
helpviewer_keywords:
- C4674
ms.assetid: 638dae0b-b82c-4865-9599-72630827ca09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9b2f945982e80b49403387241f29a50876274e66
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024875"
---
# <a name="compiler-warning-level-1-c4674"></a>編譯器警告 (層級 1) C4674

'method' 必須宣告為 'static'，而且只能有一個參數

轉換運算子的簽章不正確。 此方法不會視為使用者定義的轉換。 如需有關如何定義運算子的詳細資訊，請參閱[使用者定義的運算子 (C + + /cli CLI)](../../dotnet/user-defined-operators-cpp-cli.md)並[使用者定義的轉換 (C + + /cli CLI)](../../dotnet/user-defined-conversions-cpp-cli.md)。

## <a name="example"></a>範例

下列範例會產生 C4674。

```
// C4674.cpp
// compile with: /clr /WX /W1 /LD
ref class G {
   int op_Implicit(int i) {   // C4674
      return 0;
   }
};
```
