---
title: 編譯器警告 (層級 1) C4091
ms.date: 11/04/2016
f1_keywords:
- C4091
helpviewer_keywords:
- C4091
ms.assetid: 3a404967-ab42-49b0-b324-fd7ba1859d78
ms.openlocfilehash: 1a9fef0a825f98ab3ce8d935c98eefe1866be6cf
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684686"
---
# <a name="compiler-warning-level-1-c4091"></a>編譯器警告 (層級 1) C4091

' 關鍵字 '：未宣告變數時，在 ' type ' 的左邊忽略

編譯器偵測到使用者可能想要宣告變數，但編譯器無法宣告變數的情況。

## <a name="examples"></a>範例

**`__declspec`** 使用者定義型別宣告開頭的屬性會套用至該類型的變數。 C4091 指出未宣告任何變數。 下列範例會產生 C4091。

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

如果識別碼是 typedef，它也不能是變數名稱。 下列範例會產生 C4091。

```cpp
// C4091_b.cpp
// compile with: /c /W1 /WX
#define LIST 4
typedef struct _LIST {} LIST;   // C4091
```
