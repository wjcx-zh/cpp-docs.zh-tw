---
title: 編譯器錯誤 C2506 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2506
dev_langs:
- C++
helpviewer_keywords:
- C2506
ms.assetid: cfed21cd-2404-46f2-985e-d0c2c3820830
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4967c410dfdce781a4191c9ac848883228ba4d3a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093411"
---
# <a name="compiler-error-c2506"></a>編譯器錯誤 C2506

'member': '__declspec(modifier)' 無法套用至這個符號

您無法宣告每個處理程序或每個 appdomain managed 類別的靜態成員。

如需詳細資訊，請參閱 [appdomain](../../cpp/appdomain.md) 。

## <a name="example"></a>範例

下列範例會產生 C2506。

```
// C2506.cpp
// compile with: /clr /c
ref struct R {
   __declspec(process) static int n;   // C2506
   int o;   // OK
};
```