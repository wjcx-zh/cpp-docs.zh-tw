---
title: 內容相關性關鍵字 (C++/CLI 和 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- internal_CPP
helpviewer_keywords:
- context-sensitive keywords
ms.assetid: e33da089-f434-44e9-8cce-4668d05a8939
ms.openlocfilehash: ca289a7ebd4578d5c67bb5d3e403d2a9a2756520
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516123"
---
# <a name="context-sensitive-keywords--ccli-and-ccx"></a>內容相關性關鍵字 (C++/CLI 和 C++/CX)

「內容相關性關鍵字」是只能在特定內容中辨識的語言元素。 在特定內容之外，內容相關性關鍵字可以是使用者定義的符號。

## <a name="all-runtimes"></a>所有執行階段

### <a name="remarks"></a>備註

下列是內容相關性關鍵字清單：

- [abstract](abstract-cpp-component-extensions.md)

- [delegate](delegate-cpp-component-extensions.md)

- [event](event-cpp-component-extensions.md)

- [finally](../dotnet/finally.md)

- [for each, in](../dotnet/for-each-in.md)

- [initonly](../dotnet/initonly-cpp-cli.md)

- `internal`

- [名稱](literal-cpp-component-extensions.md)

- [override](override-cpp-component-extensions.md)

- [屬性](property-cpp-component-extensions.md)

- [sealed](sealed-cpp-component-extensions.md)

- `where` ([泛型](generics-cpp-component-extensions.md)的一部分)

基於可讀性目的，您可能希望限制將內容相關性關鍵字當作使用者定義符號使用。

## <a name="windows-runtime"></a>Windows 執行階段

### <a name="remarks"></a>備註

(沒有此功能的平台特定備註。)

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>備註

(沒有此功能的平台特定備註。)

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

下列程式碼範例示範，在適當的內容中，可以使用 **property** 內容相關性關鍵字來定義屬性和變數。

```cpp
// context_sensitive_keywords.cpp
// compile with: /clr
public ref class C {
   int MyInt;
public:
   C() : MyInt(99) {}

   property int Property_Block {   // context-sensitive keyword
      int get() { return MyInt; }
   }
};

int main() {
   int property = 0;               // variable name
   C ^ MyC = gcnew C();
   property = MyC->Property_Block;
   System::Console::WriteLine(++property);
}
```

```Output
100
```

## <a name="see-also"></a>另請參閱

[適用於.NET 和 UWP 的元件延伸模組](component-extensions-for-runtime-platforms.md)