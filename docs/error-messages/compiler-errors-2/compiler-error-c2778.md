---
title: 編譯器錯誤 C2778
ms.date: 11/04/2016
f1_keywords:
- C2778
helpviewer_keywords:
- C2778
ms.assetid: b24cb732-2914-42cc-8928-e2d87b393428
ms.openlocfilehash: 98b5bf0a1315236f3ce96fd4b8c140ce1ab70a9f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501041"
---
# <a name="compiler-error-c2778"></a>編譯器錯誤 C2778

__declspec （uuid （））中格式不正確的 GUID

為[uuid](../../cpp/uuid-cpp.md)擴充屬性提供了不正確的 GUID。

GUID 必須是十六進位數位的字串，其格式如下：

```
// C2778a.cpp
// compile with: /c
struct __declspec(uuid("00000000-0000-0000-0000-000000000000")) A {};
struct __declspec(uuid("{00000000-0000-0000-0000-000000000000}")) B{};
```

擴充屬性會接受 [CLSIDFromString](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromstring) 所辨識的字串，並包含或不含大括弧分隔符號。`uuid`

下列範例會產生 C2778：

```
// C2778b.cpp
struct __declspec(uuid(" 00000000-0000-0000-0000-000000000000 ")) C { };   // C2778
struct __declspec(uuid("00000000000000000000000000000000")) D { };   // C2778
```