---
title: 陣列 (C++/CLI 和 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- cli::array
- details::array
- lang::array
helpviewer_keywords:
- array keyword [C++]
- arrays [C++], multidimensional
- multidimensional arrays
- arrays [C++]
ms.assetid: 49445812-d775-4db1-a231-869598dbb955
ms.openlocfilehash: ecd8425bf7bcc9772d7b1327add79b89aea629a7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182236"
---
# <a name="arrays-ccli-and-ccx"></a>陣列 (C++/CLI 和 C++/CX)

C++/CX 中的 `Platform::Array<T>` 型別或 C++/CLI 中的 **array** 關鍵字會宣告指定型別和初始值的陣列。

## <a name="all-platforms"></a>所有平台

陣列必須透過在宣告中於右角括弧 (>) 後面使用物件控制代碼 (^) 修飾詞來宣告。
陣列的元素數目不是型別的一部分。 一個陣列變數可以參考不同大小的陣列。

不同於標準 C++，註標不是指標算術的同義字且不可交換。

如需陣列的詳細資訊，請參閱：

- [如何：在 C++/CLI 中使用陣列](../dotnet/how-to-use-arrays-in-cpp-cli.md)

- [變數引數清單 (...) (C++/CLI)](variable-argument-lists-dot-dot-dot-cpp-cli.md)

## <a name="windows-runtime"></a>Windows 執行階段

陣列是 `Platform` 命名空間的成員。 陣列可以只有一維。

### <a name="syntax"></a>語法

第一個語法範例會使用 **ref new** 彙總關鍵字來配置陣列。 第二個範例會宣告本機陣列。

```cpp
[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier =
    ref new[Platform::]Array<initialization-type> [{initialization-list [,...]}]

[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier =
    {initialization-list [,...]}
```

*qualifiers*<br/>
(選擇性) 下列一或多個儲存類別規範：[mutable](../cpp/mutable-data-members-cpp.md)、[volatile](../cpp/volatile-cpp.md)、[const](../cpp/const-cpp.md)、[extern](../cpp/using-extern-to-specify-linkage.md)、[static](../cpp/static-members-cpp.md)。

*array-type*<br/>
陣列變數的型別。 有效型別為 Windows 執行階段類別和基本型別、ref 類別和結構、實值類別和結構，以及原生指標 (`type*`)。

*rank*<br/>
(選擇性) 陣列的維度數目。 必須是 1。

*identifier*<br/>
陣列變數的名稱。

*initialization-type*<br/>
將陣列初始化的實值型別。 通常 *array-type* 和 *initialization-type* 是同一個型別。 不過，如果要從 *initialization-type* 轉換為 *array-type*，型別就會不一樣：例如，若 *initialization-type* 衍生自 *array-type*。

*initialization-list*<br/>
(選擇性) 大括號中以逗號分隔的值清單，其會將陣列的元素初始化。 例如，如果 *rank-size-list* 為 `(3)` (其會宣告含 3 個元素的一維陣列)，則 *initialization list* 可能是 `{1,2,3}`。

### <a name="remarks"></a>備註

您可以在編譯時間使用 `__is_ref_array(type)` 來偵測型別是否為參考計數陣列。 如需詳細資訊，請參閱[型別特性的編譯器支援](compiler-support-for-type-traits-cpp-component-extensions.md)。

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

### <a name="examples"></a>範例

下列範例會建立含 100 個元素的一維陣列。

```cpp
// cwr_array.cpp
// compile with: /ZW
using namespace Platform;
ref class MyClass {};
int main() {
   // one-dimensional array
   Array<MyClass^>^ My1DArray = ref new Array<MyClass^>(100);
   My1DArray[99] = ref new MyClass();
}
```

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="syntax"></a>語法

第一個語法範例會使用 **gcnew** 關鍵字來配置陣列。 第二個範例會宣告本機陣列。

```cpp
[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier =
    gcnew [cli::]array<initialization-type[,rank]>(rank-size-list[,...]) [{initialization-list [,...]}]

[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier =
    {initialization-list [,...]}
```

*qualifiers*<br/>
(選擇性) 下列一或多個儲存類別規範：[mutable](../cpp/mutable-data-members-cpp.md)、[volatile](../cpp/volatile-cpp.md)、[const](../cpp/const-cpp.md)、[extern](../cpp/using-extern-to-specify-linkage.md)、[static](../cpp/static-members-cpp.md)。

*array-type*<br/>
陣列變數的型別。 有效型別為 Windows 執行階段類別和基本型別、ref 類別和結構、實值類別和結構、原生指標 (`type*`)，以及原生 POD (Plain Old Data) 型別。

*rank*<br/>
(選擇性) 陣列的維度數目。 預設值為 1；最大值為 32。 陣列的每個維度本身就是一個陣列。

*identifier*<br/>
陣列變數的名稱。

*initialization-type*<br/>
將陣列初始化的實值型別。 通常 *array-type* 和 *initialization-type* 是同一個型別。 不過，如果要從 *initialization-type* 轉換為 *array-type*，型別就會不一樣：例如，若 *initialization-type* 衍生自 *array-type*。

*rank-size-list*<br/>
陣列中每個維度的大小清單 (以逗號分隔)。 或者，如果指定了 *initialization-list* 參數，編譯器就可以推斷每個維度的大小，並可省略 *rank-size-list*。

*initialization-list*<br/>
(選擇性) 大括號中以逗號分隔的值清單，其會將陣列的元素初始化。 或者，以逗號分隔的巢狀 *initialization-list* 項目清單，其會將多維陣列中的元素初始化。

例如，如果 *rank-size-list* 為 `(3)` (其會宣告含 3 個元素的一維陣列)，則 *initialization list* 可能是 `{1,2,3}`。 如果 *rank-size-list* 為 `(3,2,4)` (其會宣告一個三維陣列：第一個維度中有 3 個元素、第二個維度中有 2 個元素，且第三個元素中有 4 個元素)，則 *initialization-list* 可能是 `{{1,2,3},{0,0},{-5,10,-21,99}}`。

### <a name="remarks"></a>備註

**array** 位於[平台、預設與 cli 命名空間](platform-default-and-cli-namespaces-cpp-component-extensions.md)的命名空間。

如同標準 C++，陣列的索引會以零起始，而陣列會使用方括號 ([]) 來註標。 與標準 C++ 不同，多維度陣列的索引會指定於每個維度的索引清單中，而非每個維度的一組方括弧 ([]) 運算子內。 例如，*identifier*[*index1*, *index2*]，而非 *identifier*[*index1*][ *index2*]。

所有受控陣列都繼承自 `System::Array`。 `System::Array` 的任何方法或屬性都可直接套用至陣列變數。

當您配置元素型別指向受控類別的陣列時，會將元素初始化為 0。

當您配置元素型別為實值型別 `V` 的陣列時，會將 `V` 的預設建構函式套用至每個陣列元素。 如需詳細資訊，請參閱 [C++ 原生型別的 .NET Framework 對應項 (C++/CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)。

在編譯時間，您可以使用 `__is_ref_array(type)` 來偵測型別是否為 Common Language Runtime (CLR) 陣列。 如需詳細資訊，請參閱[型別特性的編譯器支援](compiler-support-for-type-traits-cpp-component-extensions.md)。

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

下列範例會建立一個含 100 個元素的一維陣列，以及一個三維陣列 (第一個維度中有 3 個元素、第二個維度中有 5 個元素，且第三個維度中有 6 個元素)。

```cpp
// clr_array.cpp
// compile with: /clr
ref class MyClass {};
int main() {
   // one-dimensional array
   array<MyClass ^> ^ My1DArray = gcnew array<MyClass ^>(100);
   My1DArray[99] = gcnew MyClass();

   // three-dimensional array
   array<MyClass ^, 3> ^ My3DArray = gcnew array<MyClass ^, 3>(3, 5, 6);
   My3DArray[0,0,0] = gcnew MyClass();
}
```

## <a name="see-also"></a>另請參閱

[適用於.NET 和 UWP 的元件延伸模組](component-extensions-for-runtime-platforms.md)
