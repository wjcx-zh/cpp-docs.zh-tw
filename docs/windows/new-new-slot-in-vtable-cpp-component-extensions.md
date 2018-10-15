---
title: 新 (新 vtable 中的位置） (C + + /cli 和 C + + /CX) |Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 1a9a5704-f02f-46ae-ad65-f0f2b6dbabc3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 48351903b7827f4ad9e6d63824658e4f44e047e0
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2018
ms.locfileid: "49327735"
---
# <a name="new-new-slot-in-vtable--ccli-and-ccx"></a>新 (新 vtable 中的位置） (C + + /cli 和 C + + /CX)

**新**關鍵字會指出虛擬成員會取得 vtable 中的新位置。

## <a name="all-runtimes"></a>所有執行階段

(這個語言功能沒有適用所有執行階段的備註。)

## <a name="windows-runtime"></a>Windows 執行階段

不支援 Windows 執行階段。

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>備註

在 `/clr`編譯時，**新**表示虛擬成員會取得 vtable 中的新位置; 此函式不覆寫基底類別方法。

**新**導致 newslot 修飾詞新增至函式的 IL。  如需 newslot 的詳細資訊，請參閱：

- [MethodInfo.GetBaseDefinition 方法](https://msdn.microsoft.com/library/system.reflection.methodinfo.getbasedefinition.aspx)

- [MethodAttributes 列舉](https://msdn.microsoft.com/library/system.reflection.methodattributes.aspx)

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

下列範例顯示的效果**新**。

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

[適用於.NET 和 UWP 的元件擴充功能](../windows/component-extensions-for-runtime-platforms.md)<br/>

[覆寫規範](../windows/override-specifiers-cpp-component-extensions.md)