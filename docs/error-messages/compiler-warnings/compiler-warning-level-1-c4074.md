---
title: 編譯器警告（層級1） C4074
ms.date: 11/04/2016
f1_keywords:
- C4074
helpviewer_keywords:
- C4074
ms.assetid: cd510e66-c338-4a86-a4d7-bfa1df9b16c3
ms.openlocfilehash: 1c84bbf436354ed672cedf13358837e298c7e4a5
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626913"
---
# <a name="compiler-warning-level-1-c4074"></a>編譯器警告（層級1） C4074

初始化運算式 put 編譯器保留的初始設定區域

由[#pragma init_seg](../../preprocessor/init-seg.md)指定的編譯器初始化區域是由 Microsoft 所保留。 此區域中的程式碼可能會在 C 執行時間程式庫的初始化之前執行。

下列範例會產生 C4074：

```cpp
// C4074.cpp
// compile with: /W1
#pragma init_seg( compiler )   // C4074

// try this line to resolve the warning
// #pragma init_seg(user)

int main() {
}
```