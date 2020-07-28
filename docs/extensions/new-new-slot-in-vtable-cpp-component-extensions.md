---
title: new (vtable 中的新位置) (C++/CLI 和 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 1a9a5704-f02f-46ae-ad65-f0f2b6dbabc3
ms.openlocfilehash: 29e43fe4c462fa6ac6523f8627abf923f02247a8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214239"
---
# <a name="new-new-slot-in-vtable--ccli-and-ccx"></a>new (vtable 中的新位置) (C++/CLI 和 C++/CX)

**`new`** 關鍵字表示虛擬成員會在 vtable 中取得新的位置。

## <a name="all-runtimes"></a>所有執行階段

(這個語言功能沒有適用所有執行階段的備註。)

## <a name="windows-runtime"></a>Windows 執行階段

Windows 執行階段不支援。

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>備註

在 `/clr` 編譯中， **`new`** 表示虛擬成員會在 vtable 中取得新的位置，而函式不會覆寫基類方法。

**`new`** 使 newslot 修飾詞加入至函數的 IL。  如需 newslot 的詳細資訊，請參閱：

- <xref:System.Reflection.MethodInfo.GetBaseDefinition?displayProperty=nameWithType>

- <xref:System.Reflection.MethodAttributes?displayProperty=nameWithType>

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

下列範例顯示的效果 **`new`** 。

```cpp
// newslot.cpp
// compile with: /clr
ref class C {
public:
   virtual void f() {
      System::Console::WriteLine("C::f() called");
   }

   virtual void g() {
      System::Console::WriteLine("C::g() called");
   }
};

ref class D : public C {
public:
   virtual void f() new {
      System::Console::WriteLine("D::f() called");
   }

   virtual void g() override {
      System::Console::WriteLine("D::g() called");
   }
};

ref class E : public D {
public:
   virtual void f() override {
      System::Console::WriteLine("E::f() called");
   }
};

int main() {
   D^ d = gcnew D;
   C^ c = gcnew D;

   c->f();   // calls C::f
   d->f();   // calls D::f

   c->g();   // calls D::g
   d->g();   // calls D::g

   D ^ e = gcnew E;
   e->f();   // calls E::f
}
```

```Output
C::f() called

D::f() called

D::g() called

D::g() called

E::f() called
```

## <a name="see-also"></a>另請參閱

[適用于 .NET 和 UWP 的元件擴充功能](component-extensions-for-runtime-platforms.md)<br/>
[覆寫規範](override-specifiers-cpp-component-extensions.md)
