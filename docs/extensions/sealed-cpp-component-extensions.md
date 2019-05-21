---
title: sealed (C++/CLI 和 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- sealed_cpp
- sealed
helpviewer_keywords:
- sealed keyword [C++]
ms.assetid: 3d0d688a-41aa-45f5-a25a-65c44206521e
ms.openlocfilehash: 493f6597d146480714848b37154cc8bacd37113a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516003"
---
# <a name="sealed--ccli-and-ccx"></a>sealed (C++/CLI 和 C++/CX)

**sealed** 是 ref 類別的內容相關性關鍵字，可指出無法覆寫虛擬成員，或者無法將型別當成基底類型使用。

> [!NOTE]
> ISO C++11 標準語言引進了 [final](../cpp/final-specifier.md) 關鍵字。 在標準類別上使用 **final**，並在 ref 類別上使用 **sealed**。

## <a name="all-runtimes"></a>所有執行階段

## <a name="syntax"></a>語法

```cpp
ref class identifier sealed {...};
virtual return-type identifier() sealed {...};
```

### <a name="parameters"></a>參數

*identifier*<br/>
函式或類別的名稱。

*return-type*<br/>
由函數傳回的類型。

## <a name="remarks"></a>備註

在第一個語法範例中，已密封類別。 在第二個範例中，已密封虛擬函式。

針對 ref 類別及其虛擬成員函式使用 **sealed** 關鍵字。 如需詳細資訊，請參閱[覆寫規範和原生編譯](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)。

您可以在編譯時期使用 `__is_sealed(type)` 型別特性來偵測是否已密封某個型別。 如需詳細資訊，請參閱[型別特性的編譯器支援](compiler-support-for-type-traits-cpp-component-extensions.md)。

**sealed** 是內容相關性關鍵字。  如需詳細資訊，請參閱[內容相關性關鍵字](context-sensitive-keywords-cpp-component-extensions.md)。

## <a name="windows-runtime"></a>Windows 執行階段

請參閱 [Ref 類別與結構](../cppcx/ref-classes-and-structs-c-cx.md)。

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

(這個語言功能沒有只適用於 Common Language Runtime 的備註。)

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

下列這個程式碼範例顯示 **sealed** 在虛擬成員上的效果。

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

[適用於.NET 和 UWP 的元件延伸模組](component-extensions-for-runtime-platforms.md)