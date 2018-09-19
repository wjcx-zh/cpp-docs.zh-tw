---
title: 編譯器錯誤 C3418 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3418
dev_langs:
- C++
helpviewer_keywords:
- C3418
ms.assetid: 54042c04-3c45-41c1-bad7-90f9ee05a21b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 26fa67da6f24e578319660c17cb48d7d715be408
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033266"
---
# <a name="compiler-error-c3418"></a>編譯器錯誤 C3418

不支援存取規範 'specifier'

CLR 存取規範指定不正確。  如需詳細資訊，請參閱類型可視性和中的成員可視性[如何： 定義與使用類別和結構 (C + + /cli CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)。

## <a name="example"></a>範例

下列範例會產生 C3418：

```cpp
// C3418.cpp
// compile with: /clr /c
ref struct m {
internal public:   // C3418
   void test(){}
};

ref struct n {
internal:   // OK
   void test(){}
};
```