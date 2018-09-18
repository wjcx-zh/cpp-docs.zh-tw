---
title: 編譯器錯誤 C3234 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3234
dev_langs:
- C++
helpviewer_keywords:
- C3234
ms.assetid: ebefc15a-e40d-424b-a3dd-d7e185d0ed7b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f701eb20743925913bf0eab754f2788e8bd3a9b6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46017039"
---
# <a name="compiler-error-c3234"></a>編譯器錯誤 C3234

泛型類別不可衍生自泛型類型參數

泛型類別不可繼承自泛型類型參數。

## <a name="example"></a>範例

下列範例會產生 C3234：

```
// C3234.cpp
// compile with: /clr /c
generic <class T>
public ref class C : T {};   // C3234
// try the following line instead
// public ref class C {};
```