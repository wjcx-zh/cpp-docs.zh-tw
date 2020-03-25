---
title: ref new 和 gcnew  (C++/CLI 和 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- gcnew
- ref new
- gcnew_cpp
helpviewer_keywords:
- ref new keyword (C++)
- gcnew keyword [C++]
ms.assetid: 388a62da-c2df-4a94-a9a2-205b53e577da
ms.openlocfilehash: f7269a62d7899df4eb89f6dd9487310c0fda0b4d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181807"
---
# <a name="ref-new-gcnew--ccli-and-ccx"></a>ref new 和 gcnew  (C++/CLI 和 C++/CX)

**ref new** 可彙總關鍵字，其配置當物件變成無法存取時回收之型別的執行個體，並將控制代碼 ([^](handle-to-object-operator-hat-cpp-component-extensions.md)) 傳回配置的物件。

## <a name="all-runtimes"></a>所有執行階段

**ref new** 所配置型別的執行個體記憶體會自動取消配置。

如果無法配置記憶體，**ref new** 作業會擲回 `OutOfMemoryException`。

如需有關如何配置和取消配置記憶體給原生 C++ 類型的詳細資訊，請參閱 [new 和 delete 運算子](../cpp/new-and-delete-operators.md)。

## <a name="windows-runtime"></a>Windows 執行階段

使用 **ref new**，將記憶體配置給您想要自動管理其存留期的 Windows 執行階段物件。 當其參考計數歸零時 (參考的最後一個複本已離開範圍之後發生)，會自動取消配置物件。 如需詳細資訊，請參閱 [Ref 類別與結構](../cppcx/ref-classes-and-structs-c-cx.md)。

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

受控型別 (參考或實值型別) 的記憶體是由 **gcnew** 配置，並且是使用記憶體回收功能以取消配置。

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

以下範例會使用 **gcnew** 配置訊息物件。

```cpp
// mcppv2_gcnew_1.cpp
// compile with: /clr
ref struct Message {
   System::String^ sender;
   System::String^ receiver;
   System::String^ data;
};

int main() {
   Message^ h_Message  = gcnew Message;
  //...
}
```

以下範例會使用 **gcnew** 建立 boxed 實值型別，以便以類似參考類型的方法使用。

```cpp
// example2.cpp : main project file.
// compile with /clr
using namespace System;
value class Boxed {
    public:
        int i;
};
int main()
{
    Boxed^ y = gcnew Boxed;
    y->i = 32;
    Console::WriteLine(y->i);
    return 0;
}
```

```Output
32
```

## <a name="see-also"></a>另請參閱

[適用於.NET 和 UWP 的元件延伸模組](component-extensions-for-runtime-platforms.md)
