---
title: 如何：宣告固定的指標和實值類型
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- value types, declaring
- pinning pointers
ms.assetid: 57c5ec8a-f85a-48c4-ba8b-a81268bcede0
ms.openlocfilehash: 88ef7e82161703a272a571392fd66e6055371c61
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181963"
---
# <a name="how-to-declare-pinning-pointers-and-value-types"></a>如何：宣告固定的指標和實值類型

實值類型可以隱含成為 Boxed。 然後您就可以宣告指向實值型別物件本身的 Pin 指標，並對 Boxed 實值型別使用 **pin_ptr**。

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

[pin_ptr (C++/CLI)](pin-ptr-cpp-cli.md)
