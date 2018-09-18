---
title: 編譯器錯誤 C3183 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3183
dev_langs:
- C++
helpviewer_keywords:
- C3183
ms.assetid: dbd0f020-c739-43c9-947e-9ce21537331b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 76822882f1b0ac2da2e18131b47d5730820f4751
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020182"
---
# <a name="compiler-error-c3183"></a>編譯器錯誤 C3183

無法在 Managed 或 WinRT 類型 'type' 內部定義未命名的類別、結構或等位

內嵌在 Managed 或 WinRT 類型中的類型必須命名。

下列範例會產生 C3183：

```
// C3183a.cpp
// compile with: /clr /c
ref class Test
{
   ref class
   {  // C3183, delete class or name it
      int a;
      int b;
   };
};
```
