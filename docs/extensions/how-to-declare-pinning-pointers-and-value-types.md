---
title: 作法：宣告固定指標和實值型別
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- value types, declaring
- pinning pointers
ms.assetid: 57c5ec8a-f85a-48c4-ba8b-a81268bcede0
ms.openlocfilehash: 901980c76aac5dd364f2fa2fae0e007f5d25f3d8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515733"
---
# <a name="how-to-declare-pinning-pointers-and-value-types"></a>作法：宣告固定指標和實值型別

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