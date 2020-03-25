---
title: 編譯器警告 (層級 1) C4036
ms.date: 11/04/2016
f1_keywords:
- C4036
helpviewer_keywords:
- C4036
ms.assetid: f0b15359-4d62-48ec-8cb1-a7b36587a47f
ms.openlocfilehash: 812f36884d24ac988353dbcb18609d4c506e3110
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164257"
---
# <a name="compiler-warning-level-1-c4036"></a>編譯器警告 (層級 1) C4036

未命名的 'type' 當做實質參數

未針對結構、等位、列舉或作為實質參數的類別提供任何類型名稱。 如果您使用 [/Zg](../../build/reference/zg-generate-function-prototypes.md) 來產生函式原型，編譯器會發出這個警告並將產生之原型中的型式參數標記為註解。

請指定類型名稱來解決這個警告。

## <a name="example"></a>範例

下列範例會產生 C4036：

```c
// C4036.c
// compile with: /Zg /W1
// D9035 expected
typedef struct { int i; } T;
void f(T* t) {}   // C4036

// OK
typedef struct MyStruct { int i; } T2;
void f2(T2 * t) {}
```
