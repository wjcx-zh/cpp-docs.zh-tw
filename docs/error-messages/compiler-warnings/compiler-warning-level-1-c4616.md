---
title: 編譯器警告（層級1） C4616
ms.date: 11/04/2016
f1_keywords:
- C4616
helpviewer_keywords:
- C4616
ms.assetid: 71e15265-c5bc-42ce-a6a9-4879892472b1
ms.openlocfilehash: 3c13eb28981779e2d089575660d8968c54e4e75f
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051470"
---
# <a name="compiler-warning-level-1-c4616"></a>編譯器警告（層級1） C4616

\#pragma warning：警告編號 ' number ' 不是有效的編譯器警告

無法重新指派[警告](../../preprocessor/warning.md)pragma 中指定的警告編號。 已忽略 pragma。

下列範例會產生 C4616：

```cpp
// C4616.cpp
// compile with: /W1 /c
#pragma warning( disable : 0 )   // C4616
#pragma warning( disable : 999 )   // OK
#pragma warning( disable : 4998 )   // OK
```