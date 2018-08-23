---
title: interior_ptr (C + + /cli CLI) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- stdcli::language::interior_ptr
- interior_ptr_cpp
- interior_ptr
dev_langs:
- C++
helpviewer_keywords:
- interior_ptr keyword [C++]
ms.assetid: 25160f74-569e-492d-9e3c-67ece7486baa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c2745ed1a17311f92fda6fc61743fed65882b952
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601104"
---
# <a name="interiorptr-ccli"></a>interior_ptr (C++/CLI)

*內部指標*宣告指標在參考類型，而非物件本身。 內部指標可以指向參考控制代碼、實值類型、Boxed 類型控制代碼、Managed 類型的成員，或是指向 Managed 陣列的元素。

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

*cv_qualifier*  
**const**或是**volatile**限定詞。

*type*  
型別*初始設定式*。

*var*  
名稱**interior_ptr**變數。

*initializer*  
參考類型的成員，Managed 陣列的元素，或是其他任何可以指派至原生指標的物件。

### <a name="remarks"></a>備註

原生指標無法追蹤項目，因為它的位置會在 Managed 堆積上變更，這是記憶體回收行程移動物件的執行個體所造成。 為了讓指標正確參考執行個體，執行階段必須更新指標以指向新放置的物件。

**Interior_ptr**代表原生指標的功能超集。  因此，任何可以指派給原生指標的項目也可指派給**interior_ptr**。  內部指標可以執行與原生指標相同的一組作業，包括比較和指標算術。

內部指標只能在堆疊上宣告。  內部指標不可以宣告為類別的成員。

由於內部指標只會出現在堆疊上，因此採用內部指標的位址會產生 Unmanaged 指標。

**interior_ptr**具有隱含轉換成**bool**，這可讓您在條件陳述式中使用。

如需如何宣告內部指標指向無法移到記憶體回收堆積上之物件的資訊，請參閱[pin_ptr](../windows/pin-ptr-cpp-cli.md)。

**interior_ptr**位於 cli 命名空間。  請參閱[Platform、 default 和 cli 命名空間](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md)如需詳細資訊。

如需內部指標的詳細資訊，請參閱

- [如何：宣告及使用內部指標和 Managed 陣列 (C++/CLI)](../windows/how-to-declare-and-use-interior-pointers-and-managed-arrays-cpp-cli.md)

- [如何：使用 interior_ptr 關鍵字宣告實值型別 (C++/CLI)](../windows/how-to-declare-value-types-with-the-interior-ptr-keyword-cpp-cli.md)

- [如何：多載具有內部指標與原生指標的函式 (C++/CLI)](../windows/how-to-overload-functions-with-interior-pointers-and-native-pointers-cpp-cli.md)

- [如何：使用 const 關鍵字宣告內部指標 (C++/CLI)](../windows/how-to-declare-interior-pointers-with-the-const-keyword-cpp-cli.md)

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

[執行階段平台的元件延伸模組](../windows/component-extensions-for-runtime-platforms.md)