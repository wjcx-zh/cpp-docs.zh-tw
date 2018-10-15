---
title: sealed (C + + /cli 和 C + + /CX) |Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- sealed_cpp
- sealed
dev_langs:
- C++
helpviewer_keywords:
- sealed keyword [C++]
ms.assetid: 3d0d688a-41aa-45f5-a25a-65c44206521e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 211428335473f677f520ee14ad688e5ffcbda8fd
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2018
ms.locfileid: "49327995"
---
# <a name="sealed--ccli-and-ccx"></a>sealed (C + + /cli 和 C + + /CX)

**密封**是 ref 類別的即時線上關鍵字表示，就無法覆寫虛擬成員，或類型不能用做基底型別。

> [!NOTE]
> ISO C + + 11 標準語言引進[最終](../cpp/final-specifier.md)關鍵字。 使用**最終**上標準的類別，並**密封**ref 類別上。

## <a name="all-runtimes"></a>所有執行階段

## <a name="syntax"></a>語法

```cpp
ref class identifier sealed {...};
virtual return-type identifier() sealed {...};
```

### <a name="parameters"></a>參數

*identifier*<br/>
函式或類別的名稱。

*傳回型別*<br/>
由函數傳回的類型。

## <a name="remarks"></a>備註

在第一個語法範例中，已密封類別。 在第二個範例中，已密封虛擬函式。

使用**密封**ref 類別和其虛擬成員函式的關鍵字。 如需詳細資訊，請參閱 <<c0> [ 覆寫規範和原生編譯](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)。

您可以在編譯時期偵測是否為型別密封格式，使用`__is_sealed(type)`類型特性。 如需詳細資訊，請參閱 <<c0> [ 類型特性的編譯器支援](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。

**密封**是內容相關性關鍵字。  如需詳細資訊，請參閱 <<c0> [ 即時線上關鍵字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。

## <a name="windows-runtime"></a>Windows 執行階段

請參閱[Ref 類別與結構](../cppcx/ref-classes-and-structs-c-cx.md)。

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

(這個語言功能沒有只適用於 Common Language Runtime 的備註。)

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

這個程式碼範例顯示的效果**密封**上的虛擬成員。

```cpp
// sealed_keyword.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
   virtual void g();
};

ref class X : I1 {
public:
   virtual void f() {
      System::Console::WriteLine("X::f override of I1::f");
   }

   virtual void g() sealed {
      System::Console::WriteLine("X::f override of I1::g");
   }
};

ref class Y : public X {
public:
   virtual void f() override {
      System::Console::WriteLine("Y::f override of I1::f");
   }

   /*  
   // the following override generates a compiler error
   virtual void g() override {
      System::Console::WriteLine("Y::g override of I1::g");
   }
   */
};

int main() {
   I1 ^ MyI = gcnew X;
   MyI -> f();
   MyI -> g();

   I1 ^ MyI2 = gcnew Y;
   MyI2 -> f();
}
```

```Output
X::f override of I1::f
X::f override of I1::g
Y::f override of I1::f
```

下一步的程式碼範例示範如何將類別標示為已密封。

```cpp
// sealed_keyword_2.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
};

ref class X sealed : I1 {
public:
   virtual void f() override {}
};

ref class Y : public X {   // C3246 base class X is sealed
public:
   virtual void f() override {}
};
```

## <a name="see-also"></a>另請參閱

[適用於.NET 和 UWP 的元件擴充功能](../windows/component-extensions-for-runtime-platforms.md)