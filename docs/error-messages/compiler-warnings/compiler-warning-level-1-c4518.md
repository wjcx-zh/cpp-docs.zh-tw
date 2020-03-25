---
title: 編譯器警告 (層級 1) C4518
ms.date: 11/04/2016
f1_keywords:
- C4518
helpviewer_keywords:
- C4518
ms.assetid: 4ad21004-f076-43fd-99f4-4bf1f9be4c0b
ms.openlocfilehash: 76761d9e0a260a05acef01bc451ad411aac517c7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186513"
---
# <a name="compiler-warning-level-1-c4518"></a>編譯器警告 (層級 1) C4518

' 規範 '：此處非預期的儲存類別或類型規範;忽略

下列範例會產生 C4518：

```cpp
// C4518.cpp
// compile with: /c /W1
_declspec(dllexport) extern "C" void MyFunction();   // C4518

extern "C" void MyFunction();   // OK
```
