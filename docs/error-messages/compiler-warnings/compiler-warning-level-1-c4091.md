---
title: 編譯器警告（層級1） C4091
ms.date: 11/04/2016
f1_keywords:
- C4091
helpviewer_keywords:
- C4091
ms.assetid: 3a404967-ab42-49b0-b324-fd7ba1859d78
ms.openlocfilehash: 8c373ad1eba07337dc970cb84202370c147560dd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163906"
---
# <a name="compiler-warning-level-1-c4091"></a>編譯器警告（層級1） C4091

' 關鍵字 '：未宣告任何變數時，在 ' type ' 左側忽略

編譯器偵測到使用者可能想要宣告變數，但編譯器無法宣告變數的情況。

## <a name="example"></a>範例

使用者自訂類型宣告開頭的 `__declspec` 屬性會套用至該類型的變數。 C4091 表示未宣告任何變數。 下列範例會產生 C4091。

```cpp
// C4091.cpp
// compile with: /W1 /c
__declspec(dllimport) class X {}; // C4091

// __declspec attribute applies to varX
__declspec(dllimport) class X2 {} varX;

// __declspec attribute after the class or struct keyword
// applies to user defined type
class __declspec(dllimport) X3 {};
```

## <a name="example"></a>範例

如果識別碼是 typedef，它也不能是變數名稱。 下列範例會產生 C4091。

```cpp
// C4091_b.cpp
// compile with: /c /W1 /WX
#define LIST 4
typedef struct _LIST {} LIST;   // C4091
```
