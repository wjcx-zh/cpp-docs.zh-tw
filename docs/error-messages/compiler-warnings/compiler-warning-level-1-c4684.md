---
title: 編譯器警告（層級1） C4684
ms.date: 11/04/2016
f1_keywords:
- C4684
helpviewer_keywords:
- C4684
ms.assetid: e95f1a83-2784-4b05-ae94-12148e056e26
ms.openlocfilehash: f6ce86cc297a6529d58573f3e7d906f51771013b
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052511"
---
# <a name="compiler-warning-level-1-c4684"></a>編譯器警告（層級1） C4684

' attribute '：警告！ 屬性可能會導致不正確程式碼產生：請小心使用

您使用了不應該經常使用的屬性。

下列範例會產生 C4684：

```cpp
// C4684.cpp
// compile with: /W1 /LD
[module(name="xx")]; // C4684 expected
[no_injected_text];
```