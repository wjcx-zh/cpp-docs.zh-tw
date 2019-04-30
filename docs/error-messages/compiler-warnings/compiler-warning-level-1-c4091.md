---
title: 編譯器警告 （層級 1） C4091
ms.date: 11/04/2016
f1_keywords:
- C4091
helpviewer_keywords:
- C4091
ms.assetid: 3a404967-ab42-49b0-b324-fd7ba1859d78
ms.openlocfilehash: 87432a74dfe7c09a52f436d4e91b3f70eb66856b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410443"
---
# <a name="compiler-warning-level-1-c4091"></a>編譯器警告 （層級 1） C4091

'keyword': 當沒有宣告變數時，忽略 'type' 的左邊

編譯器偵測到的情況下，使用者可能想要的變數宣告，但編譯器找不到宣告變數。

## <a name="example"></a>範例

A`__declspec`使用者定義型別宣告的開頭的屬性會套用至該類型的變數。 C4091 表示沒有宣告變數時。 下列範例會產生 C4091。

```
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

如果識別項的 typedef，它不能也是變數的名稱。 下列範例會產生 C4091。

```
// C4091_b.cpp
// compile with: /c /W1 /WX
#define LIST 4
typedef struct _LIST {} LIST;   // C4091
```