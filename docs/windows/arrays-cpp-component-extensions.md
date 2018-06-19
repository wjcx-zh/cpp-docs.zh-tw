---
title: 陣列 （c + + 元件擴充功能） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
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
- declaring arrays, about declaring arrays
- arrays [C++], multidimensional
- multidimensional arrays
- arrays [C++]
ms.assetid: 49445812-d775-4db1-a231-869598dbb955
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a17649402fa6ebe9c98d768badcf36e5700f5b75
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33862718"
---
# <a name="arrays-c-component-extensions"></a>陣列 (C++ 元件擴充功能)
`Platform::Array<T>`類型在 C + + /CX 中，或`array`關鍵字在 C + + CLI，會宣告陣列的指定型別和初始值。  
  
## <a name="all-platforms"></a>所有平台  
 陣列必須在右角括弧 (>) 在宣告後使用到物件控制代碼 (^) 修飾詞宣告。  
 陣列的元素數目不是類型的一部分。 一個陣列變數可以參考以不同大小的陣列。  
  
 不同於標準 c + + 中，註標不是指標算術的同義字，而且不交替。  
  
 如需陣列的詳細資訊，請參閱：  
  
-   [如何：在 C++/CLI 中使用陣列](../dotnet/how-to-use-arrays-in-cpp-cli.md)  
    
-   [變數引數清單 (...) (C++/CLI)](../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)  
  
## <a name="windows-runtime"></a>Windows 執行階段  
 陣列是屬於`Platform`命名空間。 陣列可以是只有一維陣列。  
  
### <a name="syntax"></a>語法  
  
 第一個語法的範例會使用`ref new`彙總關鍵字來配置陣列。 第二個範例會宣告區域陣列。  
  
```  
[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier = 
    ref new[Platform::]Array<initialization-type> [{initialization-list [,...]}]  
  
[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier = 
    {initialization-list [,...]}  
```  
  
 *限定詞*[選用]  
 一或多個這些儲存類別規範：[可變動](../cpp/mutable-data-members-cpp.md)， [volatile](../cpp/volatile-cpp.md)， [const](../cpp/const-cpp.md)， [extern](../cpp/using-extern-to-specify-linkage.md)，[靜態](../cpp/static-members-cpp.md).  
  
 `array-type`  
 陣列變數的型別。 有效的類型為 Windows 執行階段類別和基本類型、 ref 類別和結構、 實值類別、 結構和原生指標 (`type*`)。  
  
 `rank` [選用]  
 陣列維度的數目。 必須是 1。  
  
 `identifier`  
 陣列變數名稱。  
  
 `initialization-type`  
 值，初始化陣列型別。 一般而言，`array-type`和`initialization-type`類型相同。 不過，類型可以不同，如果沒有從轉換`initialization-type`至`array-type`— 例如，如果`initialization-type`衍生自`array-type`。  
  
 `initialization-list` [選用]  
 初始化陣列元素的大括號中值的逗號分隔清單。 例如，如果`rank-size-list`已`(3)`，其中宣告的 3 個元素，一維陣列`initialization list`可能`{1,2,3}`。  
  
### <a name="remarks"></a>備註  
  
 您可以在編譯時期偵測類型是否具有的參考計數陣列`__is_ref_array(type)`。 如需詳細資訊，請參閱[類型特性的編譯器支援](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。  
  
### <a name="requirements"></a>需求  
 編譯器選項： **/ZW**  
  
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
  
 第一個語法的範例會使用`gcnew`關鍵字來配置陣列。 第二個範例會宣告區域陣列。  
  
```  
[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier = 
    gcnew [cli::]array<initialization-type[,rank]>(rank-size-list[,...]) [{initialization-list [,...]}]  
  
[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier = 
    {initialization-list [,...]}  
```  
  
 *限定詞*[選用]  
 一或多個這些儲存類別規範：[可變動](../cpp/mutable-data-members-cpp.md)， [volatile](../cpp/volatile-cpp.md)， [const](../cpp/const-cpp.md)， [extern](../cpp/using-extern-to-specify-linkage.md)，[靜態](../cpp/static-members-cpp.md).  
  
 `array-type`  
 陣列變數的型別。 有效的類型為 Windows 執行階段類別和基本類型、 ref 類別和結構、 實值類別與結構，原生指標 (`type*`)，以及原生的 POD （一般舊資料） 型別。  
  
 `rank` [選用]  
 陣列維度的數目。 預設值為 1。最大值為 32。 陣列的每個維度是本身的陣列。  
  
 `identifier`  
 陣列變數名稱。  
  
 `initialization-type`  
 值，初始化陣列型別。 一般而言，`array-type`和`initialization-type`類型相同。 不過，類型可以不同，如果沒有從轉換`initialization-type`至`array-type`— 例如，如果`initialization-type`衍生自`array-type`。  
  
 `rank-size-list`  
 陣列中每個維度的大小以逗號分隔清單。 或者，如果`initialization-list`參數指定，則編譯器可以減少每個維度大小和`rank-size-list`可以省略。 
  
 `initialization-list` [選用]  
 初始化陣列元素的大括號中值的逗號分隔清單。 或以逗號分隔清單的巢狀*初始設定清單*初始化多維陣列中的元素的項目。  
  
 例如，如果`rank-size-list`已`(3)`，其中宣告的 3 個元素，一維陣列`initialization list`可能`{1,2,3}`。 如果`rank-size-list`已`(3,2,4)`，其中會宣告一個三維陣列的第一個維度、 第二、 2 個元素和第三個，在 4 個元素中的 3 個元素的`initialization-list`可能`{{1,2,3},{0,0},{-5,10,-21,99}}`。)  
  
### <a name="remarks"></a>備註  
  
 `array` 處於[平台、 default 和 cli 命名空間](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md)命名空間。  
  
 類似標準 c + + 中，陣列的索引是以零起始，並加上使用方括號 ([]) 註標的陣列。 不同於標準 c + + 中，針對每個維度，而不是一組方括弧 ([]) 運算子，針對每個維度的索引的清單中指定多維陣列的索引。 例如，*識別碼*[*index1*， *index2*] 而不是*識別碼*[*index1*] [ *index2*]。  
  
 所有的 managed 的陣列繼承自`System::Array`。 任何方法或屬性`System::Array`可以直接套用到陣列變數。  
  
 當您配置陣列，其項目類型是指標的為受管理的類別，項目會是 0 初始化。  
  
 當您配置一個陣列的項目型別是實值類型`V`的預設建構函式`V`套用至每個陣列元素。 如需詳細資訊，請參閱[c + + 原生類型的.NET Framework 對等用法 (C + + /CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)。  
  
 在編譯時期，您可以偵測到的型別是否具有的 common language runtime (CLR) 陣列`__is_ref_array(type)`。 如需詳細資訊，請參閱[類型特性的編譯器支援](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。  
  
### <a name="requirements"></a>需求  
 編譯器選項： **/clr**  
  
### <a name="examples"></a>範例  
 下列範例會建立一維陣列，具有 100 個元素和三維陣列具有 3 個元素的第一個維度中、 5 的項目中，第二個和第三個中的 6 項目。  
  
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
 [執行階段平台的元件延伸模組](../windows/component-extensions-for-runtime-platforms.md)