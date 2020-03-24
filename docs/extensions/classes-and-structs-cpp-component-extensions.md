---
title: ref 類別和 ref 結構 (C++/CLI 和 C++/CX)
ms.date: 05/30/2019
ms.topic: reference
f1_keywords:
- ref class
- value class
- ref struct
- value struct
helpviewer_keywords:
- ref class keyword [C++]
- value class keyword [C++]
- value struct keyword [C++]
- ref struct keyword [C++]
ms.assetid: 5c360764-b229-49c6-9357-66213afbc372
ms.openlocfilehash: 78cf7cf16c4ccf29f72038fd79c5d7a1689c05ac
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172564"
---
# <a name="ref-class-and-ref-struct--ccli-and-ccx"></a>ref 類別和 ref 結構 (C++/CLI 和 C++/CX)

**ref 類別**或 **ref 結構** 延伸模組會宣告「物件存留期」會自動管理的類別或結構。 當物件無法再存取或超出範圍時，就會釋放記憶體。

## <a name="all-runtimes"></a>所有執行階段

### <a name="syntax"></a>語法

```cpp
      class_access
      ref class
      name
      modifier :  inherit_accessbase_type {};
class_accessref structnamemodifier :  inherit_accessbase_type {};
class_accessvalue classnamemodifier :  inherit_accessbase_type {};
class_accessvalue structnamemodifier :  inherit_accessbase_type {};
```

### <a name="parameters"></a>參數

*class_access*<br/>
(選擇性) 組件外部的類別或結構的存取範圍。 可能的值為 **public** 和 **private** (**private** 為預設值)。 巢狀類別或結構不可以有*class_access* 指定名稱。

*name*<br/>
類別或結構的名稱。

*modifier*<br/>
(選擇性) [abstract](abstract-cpp-component-extensions.md) 和 [sealed](sealed-cpp-component-extensions.md) 為有效的修飾詞。

*inherit_access*<br/>
(選擇性) *base_interface* 的存取範圍。 唯一允許的存取範圍是 **public** (**public** 為預設值)。

*base_type*<br/>
(選擇性) 基底類型。 不過，值類型無法做為基底類型。

如需詳細資訊，請參閱 Windows 執行階段和 Common Language Runtime 區段中，此參數的語言特定描述。

### <a name="remarks"></a>備註

使用 **ref 類別**或**類別**宣告之物件的預設成員存取範圍是 **private**。 此外，使用 **ref 結構** 或 **value 結構** 宣告之物件的預設成員存取範圍是 **public**。

當參考類型繼承自另一個參考類型時，必須以 [override](override-cpp-component-extensions.md) 明確覆寫，或以 [new (vtable 中的新位置)](new-new-slot-in-vtable-cpp-component-extensions.md) 隱藏基底類別中的虛擬函式。 必須將衍生的類別函式明確標示為 **virtual**。

若要在編譯時間偵測某個類型為 **ref 類別**或 **ref 結構**，或是**實值類別**或**實值結構**，請使用 `__is_ref_class (type)`、`__is_value_class (type)` 或 `__is_simple_value_class (type)`。 如需詳細資訊，請參閱[型別特性的編譯器支援](compiler-support-for-type-traits-cpp-component-extensions.md)。

如需類別和結構的詳細資訊，請參閱

- [具現化類別和結構](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)

- [參考型別的 C++ 堆疊語意](../dotnet/cpp-stack-semantics-for-reference-types.md)

- [類別、結構和等位](../cpp/classes-and-structs-cpp.md)

- [如何：定義和使用類別和結構（C++/cli）中的析構函數和完成項](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)

- [使用者定義的運算子 (C++/CLI)](../dotnet/user-defined-operators-cpp-cli.md)

- [使用者定義轉換 (C++/CLI)](../dotnet/user-defined-conversions-cpp-cli.md)

- [如何：包裝原生類別以便讓 C# 使用](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)

- [泛型類別 (C++/CLI)](generic-classes-cpp-cli.md)

## <a name="windows-runtime"></a>Windows 執行階段

### <a name="remarks"></a>備註

請參閱 [Ref 類別與結構](../cppcx/ref-classes-and-structs-c-cx.md)和[實值類別與結構](../cppcx/value-classes-and-structs-c-cx.md)。

### <a name="parameters"></a>參數

*base_type*<br/>
(選擇性) 基底類型。 **ref 類別**或 **ref 結構**可以繼承自零或多個介面，以及零或一種 **ref** 類型。 **實值類別**或**實值結構**只可以繼承自零或多個介面。

當您使用 **ref 類別**或 **ref 結構**關鍵字宣告物件時，控制代碼可針對物件存取物件；也就是物件的參考計數器指標。 當宣告的變數超出範圍時，編譯器會自動刪除基礎物件。 當物件做為呼叫中的參數使用，或是儲存在變數中時，實際上是傳遞或儲存該物件的控制代碼。

當您使用**實值類別**或**實值結構**關鍵字宣告物件時，不會監督所宣告物件的物件存留期。 此物件類似任何其他標準 C++ 類別或結構。

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>備註

下表列出 C++/CLI 特有的**所有執行階段**區段中所顯示語法的差異。

### <a name="parameters"></a>參數

*base_type*<br/>
(選擇性) 基底類型。 **ref 類別**或 **ref 結構**可以繼承自零或多個受控介面，以及零或一種 ref 類型。 **實值類別**或**實值結構**只可以繼承自零或多個受控介面。

**ref 類別**和 **ref 結構**關鍵字會告訴編譯器：類別或結構是在堆積上配置。 當物件做為呼叫中的參數使用，或是儲存在變數中時，實際上是傳遞或儲存該物件的參考。

**實值類別**和**實值結構**關鍵字會告訴編譯器，所配置類別或結構的值已傳遞給函式或儲存在成員中。

### <a name="requirements"></a>需求

編譯器選項：`/clr`

## <a name="see-also"></a>另請參閱

[適用於.NET 和 UWP 的元件延伸模組](component-extensions-for-runtime-platforms.md)
