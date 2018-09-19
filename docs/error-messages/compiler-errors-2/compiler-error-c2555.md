---
title: 編譯器錯誤 C2555 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2555
dev_langs:
- C++
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f91ec33db2d3a7b6772556233a3c99b501ede76
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46017335"
---
# <a name="compiler-error-c2555"></a>編譯器錯誤 C2555

'class1::function1': 覆寫虛擬函式傳回類型不同，而且不是從 'class2::function2' 的 covariant

虛擬函式和衍生的覆寫函式具有相同的參數清單，但不同的傳回型別。 在衍生類別中的覆寫函式不能在只能由其傳回類型的基底類別中的虛擬函式不同。

若要解決這個錯誤，請呼叫虛擬函式之後轉換傳回的值。

如果您使用 /clr 編譯時，可能也會看到此錯誤。   例如，Visual c + + 相當於下列 C# 宣告：

```
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);
```

是

```
Guid CheckSources(Guid sourceID, Guid carouselIDs[]) [];
```

如需有關 C2555 的詳細資訊，請參閱知識庫文件 Q240862。

下列範例會產生 C2555:

```
// C2555.cpp
// compile with: /c
struct X {
   virtual void func();
};
struct Y : X {
   char func();  // C2555
   void func2();   // OK
};
```