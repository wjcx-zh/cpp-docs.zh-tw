---
title: 編譯器警告 (層級 2) C4099
ms.date: 11/04/2016
f1_keywords:
- C4099
helpviewer_keywords:
- C4099
ms.assetid: 00bb803d-cae7-4ab8-8969-b46f54139ac8
ms.openlocfilehash: d685f1f40826b975623dbedc2ba8115c6b3edc45
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052185"
---
# <a name="compiler-warning-level-2-c4099"></a>編譯器警告 (層級 2) C4099

' identifier '：第一次看到使用 ' objecttype1 ' 的類型名稱，現在已使用 ' objecttype2 '

宣告為結構的物件會定義為類別，或宣告為類別的物件會定義為結構。 編譯器會使用定義中提供的型別。

## <a name="example"></a>範例

下列範例會產生 C4099。

```cpp
// C4099.cpp
// compile with: /W2 /c
struct A;
class A {};   // C4099, use different identifer or use same object type
```