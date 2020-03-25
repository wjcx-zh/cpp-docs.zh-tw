---
title: 編譯器警告 (層級 4) C4431
ms.date: 11/04/2016
f1_keywords:
- C4431
helpviewer_keywords:
- C4431
ms.assetid: 58434ab6-dd8d-427b-953a-602fb7453ae6
ms.openlocfilehash: d4d803ef003f2c8367c750cf6d6aef07e4032140
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185356"
---
# <a name="compiler-warning-level-4-c4431"></a>編譯器警告 (層級 4) C4431

遺漏類型規範 - 假設為 int。 注意: C 已不再支援 default-int

此錯誤可能是因為針對 Visual Studio 2005 所做的編譯器一致性工作所產生： Visual C++不再建立不具類型的識別碼做為 int （預設值）。 必須明確指定識別碼的類型。

此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。

## <a name="example"></a>範例

下列範例會產生 C4431。

```c
// C4431.c
// compile with: /c /W4
#pragma warning(default:4431)
i;   // C4431
int i;   // OK
```
