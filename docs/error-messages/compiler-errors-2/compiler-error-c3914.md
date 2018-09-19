---
title: 編譯器錯誤 C3914 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3914
dev_langs:
- C++
helpviewer_keywords:
- C3914
ms.assetid: 8f3190e6-ee50-4916-9ecc-3b8748b2e1e7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7bb10652a6328bb8ddcc3a8e62755a960a7fc850
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029412"
---
# <a name="compiler-error-c3914"></a>編譯器錯誤 C3914

預設屬性不可為靜態

預設屬性宣告不正確。  如需詳細資訊，請參閱 <<c0> [ 如何： 使用屬性，在 C + + /cli CLI](../../dotnet/how-to-use-properties-in-cpp-cli.md)。

## <a name="example"></a>範例

下列範例會產生 C3914，並示範如何修正此問題。

```
// C3914.cpp
// compile with: /clr /c
ref struct X {
   static property int default[int] {   // C3914
   // try the following line instead
   // property int default[int] {
      int get(int) { return 0; }
      void set(int, int) {}
   }
};
```