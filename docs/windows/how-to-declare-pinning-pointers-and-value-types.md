---
title: 如何： 宣告 Pin 指標和實值型別 |Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- value types, declaring
- pinning pointers
ms.assetid: 57c5ec8a-f85a-48c4-ba8b-a81268bcede0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2e724e468ec9c95a2404ea70c8666bc6880207ca
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2018
ms.locfileid: "49327605"
---
# <a name="how-to-declare-pinning-pointers-and-value-types"></a>如何：宣告固定的指標和實值類型

實值類型可以隱含成為 Boxed。 然後，您可以宣告 pin 指標值的型別物件本身以及使用**pin_ptr**為 boxed 實的值型別。

## <a name="example"></a>範例

### <a name="code"></a>程式碼

```cpp
// pin_ptr_value.cpp
// compile with: /clr
value struct V {
   int i;
};

int main() {
   V ^ v = gcnew V;   // imnplicit boxing
   v->i=8;
   System::Console::WriteLine(v->i);
   pin_ptr<V> mv = &*v;
   mv->i = 7;
   System::Console::WriteLine(v->i);
   System::Console::WriteLine(mv->i);
}
```

```Output
8
7
7
```

## <a name="see-also"></a>另請參閱

[pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)