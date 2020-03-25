---
title: 編譯器警告 (層級 1) C4176
ms.date: 11/04/2016
f1_keywords:
- C4176
helpviewer_keywords:
- C4176
ms.assetid: cfffb934-219a-4a63-9df6-ba54405bf766
ms.openlocfilehash: e7efe17b9840179bd21a432c2654fadd7e9230c6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199988"
---
# <a name="compiler-warning-level-1-c4176"></a>編譯器警告 (層級 1) C4176

'subcomponent': #pragma 元件瀏覽器的未知子元件

**component** pragma 包含無效的子元件。 若要排除特定名稱的參考，您必須在名稱前面使用 **參考** 選項。

## <a name="example"></a>範例

```cpp
// C4176.cpp
// compile with: /W1 /LD
#pragma component(browser, off, i)  // C4176
#pragma component(browser, off, references, i) // ok
```
