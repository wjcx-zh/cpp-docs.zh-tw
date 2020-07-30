---
title: __raise
ms.date: 11/04/2016
f1_keywords:
- __raise
- __raise_cpp
helpviewer_keywords:
- __raise keyword [C++]
ms.assetid: 6f1ae418-5f0f-48b6-9f6e-8ea7e66b239a
ms.openlocfilehash: db6ba1693e4d3144b95530646b061e9cd7a58a5a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227123"
---
# <a name="__raise"></a>__raise

強調事件的呼叫位置。

## <a name="syntax"></a>語法

```
__raise method-declarator;
```

## <a name="remarks"></a>備註

在 Managed 程式碼中，只能從已定義的類別內引發事件。 如需詳細資訊，請參閱[事件](../extensions/event-cpp-component-extensions.md)。

**`__raise`** 如果您呼叫非事件，關鍵字會導致發出錯誤。

> [!NOTE]
> 樣板類別或結構不能包含事件。

## <a name="example"></a>範例

```cpp
// EventHandlingRef_raise.cpp
struct E {
   __event void func1();
   void func1(int) {}

   void func2() {}

   void b() {
      __raise func1();
      __raise func1(1);  // C3745: 'int Event::bar(int)':
                         // only an event can be 'raised'
      __raise func2();   // C3745
   }
};

int main() {
   E e;
   __raise e.func1();
   __raise e.func1(1);  // C3745
   __raise e.func2();   // C3745
}
```

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)<br/>
[事件處理](../cpp/event-handling.md)<br/>
[執行階段平台的元件延伸模組](../extensions/component-extensions-for-runtime-platforms.md)
