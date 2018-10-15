---
title: 即時線上關鍵字 (C + + /cli 和 C + + /CX) |Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal_CPP
dev_langs:
- C++
helpviewer_keywords:
- context-sensitive keywords
ms.assetid: e33da089-f434-44e9-8cce-4668d05a8939
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5d02939e61da4a247b46da5637c38d01e7990c49
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2018
ms.locfileid: "49327930"
---
# <a name="context-sensitive-keywords--ccli-and-ccx"></a>即時線上關鍵字 (C + + /cli 和 C + + /CX)

*即時線上關鍵字*是只在特定內容中辨識的語言項目。 在特定內容之外，內容相關性關鍵字可以是使用者定義的符號。

## <a name="all-runtimes"></a>所有執行階段

### <a name="remarks"></a>備註

下列是內容相關性關鍵字清單：

- [abstract](../windows/abstract-cpp-component-extensions.md)

- [delegate](../windows/delegate-cpp-component-extensions.md)

- [event](../windows/event-cpp-component-extensions.md)

- [finally](../dotnet/finally.md)

- [for each, in](../dotnet/for-each-in.md)

- [initonly](../dotnet/initonly-cpp-cli.md)

- `internal`

- [名稱](../windows/literal-cpp-component-extensions.md)

- [override](../windows/override-cpp-component-extensions.md)

- [屬性](../windows/property-cpp-component-extensions.md)

- [sealed](../windows/sealed-cpp-component-extensions.md)

- `where` (屬於[泛型](../windows/generics-cpp-component-extensions.md))

基於可讀性目的，您可能想要限制內容相關性關鍵字做為使用者定義的符號使用。

## <a name="windows-runtime"></a>Windows 執行階段

### <a name="remarks"></a>備註

(沒有這項功能的平台特定備註。)

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>備註

(沒有這項功能的平台特定備註。)

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

下列程式碼範例所示範的是，在適當的內容中，**屬性**內容相關性關鍵字可用來定義屬性和變數。

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

[適用於.NET 和 UWP 的元件擴充功能](../windows/component-extensions-for-runtime-platforms.md)