---
title: 編譯器警告 (層級 4) C4431
ms.date: 11/04/2016
f1_keywords:
- C4431
helpviewer_keywords:
- C4431
ms.assetid: 58434ab6-dd8d-427b-953a-602fb7453ae6
ms.openlocfilehash: 1cef70ab02148924bf6a0f29e298b34c54b28bc4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391513"
---
# <a name="compiler-warning-level-4-c4431"></a>編譯器警告 (層級 4) C4431

遺漏類型規範 - 假設為 int。 注意:C 不再支援 default-int

此錯誤可能會導致針對視覺效果所進行的編譯器一致性工作C++2005年:視覺化C++不會再預設會建立不具類型的識別項為 int。 必須明確指定識別碼的類型。

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