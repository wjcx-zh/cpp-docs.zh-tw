---
title: 編譯器錯誤 C3665 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3665
dev_langs:
- C++
helpviewer_keywords:
- C3665
ms.assetid: 893bb47e-8de1-43aa-af7d-fa47ad149ee9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16d7f64bebfda41a958edf9759359bc38352c086
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025252"
---
# <a name="compiler-error-c3665"></a>編譯器錯誤 C3665

'解構函式': 覆寫規範 'keyword' 不允許解構函式/完成項

使用解構函式或完成項不允許的關鍵字。

比方說，解構函式或完成項無法要求新的位置。  如需詳細資訊，請參閱 <<c0> [ 明確覆寫](../../windows/explicit-overrides-cpp-component-extensions.md)並[解構函式和完成項](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)。

下列範例會產生 C3665:

```
// C3665.cpp
// compile with: /clr
public ref struct R {
   virtual ~R() { }
   virtual void a() { }
};

public ref struct S : R {
   virtual ~S() new {}   // C3665
   virtual void a() new {}   // OK
};
```