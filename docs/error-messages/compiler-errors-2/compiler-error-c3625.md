---
title: 編譯器錯誤 C3625 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3625
dev_langs:
- C++
helpviewer_keywords:
- C3625
ms.assetid: fdf49f21-d6b1-42f4-9eec-23b04ae8b4aa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ebb7a94e807dbd8bbb9e5614f15d03e9b577858
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022587"
---
# <a name="compiler-error-c3625"></a>編譯器錯誤 C3625

'native_type'：不可以從 Managed 或 WinRT 類型 'type' 衍生原生類型

原生類別不可繼承自 Managed 或 WinRT 類別。 如需詳細資訊，請參閱 <<c0> [ 類別和結構](../../windows/classes-and-structs-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3625：

```
// C3625.cpp
// compile with: /clr /c
ref class B {};
class D : public B {};   // C3625 cannot inherit from a managed class
```
