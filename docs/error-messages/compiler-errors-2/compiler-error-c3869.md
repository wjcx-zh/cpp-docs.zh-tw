---
title: 編譯器錯誤 C3869 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3869
dev_langs:
- C++
helpviewer_keywords:
- C3869
ms.assetid: 85b2ad72-95c1-4ed6-9761-6ef66c3802b7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 84b4ce32f6c4916e0e178d488bf725d257f4d887
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020158"
---
# <a name="compiler-error-c3869"></a>編譯器錯誤 C3869

gcnew 條件約束遺漏空參數清單 '（）'

`gcnew`特殊條件約束指定沒有空的參數清單。 請參閱[泛型類型參數的條件約束 (C + + /cli CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md)如需詳細資訊。

## <a name="example"></a>範例

下列範例會產生 C3869。

```
// C3869.cpp
// compile with: /c /clr
using namespace System;
generic <typename T>
where T : gcnew   // C3869
// try the following line instead
// where T : gcnew()
ref class List {};
```