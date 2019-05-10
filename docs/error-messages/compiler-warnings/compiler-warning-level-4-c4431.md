---
title: 編譯器警告 (層級 4) C4431
ms.date: 11/04/2016
f1_keywords:
- C4431
helpviewer_keywords:
- C4431
ms.assetid: 58434ab6-dd8d-427b-953a-602fb7453ae6
ms.openlocfilehash: 6a07a9ffa938d9372ebed9676847b3274115d526
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447014"
---
# <a name="compiler-warning-level-4-c4431"></a>編譯器警告 (層級 4) C4431

遺漏類型規範 - 假設為 int。 注意:C 不再支援 default-int

此錯誤可能會導致針對 Visual Studio 2005 所進行的編譯器一致性工作：視覺化C++不會再預設會建立不具類型的識別項為 int。 必須明確指定識別碼的類型。

此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。

## <a name="example"></a>範例

下列範例會產生 C4431。

```
// C4431.c
// compile with: /c /W4
#pragma warning(default:4431)
i;   // C4431
int i;   // OK
```