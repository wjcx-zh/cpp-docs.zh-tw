---
title: 編譯器錯誤 C2506
ms.date: 11/04/2016
f1_keywords:
- C2506
helpviewer_keywords:
- C2506
ms.assetid: cfed21cd-2404-46f2-985e-d0c2c3820830
ms.openlocfilehash: 02f0a81204c4bc1c41111d32bae1c6946dee09ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62164861"
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