---
title: 編譯器錯誤 C3139 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3139
dev_langs:
- C++
helpviewer_keywords:
- C3139
ms.assetid: 95c92263-10ac-4ff3-b385-6312dd92adbc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ac401381dffab11ddb59eb05a5cafe13373d7791
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026448"
---
# <a name="compiler-error-c3139"></a>編譯器錯誤 C3139

'struct': 無法匯出 UDT 沒有成員

您嘗試將套用[匯出](../../windows/export.md)屬性設定為空的 UDT （使用者定義型別）。 例如: 

```
// C3139.cpp
#include "unknwn.h"
[emitidl];
[module(name=xx)];

[export] struct MyStruct {   // C3139 empty type
};
int main(){}
```