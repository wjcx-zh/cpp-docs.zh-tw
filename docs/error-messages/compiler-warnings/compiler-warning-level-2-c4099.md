---
title: 編譯器警告 (層級 2) C4099
ms.date: 11/04/2016
f1_keywords:
- C4099
helpviewer_keywords:
- C4099
ms.assetid: 00bb803d-cae7-4ab8-8969-b46f54139ac8
ms.openlocfilehash: 97ead14dc9771dc02ad722843ec9fe1a8056e3f6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174280"
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
