---
title: 編譯器警告 (層級 4) C4565
ms.date: 08/27/2018
f1_keywords:
- C4565
helpviewer_keywords:
- C4565
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
ms.openlocfilehash: b655dcfb456d32e45833e89e5a48926ad70d1d9e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62220477"
---
# <a name="compiler-warning-level-4-c4565"></a>編譯器警告 (層級 4) C4565

> '*函式*': 重複定義; 符號先前已宣告為 __declspec (*修飾詞*)

## <a name="remarks"></a>備註

符號已重新定義或宣告和第二個定義或宣告中的，不同於第一個定義或宣告中，沒有`__declspec`修飾詞 (*修飾詞*)。 這個警告僅供參考。 若要修正這個警告，請刪除其中一個定義。

## <a name="example"></a>範例

下列範例會產生 C4565:

```cpp
// C4565.cpp
// compile with: /W4 /LD
__declspec(noalias) void f();
void f();   // C4565
```