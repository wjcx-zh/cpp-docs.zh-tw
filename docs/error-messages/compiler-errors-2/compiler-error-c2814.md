---
title: 編譯器錯誤 C2814 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2814
dev_langs:
- C++
helpviewer_keywords:
- C2814
ms.assetid: 7d165136-a08b-4497-a76d-60a21bb19404
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef85e143b13ea5184235676179e33b387f751aa8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46046572"
---
# <a name="compiler-error-c2814"></a>編譯器錯誤 C2814

'member'：原生類型不可以巢狀方式置於 Managed 或 WinRT 類型 'type' 中

## <a name="example"></a>範例

原生類型不可以巢狀方式置於 CLR 或 WinRT 類型中。 下列範例會產生 C2814，並示範如何修正此問題。

```
// C2814.cpp
// compile with: /clr /c
ref class A {
   class B {};   // C2814
   ref class C {};   // OK
};
```
