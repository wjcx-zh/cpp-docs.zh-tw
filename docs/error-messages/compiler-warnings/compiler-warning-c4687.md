---
title: 編譯器警告 C4687
ms.date: 11/04/2016
f1_keywords:
- C4687
helpviewer_keywords:
- C4687
ms.assetid: 2f28e0b1-7358-4c88-bd70-aad8f0aa004c
ms.openlocfilehash: 83f5c535f9cf252783110838c181c88c8b0096ee
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/20/2019
ms.locfileid: "69631600"
---
# <a name="compiler-warning-c4687"></a>編譯器警告 C4687

> '*class*': 密封抽象類別無法實作為介面 '*interface*'

## <a name="remarks"></a>備註

密封的抽象類別型通常只適用于保存靜態成員函式。

如需詳細資訊, 請參閱[abstract](../../extensions/abstract-cpp-component-extensions.md)和[sealed](../../extensions/sealed-cpp-component-extensions.md)。

預設會將 C4687 發行為錯誤。 您可以使用[warning](../../preprocessor/warning.md) pragma 來隱藏 C4687。 如果您確定要在密封的抽象類別型中執行介面, 則可以隱藏 C4687。

## <a name="example"></a>範例

下列範例會產生 C4687。

```cpp
// C4687.cpp
// compile with: /clr /c
interface class A {};

ref struct B sealed abstract : A {};   // C4687
ref struct C sealed : A {};   // OK
ref struct D abstract : A {};   // OK
```
