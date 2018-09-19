---
title: 編譯器錯誤 C2535 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2535
dev_langs:
- C++
helpviewer_keywords:
- C2535
ms.assetid: a958f83e-e2bf-4a59-b44b-d406ec325d7e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 98e1920b2163a318fbdba3b64d56bf74a8cd809f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085894"
---
# <a name="compiler-error-c2535"></a>編譯器錯誤 C2535

'identifier': 已經定義或宣告的成員函式

此錯誤可能被因使用一個以上的定義或宣告的多載的函式中相同的型式參數清單。

如果您因為 Dispose 函式而接到 c2535 錯誤訊息，請參閱[解構函式和完成項](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)如需詳細資訊。

如果您正在編譯 ATL 專案，請參閱知識庫文章 Q241852。

下列範例會產生 C2535:

```
// C2535.cpp
// compile with: /c
class C {
public:
   void func();   // forward declaration
   void func() {}   // C2535
};
```