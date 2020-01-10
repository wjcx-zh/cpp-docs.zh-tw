---
title: 編譯器錯誤 C2778
ms.date: 11/04/2016
f1_keywords:
- C2778
helpviewer_keywords:
- C2778
ms.assetid: b24cb732-2914-42cc-8928-e2d87b393428
ms.openlocfilehash: 247aba1b4dfe6b6d6db1e2b8f46f2aa08abf1a79
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739983"
---
# <a name="compiler-error-c2778"></a>編譯器錯誤 C2778

__declspec （uuid （））中格式不正確的 GUID

為[uuid](../../cpp/uuid-cpp.md)擴充屬性提供了不正確的 GUID。

GUID 必須是十六進位數位的字串，其格式如下：

```cpp
// C2778a.cpp
// compile with: /c
struct __declspec(uuid("00000000-0000-0000-0000-000000000000")) A {};
struct __declspec(uuid("{00000000-0000-0000-0000-000000000000}")) B{};
```

`uuid` 擴充屬性會接受[CLSIDFromString](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromstring)所辨識的字串，以及或不含大括弧分隔符號。

下列範例會產生 C2778：

```cpp
// C2778b.cpp
struct __declspec(uuid(" 00000000-0000-0000-0000-000000000000 ")) C { };   // C2778
struct __declspec(uuid("00000000000000000000000000000000")) D { };   // C2778
```
