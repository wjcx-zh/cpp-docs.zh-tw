---
title: 編譯器錯誤 C3625
ms.date: 11/04/2016
f1_keywords:
- C3625
helpviewer_keywords:
- C3625
ms.assetid: fdf49f21-d6b1-42f4-9eec-23b04ae8b4aa
ms.openlocfilehash: 83b6756c75f90380024a8f31df62290bed1f7738
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761903"
---
# <a name="compiler-error-c3625"></a>編譯器錯誤 C3625

'native_type'：不可以從 Managed 或 WinRT 類型 'type' 衍生原生類型

原生類別不可繼承自 Managed 或 WinRT 類別。 如需詳細資訊，請參閱[類別與結構](../../extensions/classes-and-structs-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3625：

```cpp
// C3625.cpp
// compile with: /clr /c
ref class B {};
class D : public B {};   // C3625 cannot inherit from a managed class
```
