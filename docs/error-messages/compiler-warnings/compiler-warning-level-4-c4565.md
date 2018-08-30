---
title: 編譯器警告 （層級 4） C4565 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4565
dev_langs:
- C++
helpviewer_keywords:
- C4565
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c25f2f1fc16c6d45a7d1eddec8d3efe62db142f2
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211258"
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