---
title: 編譯器警告 C4687 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4687
dev_langs:
- C++
helpviewer_keywords:
- C4687
ms.assetid: 2f28e0b1-7358-4c88-bd70-aad8f0aa004c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9d813ce6d666431cfc3f74d1409012a4a0aec897
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118709"
---
# <a name="compiler-warning-c4687"></a>編譯器警告 C4687

'class': 密封抽象類別無法實作介面 'interface'

密封的抽象類別通常是僅有用來保存靜態成員函式。

如需詳細資訊，請參閱 <<c0> [ 抽象](../../windows/abstract-cpp-component-extensions.md)並[密封](../../windows/sealed-cpp-component-extensions.md)。

根據預設，C4687 會發出為錯誤。 您可以隱藏與 C4687[警告](../../preprocessor/warning.md)pragma。 如果您確定您想要在密封的抽象類別中實作的介面，您可以隱藏 C4687。

## <a name="example"></a>範例

下列範例會產生 C4687。

```
// C4687.cpp
// compile with: /clr /c
interface class A {};

ref struct B sealed abstract : A {};   // C4687
ref struct C sealed : A {};   // OK
ref struct D abstract : A {};   // OK
```