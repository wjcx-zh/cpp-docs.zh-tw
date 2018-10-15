---
title: 陣列 (C + + /cli 和 C + + /CX) |Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- cli::array
- details::array
- lang::array
dev_langs:
- C++
helpviewer_keywords:
- array keyword [C++]
- arrays [C++], multidimensional
- multidimensional arrays
- arrays [C++]
ms.assetid: 49445812-d775-4db1-a231-869598dbb955
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b1a1f977e15d80d631799d8a9e101a8c85e3aaf1
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2018
ms.locfileid: "49328099"
---
# <a name="arrays-ccli-and-ccx"></a>陣列 (C + + /cli 和 C + + /CX)

`Platform::Array<T>`型別在 C + + /CX 中，或有**陣列**關鍵字在 C + + /cli CLI 中，宣告指定型別和初始值的陣列。

## <a name="all-platforms"></a>所有平台

陣列必須宣告之後宣告中的右角括弧 (>) 使用以物件控制代碼 (^) 修飾詞。
陣列的元素數目不是類型的一部分。 一個陣列變數可以參考不同大小的陣列。

不同於標準 c + + 中，註標不是指標算術的同義字，而且不交替運算。

如需陣列的詳細資訊，請參閱：

- [如何：在 C++/CLI 中使用陣列](../dotnet/how-to-use-arrays-in-cpp-cli.md)

- [變數引數清單 (...) (C++/CLI)](../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)

## <a name="windows-runtime"></a>Windows 執行階段

陣列是屬於`Platform`命名空間。 陣列可以是只有一維。

### <a name="syntax"></a>語法

第一個語法的範例會使用**ref 新**彙總的關鍵字，可配置的陣列。 第二個範例會宣告本機陣列。

```cpp
[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier = 
    ref new[Platform::]Array<initialization-type> [{initialization-list [,...]}]

[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier = 
    {initialization-list [,...]}
```

*限定詞*<br/>
（選擇性）一或多個這些儲存類別規範：[可變](../cpp/mutable-data-members-cpp.md)， [volatile](../cpp/volatile-cpp.md)， [const](../cpp/const-cpp.md)， [extern](../cpp/using-extern-to-specify-linkage.md)，[靜態](../cpp/static-members-cpp.md).

*陣列類型*<br/>
陣列變數的型別。 有效的類型為 Windows 執行階段類別和基本類型、 ref 類別和結構、 實值類別和結構和原生指標 (`type*`)。

*rank*<br/>
（選擇性）陣列維度的數目。 必須是 1。

*identifier*<br/>
陣列變數的名稱。

*初始化型別*<br/>
初始化陣列值型別。 通常*陣列型別*並*初始化型別*都是相同的型別。 不過，類型可以不同的轉換是否*初始化型別*要*陣列型別*— 比方說，如果*初始化型別*衍生自*陣列型別*。

*初始設定式清單*<br/>
（選擇性）初始化陣列的元素的大括號中值的逗號分隔清單。 例如，如果*陣序大小清單*已`(3)`，其中宣告的 3 個元素，一維陣列*初始化清單*可能`{1,2,3}`。

### <a name="remarks"></a>備註

您可以在編譯時期偵測類型是否具有參考計數陣列`__is_ref_array(type)`。 如需詳細資訊，請參閱 <<c0> [ 類型特性的編譯器支援](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

### <a name="examples"></a>範例

下列範例會建立一維陣列，具有 100 個元素。

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

第一個語法的範例會使用**gcnew**關鍵字來配置陣列。 第二個範例會宣告本機陣列。

```cpp
[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier = 
    gcnew [cli::]array<initialization-type[,rank]>(rank-size-list[,...]) [{initialization-list [,...]}]

[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier = 
    {initialization-list [,...]}
```

*限定詞*<br/>
（選擇性）一或多個這些儲存類別規範：[可變](../cpp/mutable-data-members-cpp.md)， [volatile](../cpp/volatile-cpp.md)， [const](../cpp/const-cpp.md)， [extern](../cpp/using-extern-to-specify-linkage.md)，[靜態](../cpp/static-members-cpp.md).

*陣列類型*<br/>
陣列變數的型別。 有效的類型為 Windows 執行階段類別和基本類型、 ref 類別和結構、 實值類別與結構，原生指標 (`type*`)，和 POD （一般舊資料） 的原生類型。

*rank*<br/>
（選擇性）陣列維度的數目。 預設值為 1;最大值為 32。 每個維度本身是陣列的一個陣列。

*identifier*<br/>
陣列變數的名稱。

*初始化型別*<br/>
初始化陣列值型別。 通常*陣列型別*並*初始化型別*都是相同的型別。 不過，類型可以不同的轉換是否*初始化型別*要*陣列型別*— 比方說，如果*初始化型別*衍生自*陣列型別*。

*陣序大小清單*<br/>
陣列中每個維度的大小以逗號分隔清單。 或者，如果*初始設定式清單*參數指定，則編譯器可以推斷每個維度大小並*陣序大小清單*可以省略。

*初始設定式清單*<br/>
（選擇性）初始化陣列的元素的大括號中值的逗號分隔清單。 或以逗號分隔清單的巢狀*初始設定式清單*初始化多維陣列中的元素的項目。

例如，如果*陣序大小清單*已`(3)`，其中宣告的 3 個元素，一維陣列*初始化清單*可能`{1,2,3}`。 如果*陣序大小清單*已`(3,2,4)`，其中宣告中的第一個維度，2 個項目中第二個，在第三，4 個元素的 3 個元素的三維陣列*初始化清單*可能是`{{1,2,3},{0,0},{-5,10,-21,99}}`。)

### <a name="remarks"></a>備註

**陣列**處於[Platform、 default 和 cli 命名空間](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md)命名空間。

如同標準的 c + + 陣列的索引是以零起始，而使用方括號 ([]) 註標的陣列是。 不同於標準 c + + 中，而不是一組方括弧 ([]) 運算子，針對每個維度的每個維度的索引的清單中指定多維陣列的索引。 例如，*識別碼*[*index1*， *index2*] 而不是*識別碼*[*index1*] [ *index2*]。

受管理的所有陣列都繼承自`System::Array`。 任何方法或屬性`System::Array`可以直接套用到陣列變數。

當您配置陣列，其項目類型是指標-managed 類別中，項目為 0 初始化。

當您配置陣列，其項目類型是實值型別`V`，預設建構函式`V`套用至每個陣列元素。 如需詳細資訊，請參閱 < [c + + 原生類型的.NET Framework 對應項 (C + + /cli CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)。

在編譯時期，您可以偵測型別是否具有的 common language runtime (CLR) 陣列`__is_ref_array(type)`。 如需詳細資訊，請參閱 <<c0> [ 類型特性的編譯器支援](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

下列範例會建立一維陣列，具有 100 個元素和一個三維陣列第一個維度中的 3 個元素，5 個元素中，第二個和第三個中的 6 個項目。

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

[適用於.NET 和 UWP 的元件擴充功能](../windows/component-extensions-for-runtime-platforms.md)