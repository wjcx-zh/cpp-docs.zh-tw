---
title: interior_ptr (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- stdcli::language::interior_ptr
- interior_ptr_cpp
- interior_ptr
helpviewer_keywords:
- interior_ptr keyword [C++]
ms.assetid: 25160f74-569e-492d-9e3c-67ece7486baa
ms.openlocfilehash: 264ac0a56996b0dcbeeb64246623eca1a3fc73ff
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172148"
---
# <a name="interior_ptr-ccli"></a>interior_ptr (C++/CLI)

「內部指標」會宣告指向參考型別內部的指標，而不是指向物件本身。 內部指標可以指向參考控制代碼、實值類型、Boxed 類型控制代碼、Managed 類型的成員，或是指向 Managed 陣列的元素。

## <a name="all-runtimes"></a>所有執行階段

(這個語言功能沒有適用所有執行階段的備註。)

## <a name="windows-runtime"></a>Windows 執行階段

(這個語言功能沒有只適用於 Windows 執行階段的備註。)

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

下列語法範例將示範內部指標。

### <a name="syntax"></a>語法

```cpp
cli::interior_ptr<cv_qualifier type> var = &initializer;
```

### <a name="parameters"></a>參數

*cv_qualifier*<br/>
**const** 或 **volatile** 限定詞。

*type*<br/>
*initializer* 的型別。

*var*<br/>
**interior_ptr** 變數的名稱。

*initializer*<br/>
參考類型的成員，Managed 陣列的元素，或是其他任何可以指派至原生指標的物件。

### <a name="remarks"></a>備註

原生指標無法追蹤項目，因為它的位置會在 Managed 堆積上變更，這是記憶體回收行程移動物件的執行個體所造成。 為了讓指標正確參考執行個體，執行階段必須更新指標以指向新放置的物件。

**interior_ptr** 代表原生指標功能的超集。  因此，任何可指派給原生指標的項目也都能指派給 **interior_ptr**。  內部指標可以執行與原生指標相同的一組作業，包括比較和指標算術。

內部指標只能在堆疊上宣告。  內部指標不可以宣告為類別的成員。

由於內部指標只會出現在堆疊上，因此採用內部指標的位址會產生 Unmanaged 指標。

**interior_ptr** 具有 **bool** 的隱含轉換，因此能夠在條件陳述式中使用。

如需如何宣告內部指標，讓它指向無法在記憶體回收堆積上移動之物件的相關資訊，請參閱 [pin_ptr](pin-ptr-cpp-cli.md)。

**interior_ptr** 位於 cli 命名空間。  如需詳細資訊，請參閱[平台、預設與 cli 命名空間](platform-default-and-cli-namespaces-cpp-component-extensions.md)。

如需內部指標的詳細資訊，請參閱

- [如何：宣告及使用內部指標和 Managed 陣列 (C++/CLI)](how-to-declare-and-use-interior-pointers-and-managed-arrays-cpp-cli.md)

- [如何：使用 interior_ptr 關鍵字宣告實值型別 (C++/CLI)](how-to-declare-value-types-with-the-interior-ptr-keyword-cpp-cli.md)

- [如何：多載具有內部指標與原生指標的函式 (C++/CLI)](how-to-overload-functions-with-interior-pointers-and-native-pointers-cpp-cli.md)

- [如何：使用 const 關鍵字宣告內部指標 (C++/CLI)](how-to-declare-interior-pointers-with-the-const-keyword-cpp-cli.md)

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

下列範例將示範如何宣告內部指標並應用到參考類型中。

```cpp
// interior_ptr.cpp
// compile with: /clr
using namespace System;

ref class MyClass {
public:
   int data;
};

int main() {
   MyClass ^ h_MyClass = gcnew MyClass;
   h_MyClass->data = 1;
   Console::WriteLine(h_MyClass->data);

   interior_ptr<int> p = &(h_MyClass->data);
   *p = 2;
   Console::WriteLine(h_MyClass->data);

   // alternatively
   interior_ptr<MyClass ^> p2 = &h_MyClass;
   (*p2)->data = 3;
   Console::WriteLine((*p2)->data);
}
```

```Output
1
2
3
```

## <a name="see-also"></a>另請參閱

[適用於.NET 和 UWP 的元件延伸模組](component-extensions-for-runtime-platforms.md)
