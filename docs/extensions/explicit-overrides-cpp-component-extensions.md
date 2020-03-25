---
title: 明確覆寫 (C++/CLI 和 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- overriding, override [C++]
ms.assetid: 4ec3eaf5-163b-4df8-8f16-7a2ec04c3d0f
ms.openlocfilehash: c199301794daaa140ede2fd99b0ae755cea70f97
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172369"
---
# <a name="explicit-overrides--ccli-and-ccx"></a>明確覆寫 (C++/CLI 和 C++/CX)

本主題討論如何明確覆寫基底類別或介面的成員。 具名 (明確) 覆寫只應用於以具有不同名稱的衍生方法來覆寫方法。

## <a name="all-runtimes"></a>所有執行階段

### <a name="syntax"></a>語法

```cpp
overriding-function-declarator = type::function [,type::function] { overriding-function-definition }
overriding-function-declarator = function { overriding-function-definition }
```

### <a name="parameters"></a>參數

*overriding-function-declarator*<br/>
覆寫函式的傳回型別、名稱和引數清單。  請注意，覆寫函式的名稱不需與要覆寫的函式的名稱一樣。

*type*<br/>
包含要覆寫之函式的基底型別。

*函數*<br/>
要覆寫之一或多個函式名稱的逗號分隔清單。

*overriding-function-definition*<br/>
定義覆寫函式的函式主體陳述式。

### <a name="remarks"></a>備註

使用明確覆寫來建立方法簽章的別名，或為具有相同簽章的方法提供不同的執行方式。

如需修改繼承型別和繼承型別成員之行為的相關資訊，請參閱[覆寫指定名稱](override-specifiers-cpp-component-extensions.md)。

## <a name="windows-runtime"></a>Windows 執行階段

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>備註

如需在機器碼或使用 `/clr:oldSyntax` 編譯的程式碼中進行明確覆寫的相關資訊，請參閱[明確覆寫](../cpp/explicit-overrides-cpp.md)。

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

下列程式碼範例示範如何在不使用明確覆的情況下，於基底介面中簡單且隱含地覆寫及實作成員。

```cpp
// explicit_override_1.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
};

ref class X : public I1 {
public:
   virtual void f() {
      System::Console::WriteLine("X::f override of I1::f");
   }
};

int main() {
   I1 ^ MyI = gcnew X;
   MyI -> f();
}
```

```Output
X::f override of I1::f
```

下列程式碼範例示範如何使用明確覆寫語法，透過一般簽章來實作所有介面成員。

```cpp
// explicit_override_2.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
};

interface struct I2 {
   virtual void f();
};

ref struct X : public I1, I2 {
   virtual void f() = I1::f, I2::f {
      System::Console::WriteLine("X::f override of I1::f and I2::f");
   }
};

int main() {
   I1 ^ MyI = gcnew X;
   I2 ^ MyI2 = gcnew X;
   MyI -> f();
   MyI2 -> f();
}
```

```Output
X::f override of I1::f and I2::f
X::f override of I1::f and I2::f
```

下列程式碼範例示範函式覆寫如何具備與其所實作之函式不同的名稱。

```cpp
// explicit_override_3.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
};

ref class X : public I1 {
public:
   virtual void g() = I1::f {
      System::Console::WriteLine("X::g");
   }
};

int main() {
   I1 ^ a = gcnew X;
   a->f();
}
```

```Output
X::g
```

下列程式碼範例示範實作型別安全集合的明確介面實作。

```cpp
// explicit_override_4.cpp
// compile with: /clr /LD
using namespace System;
ref class R : ICloneable {
   int X;

   virtual Object^ C() sealed = ICloneable::Clone {
      return this->Clone();
   }

public:
   R() : X(0) {}
   R(int x) : X(x) {}

   virtual R^ Clone() {
      R^ r = gcnew R;
      r->X = this->X;
      return r;
   }
};
```

## <a name="see-also"></a>另請參閱

[適用於.NET 和 UWP 的元件延伸模組](component-extensions-for-runtime-platforms.md)
