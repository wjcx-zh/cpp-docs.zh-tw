---
title: 抽象  (C++/CLI 和 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- abstract
- abstract_cpp
helpviewer_keywords:
- abstract keyword [C++]
ms.assetid: cbae3408-0378-4ac8-b70d-c016b381a6d5
ms.openlocfilehash: d5060f1a0950b9b2ac2638b99ff157983944a3bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516163"
---
# <a name="abstract--ccli-and-ccx"></a>抽象  (C++/CLI 和 C++/CX)

**abstract** 關鍵字會宣告以下其中一個：

- 類型可以當做基底類型，但是類型本身無法具現化。

- 類型成員函式只能在衍生的類型中定義。

## <a name="all-platforms"></a>所有平台

### <a name="syntax"></a>語法

*class-declaration* *class-identifier* **abstract {}**

**virtual** *return-type* *member-function-identifier* **() abstract ;**

### <a name="remarks"></a>備註

第一個範例語法會將類別宣告為抽象。 *class-declaration* 元件可以是原生 C++ 宣告 (**class** 或 **struct**)，或如果指定了 `/ZW` 或 `/clr` 編譯器選項，則可以是 C++ 擴充功能宣告 (**ref class** 或 **ref struct**)。

第二個範例語法會將虛擬成員函式宣告為抽象。 將函式宣告為抽象等同於將它宣告為純虛擬函式。 將成員宣告為抽象也會造成含括類別被宣告為抽象。

原生與平台特定程式碼支援 **abstract** 關鍵字；也就是說，編譯它時可以選擇使用或不使用 `/clr` 或 `/ZW` 編譯器選項。

您可以在編譯時間偵測某個類型是否是具有 `__is_abstract(type)` 類型特徵的抽象類型。 如需詳細資訊，請參閱[類型特徵的編譯器支援](compiler-support-for-type-traits-cpp-component-extensions.md)。

**abstract** 關鍵字是視內容而有所區別的覆寫指定名稱。 如需視內容而有所區別的關鍵字的詳細資訊，請參閱[視內容而有所區別的關鍵字](context-sensitive-keywords-cpp-component-extensions.md)。 如需覆寫指定名稱的詳細資訊，請參閱[如何：在原生編譯中宣告覆寫指定名稱](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)。

## <a name="windows-runtime"></a>Windows 執行階段

如需詳細資訊，請參閱 [Ref 類別與結構](../cppcx/ref-classes-and-structs-c-cx.md)。

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

下列程式碼範例會產生錯誤，因為類別 `X` 標示為 **abstract**。

```cpp
// abstract_keyword.cpp
// compile with: /clr
ref class X abstract {
public:
   virtual void f() {}
};

int main() {
   X ^ MyX = gcnew X;   // C3622
}
```

下列程式碼範例會產生錯誤，因為它會具現化標示為 **abstract**的原生類別。 無論是否有 `/clr` 編譯器選項，都會發生此錯誤。

```cpp
// abstract_keyword_2.cpp
class X abstract {
public:
   virtual void f() {}
};

int main() {
   X * MyX = new X; // C3622: 'X': a class declared as 'abstract'
                    // cannot be instantiated. See declaration of 'X'}
```

下列程式碼範例會產生錯誤，因為函式 `f` 包括定義，但標示為 **abstract**。 在範例中的最後一個陳述式會顯示宣告抽象虛擬函式相當於宣告純虛擬函式。

```cpp
// abstract_keyword_3.cpp
// compile with: /clr
ref class X {
public:
   virtual void f() abstract {}   // C3634
   virtual void g() = 0 {}   // C3634
};
```

## <a name="see-also"></a>另請參閱

[適用於.NET 和 UWP 的元件延伸模組](component-extensions-for-runtime-platforms.md)
