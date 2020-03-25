---
title: 編譯器警告 (層級 1) C4399
ms.date: 11/04/2016
f1_keywords:
- C4399
helpviewer_keywords:
- C4399
ms.assetid: f58d9ba7-71a0-4c3b-b26f-f946dda8af30
ms.openlocfilehash: a556fbffad41d04b3eb0ea1acfd5e8739ddd5b68
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186799"
---
# <a name="compiler-warning-level-1-c4399"></a>編譯器警告 (層級 1) C4399

> '*symbol*'：以/clr： pure 編譯時，不應該以 __declspec （dllimport）標示每個進程符號

## <a name="remarks"></a>備註

**/Clr： pure**編譯器選項在 Visual Studio 2015 中已被取代，在 Visual Studio 2017 中不支援。

原生映射或具有原生和 CLR 結構之影像的資料，無法匯入到純影像中。 若要解決這個警告，請使用 **/clr** （不是 **/clr： pure**）進行編譯，或刪除 `__declspec(dllimport)`。

## <a name="example"></a>範例

下列範例會產生 C4399。

```cpp
// C4399.cpp
// compile with: /clr:pure /doc /W1 /c
__declspec(dllimport) __declspec(process) extern const int i;   // C4399
```
