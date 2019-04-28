---
title: 編譯器警告 (層級 4) C4559
ms.date: 08/27/2018
f1_keywords:
- C4559
helpviewer_keywords:
- C4559
ms.assetid: ed542f60-454d-45cb-85da-987ede61b1ab
ms.openlocfilehash: afb4fb493c7c3e34ca691720a30d74517b0ab5b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62220868"
---
# <a name="compiler-warning-level-4-c4559"></a>編譯器警告 (層級 4) C4559

> '*函式*': 重複定義; 函式取得 __declspec (*修飾詞*)

## <a name="remarks"></a>備註

函式已重新定義或宣告並新增第二個定義或宣告 **__declspec**修飾詞 (*修飾詞*)。 這個警告僅供參考。 若要修正這個警告，請刪除其中一個定義。

## <a name="example"></a>範例

下列範例會產生 C4559:

```cpp
// C4559.cpp
// compile with: /W4 /LD
void f();
__declspec(noalias) void f();   // C4559
```