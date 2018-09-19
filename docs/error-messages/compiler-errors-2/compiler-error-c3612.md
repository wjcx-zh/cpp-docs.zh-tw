---
title: 編譯器錯誤 C3612 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3612
dev_langs:
- C++
helpviewer_keywords:
- C3612
ms.assetid: aa6e3a2b-4afa-481c-98c1-1b6d1f82f869
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16d960095942af34aa516341862c9a2bcf72bbba
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053674"
---
# <a name="compiler-error-c3612"></a>編譯器錯誤 C3612

'type': 密封的類別不能為抽象

使用所定義的型別`value`密封格式，根據預設，和類別是抽象的除非它會實作其基底的所有方法。 密封的抽象類別都可以是基底類別，也可以它具現化。

如需詳細資訊，請參閱 <<c0> [ 類別和結構](../../windows/classes-and-structs-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3612:

```
// C3612.cpp
// compile with: /clr /c
value struct V: public System::ICloneable {};   // C3612

// OK
value struct V2: public System::ICloneable {
   Object^ Clone();
};
```