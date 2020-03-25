---
title: 編譯器警告 (層級 2) C4309
ms.date: 11/04/2016
f1_keywords:
- C4309
helpviewer_keywords:
- C4309
ms.assetid: cb3f41ef-fd8a-4def-baa1-924e751fca68
ms.openlocfilehash: a307d941f6225c9e431ad71a6385229bd01957f9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161863"
---
# <a name="compiler-warning-level-2-c4309"></a>編譯器警告 (層級 2) C4309

' 轉換 '：常數值的截斷

型別轉換會使常數超過配置給它的空間。 您可能需要針對常數使用較大的類型。

下列範例會產生 C4309：

```cpp
// C4309.cpp
// compile with: /W2
int main()
{
   char c = 128;   // C4309
}
```
