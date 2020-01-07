---
title: 編譯器錯誤 C2081
ms.date: 11/04/2016
f1_keywords:
- C2081
helpviewer_keywords:
- C2081
ms.assetid: 7db9892d-364d-4178-a49d-f8398ece09a0
ms.openlocfilehash: 2e8e813d8162b9a191b6760366b52783e7c8609f
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301986"
---
# <a name="compiler-error-c2081"></a>編譯器錯誤 C2081

' identifier '：型式參數清單中的名稱不合法

識別碼造成語法錯誤。

此錯誤可能是因為正式參數清單使用舊樣式所造成。 您必須在正式參數清單中指定正式參數的類型。

下列範例會產生 C2081：

```c
// C2081.c
void func( int i, j ) {}  // C2081, no type specified for j
```

可能的解決方案：

```c
// C2081b.c
// compile with: /c
void func( int i, int j ) {}
```
