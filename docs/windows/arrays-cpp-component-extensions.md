---
title: "Arrays (C++ Component Extensions) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "cli::array"
  - "details::array"
  - "lang::array"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "array keyword [C++]"
  - "declaring arrays, about declaring arrays"
  - "arrays [C++], multidimensional"
  - "multidimensional arrays"
  - "arrays [C++]"
ms.assetid: 49445812-d775-4db1-a231-869598dbb955
caps.latest.revision: 34
caps.handback.revision: 34
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Arrays (C++ Component Extensions)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`Platform::Array<T>` 輸入 [!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)]或 `array` 關鍵字在 [!INCLUDE[cppcli](../build/reference/includes/cppcli_md.md)]中，宣告指定的型別和初始值。  
  
## 所有平台  
 必須在宣告中使用物件的控制代碼 \(^\) 修飾詞在右邊的角括弧 \(\>\) 之後宣告陣列。  
  
 陣列中的元素數目不屬於型別的部分。  一個陣列變數可參考不同的大小。  
  
 不同於標準 C\+\+，註標不可運算指標的同義字並不能顛倒。  
  
 如需陣列的詳細資訊，請參閱：  
  
-   [陣列共變數](../misc/array-covariance.md)  
  
-   [如何：在 C\+\+\/CLI 中使用陣列](../dotnet/how-to-use-arrays-in-cpp-cli.md)  
  
-   [如何：建立多維陣列](../misc/how-to-create-multidimension-arrays.md)  
  
-   [如何：建立 Managed 陣列的陣列 \(不規則陣列\)](../misc/how-to-create-arrays-of-managed-arrays-jagged-arrays.md)  
  
-   [如何：為 Managed 陣列建立 Typedef](../misc/how-to-make-typedefs-for-managed-arrays.md)  
  
-   [如何：將 Managed 陣列當做樣板型別參數使用](../misc/how-to-use-managed-arrays-as-template-type-parameters.md)  
  
-   [Variable Argument Lists \(...\) \(C\+\+\/CLI\)](../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)  
  
-   [如何：排序陣列](../misc/how-to-sort-arrays.md)  
  
-   [如何：使用自訂準則排序陣列](../misc/how-to-sort-arrays-using-custom-criteria.md)  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 陣列為 `Platform` 命名空間的成員。  陣列只能是一維的。  
  
 **語法**  
  
 語法中的第一個範例會使用 `ref new` 彙總關鍵字配置陣列。  第二個範例會宣告一個區域陣列。  
  
```  
  
        [qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier = ref new [Platform::]Array< initialization-type > [{initialization-list [,...]}]  
  
[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier = {initialization-list [,...]}  
  
```  
  
 *qualifiers*［選擇項］  
 一或多個儲存類別規範：[mutable](../cpp/mutable-data-members-cpp.md)、[volatile](../cpp/volatile-cpp.md)， [const](../cpp/const-cpp.md)， [extern](../cpp/using-extern-to-specify-linkage.md)， [static](../misc/static-cpp.md)。  
  
 `array-type`  
 變數的元素型別。  有效型別是 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 類別和基本型別、ref 類別及結構、實值類別及結構、和原生指標 \(`type``*`\)。  
  
 `rank`［選擇項］  
 陣列維度的數目。  必須為 1。  
  
 `identifier`  
 陣列變數的名稱。  
  
 `initialization-type`  
 初始化陣列值的型別。  通常， `array-type` 和 `initialization-type` 都是相同型別。  不過，如果 `initialization-type` 轉換到 `array-type` ，型別可以是不同的，例如，如果 `initialization-type` 衍生自 `array-type`。  
  
 `initialization-list`［選擇項］  
 括號內值初始化陣列的項目的逗號分隔清單。  例如，如果 `rank-size-list` 是 `(3)`，宣告一維陣列 3 個元素， `initialization list` 可以是 `{1,2,3}`。  
  
 **備註**  
  
 您可以在編譯時期偵測型別是否為參考 ─ 具有`__is_ref_array(``type``)`的計數陣列。  如需詳細資訊，請參閱[Compiler Support for Type Traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。  
  
### 需求  
 編譯器選項：**\/ZW**  
  
### 範例  
 下列範例會建立具有 100 個元素的一維陣列。  
  
```  
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
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **語法**  
  
 語法中的第一個範例會使用 `gcnew` 關鍵字配置陣列。  第二個範例會宣告一個區域陣列。  
  
```  
  
        [qualifiers] [cli::]array<[qualifiers] array-type [,rank] >^ identifier = gcnew [cli::]array< initialization-type [,rank] >(rank-size-list[,...]) [{initialization-list [,...]}]  
  
[qualifiers] [cli::]array<[qualifiers] array-type [,rank] >^ identifier = {initialization-list [,...]}  
  
```  
  
 *qualifiers*［選擇項］  
 一或多個儲存類別規範：[mutable](../cpp/mutable-data-members-cpp.md)、[volatile](../cpp/volatile-cpp.md)， [const](../cpp/const-cpp.md)， [extern](../cpp/using-extern-to-specify-linkage.md)， [static](../misc/static-cpp.md)。  
  
 `array-type`  
 變數的元素型別。  有效型別是 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 類別和基本型別、ref 類別、結構、實值類別和結構、原生指標 \(`type``*`\) 和原生的 POD \(一般舊資料\) 型別。  
  
 `rank`［選擇項］  
 陣列維度的數目。  預設值為 1；最大值為 32。  陣列每個維度本身就是陣列。  
  
 `identifier`  
 陣列變數的名稱。  
  
 `initialization-type`  
 初始化陣列值的型別。  通常， `array-type` 和 `initialization-type` 都是相同型別。  不過，如果 `initialization-type` 轉換到 `array-type` ，型別可以是不同的，例如，如果 `initialization-type` 衍生自 `array-type`。  
  
 `rank-size-list`  
 每個陣列維度大小的逗號分隔清單陣列中。  或者，如果 `initialization-list` 參數被指定，編譯器可以推算每個維度的大小，而 `rank-size-list` 可以省略。  如需詳細資訊，請參閱[如何：建立多維陣列](../misc/how-to-create-multidimension-arrays.md)。  
  
 `initialization-list`［選擇項］  
 括號內值初始化陣列的項目的逗號分隔清單。  或在一個多維陣列初始化元素的巢狀 *initialization\-list* 項目的逗號分隔清單。  
  
 例如，如果 `rank-size-list` 是 `(3)`，宣告一維陣列 3 個元素， `initialization list` 可以是 `{1,2,3}`。  如果 `rank-size-list` 是 `(3,2,4)`，宣告第一個維度的 3 個元素的三維陣列，兩個元素在第 2 個， 4 個元素在第三個， `initialization-list` 可以是 `{{1,2,3},{0,0},{-5,10,-21,99}}`\)。  
  
 **備註**  
  
 `array`在[Platform, default, and cli Namespaces](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md) 命名空間中。  
  
 如同 Standard C\+\+，陣列的索引是以零起始，因此，陣列 subscripted 使用方括弧 \(\[\]\)。  不同於標準 C\+\+，一個多維陣列的索引在索引清單指定為每個維度而不是使用一組正方形方括弧 \(\[\]\) 運算子為每個維度。  例如，*identifier*\[*index1*, *index2*\] 而不是 *identifier*\[*index1*\]\[ *index2*\]。  
  
 所有 Managed 陣列繼承自 `System::Array`。  `System::Array` 的任何方法或屬性可以直接套用到陣列變數。  
  
 當您將項目型別是指向 Managed 類別的陣列時，元素初始化為 0 。  
  
 當您分配項目型別是實值型別 `V`的陣列時， `V` 的預設建構函式套用至每個陣列元素。  如需詳細資訊，請參閱[C\+\+ 原生類型的 .NET Framework 對應項](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)。  
  
 在編譯時期，您可以偵測型別是否為具有 `__is_ref_array(``type``)` 的 Common Language Runtime \(CLR\) 陣列。  如需詳細資訊，請參閱[Compiler Support for Type Traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。  
  
### 需求  
 編譯器選項：**\/clr**  
  
### 範例  
 下列範例會建立具有 100 個元素的一維陣列和一個三維陣列，該陣列有 3 個元素在第一維度、5 個元素的第二維度和 6 個元素在第三維度。  
  
```  
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
  
## 請參閱  
 [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)