---
title: 編譯器錯誤 C2383 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2383
dev_langs:
- C++
helpviewer_keywords:
- C2383
ms.assetid: 6696221d-879c-477a-a0f3-a6edc15fd3d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9c529c22636f112291fa53b852899cad78dac589
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113223"
---
# <a name="compiler-error-c2383"></a>編譯器錯誤 C2383

'*符號*': 預設引數不允許在這個符號

C + + 編譯器不允許預設引數，函式的指標。

此程式碼在 Visual Studio 2005 之前的版本，Visual c + + 編譯器已接受，但現在會產生錯誤。 適用於所有版本的 Visual c + + 的程式碼，不要函式指標引數來指派預設值。

## <a name="example"></a>範例

下列範例會產生 C2383，，並顯示可能的解決方案：

```cpp
// C2383.cpp
// compile with: /c
void (*pf)(int = 0);   // C2383
void (*pf)(int);   // OK
```