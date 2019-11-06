---
title: 編譯器警告（層級1） C4079
ms.date: 11/04/2016
f1_keywords:
- C4079
helpviewer_keywords:
- C4079
ms.assetid: 549759f0-e168-47e9-8c9a-de93ac843689
ms.openlocfilehash: 27304f8c31c195097c6adcdae1408ef7ad9698bc
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627047"
---
# <a name="compiler-warning-level-1-c4079"></a>編譯器警告（層級1） C4079

未預期的語彙基元 'token'

Pragma 引數清單中發生未預期的分隔符號 token。 已忽略 pragma 的其餘部分。

下列範例會產生 C4079：

```cpp
// C4079.cpp
// compile with: /W1
#pragma warning(disable : 4081)
#pragma pack(c,16)   // C4079

int main() {
}
```