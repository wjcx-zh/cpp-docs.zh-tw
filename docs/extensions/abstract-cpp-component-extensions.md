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
ms.openlocfilehash: 1e729589f78c56111717a87a27f9c7370dca7b90
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214291"
---
# <a name="abstract--ccli-and-ccx"></a>抽象  (C++/CLI 和 C++/CX)

**abstract** 關鍵字會宣告以下其中一個：

- 類型可以當做基底類型，但是類型本身無法具現化。

- 類型成員函式只能在衍生的類型中定義。

## <a name="all-platforms"></a>所有平台

### <a name="syntax"></a>語法

*class-declaration* *class-identifier* **abstract {}**

**`virtual`** 傳回*型別**成員函式-identifier* **（） abstract;**

### <a name="remarks"></a>備註

第一個範例語法會將類別宣告為抽象。 如果*class-declaration*指定了或編譯器選項，類別宣告元件可以是原生 c + + 宣告（** `class` * * * * 或 **`struct`** ），或是 c + + 擴充**功能宣告（ref 類別 * * 或**ref struct**） `/ZW` `/clr` 。

第二個範例語法會將虛擬成員函式宣告為抽象。 將函式宣告為抽象等同於將它宣告為純虛擬函式。 將成員宣告為抽象也會造成含括類別被宣告為抽象。

原生與平台特定程式碼支援 **abstract** 關鍵字；也就是說，編譯它時可以選擇使用或不使用 `/clr` 或 `/ZW` 編譯器選項。

您可以在編譯時間偵測某個類型是否是具有 `__is_abstract(type)` 類型特徵的抽象類型。 如需詳細資訊，請參閱[類型特徵的編譯器支援](compiler-support-for-type-traits-cpp-component-extensions.md)。

**abstract** 關鍵字是視內容而有所區別的覆寫指定名稱。 如需視內容而有所區別的關鍵字的詳細資訊，請參閱[視內容而有所區別的關鍵字](context-sensitive-keywords-cpp-component-extensions.md)。 如需覆寫規範的詳細資訊，請參閱[如何：在原生編譯中](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)宣告覆寫規範。

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

[適用于 .NET 和 UWP 的元件擴充功能](component-extensions-for-runtime-platforms.md)
