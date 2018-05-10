---
title: 類別和結構 （c + + 元件擴充功能） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ref class keyword [C++]
- value class keyword [C++]
- value struct keyword [C++]
- ref struct keyword [C++]
ms.assetid: 5c360764-b229-49c6-9357-66213afbc372
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9863786e5e017b69217f984e3aa6d1db597e74d3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="classes-and-structs--c-component-extensions"></a>類別和結構 (C++ 元件擴充功能)
宣告類別或結構的*物件存留期*會自動管理。 當物件不再可存取或超出範圍時，Visual C++ 會自動捨棄配置給物件的記憶體。  
  
## <a name="all-runtimes"></a>所有執行階段  
 **語法**  
  
```  
  
      class_access  
      ref class  
      name  
      modifier :  inherit_accessbase_type {};  
class_accessref structnamemodifier :  inherit_accessbase_type {};  
class_accessvalue classnamemodifier :  inherit_accessbase_type {};  
class_accessvalue structnamemodifier :  inherit_accessbase_type {};  
  
```  
  
 **參數**  
  
 *class_access* （選擇性）  
 組件外部的類別或結構的存取範圍。 可能的值為**公用**和`private`(`private`是預設值)。 巢狀的類別或結構不能有*class_access*規範。  
  
 *name*  
 類別或結構的名稱。  
  
 *修飾詞*（選擇性）  
 [抽象](../windows/abstract-cpp-component-extensions.md)和[密封](../windows/sealed-cpp-component-extensions.md)為有效的修飾詞。  
  
 *inherit_access* （選擇性）  
 `base_type` 的存取範圍。 唯一允許的存取範圍是 `public` (`public` 是預設值)。  
  
 *base_type* （選擇性）  
 基底類型。 不過，值類型無法做為基底類型。  
  
 如需詳細資訊，請參閱 < 在 Windows 執行階段和通用語言 Runtimesections 此參數的特定語言描述。  
  
 **備註**  
  
 使用物件的預設成員存取範圍宣告**ref 類別**或**實值類別**是`private`。 以宣告物件的預設成員存取範圍和**ref 結構**或**實值結構**是`public`。  
  
 當參考類型繼承自另一種參考類型時，基底類別中的虛擬函式必須明確覆寫 (與[覆寫](../windows/override-cpp-component-extensions.md)) 或隱藏 (與[新 (新 vtable 中的位置）](../windows/new-new-slot-in-vtable-cpp-component-extensions.md))。 必須將衍生的類別函式明確標示為 `virtual`。  
  
 若要在編譯時期偵測類型為`ref class`或`ref struct`，或`value class`或`value struct`，使用`__is_ref_class (type)`， `__is_value_class (type)`，或`__is_simple_value_class (type)`。 如需詳細資訊，請參閱[類型特性的編譯器支援](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。  
  
 如需類別和結構的詳細資訊，請參閱  
  
-   [具現化類別和結構](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)  
  
 
  
-   [參考型別的 C++ 堆疊語意](../dotnet/cpp-stack-semantics-for-reference-types.md)  
  
-   [類別、 結構和等位](../cpp/classes-and-structs-cpp.md)  
  
-   [解構函式與完成項中如何： 定義和使用類別和結構 (C + + /CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)  
  
-   [使用者定義的運算子 (C++/CLI)](../dotnet/user-defined-operators-cpp-cli.md)  
  
-   [使用者定義轉換 (C++/CLI)](../dotnet/user-defined-conversions-cpp-cli.md)  
  
-   [如何：包裝原生類別以便讓 C# 使用](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)  
  
-   [泛型類別 (C++/CLI)](../windows/generic-classes-cpp-cli.md)  
  
## <a name="windows-runtime"></a>Windows 執行階段  
 **備註**  
  
 請參閱[Ref 類別與結構](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx)和[實值類別與結構](http://msdn.microsoft.com/library/windows/apps/hh699861.aspx)。  
  
 **參數**  
  
 *base_type* （選擇性）  
 基底類型。 `ref class` 或 `ref struct` 可以繼承自零或多個介面，以及零或一種 `ref` 類型。 `value class` 或 `value struct` 只可以從零或多個介面繼承。  
  
 當您使用 `ref class` 或 `ref struct` 關鍵字宣告物件時，控制代碼可針對物件存取物件；也就是物件的參考計數器指標。 當宣告的變數超出範圍時，編譯器會自動刪除基礎物件。 當物件做為呼叫中的參數使用，或是儲存在變數中時，實際上是傳遞或儲存該物件的控制代碼。  
  
 當您使用 `value class` 或 `value struct` 關鍵字宣告物件時，不會監督宣告之物件的物件存留期。 此物件類似任何其他標準 C++ 類別或結構。  
  
### <a name="requirements"></a>需求  
 編譯器選項： **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
 **備註**  
  
 下表列出所示的語法差異**所有執行階段**區段特有的 C + + /CLI。  
  
 **參數**  
  
 *base_type* （選擇性）  
 基底類型。 `ref class` 或 `ref struct` 可以繼承自零或多個 Managed 介面及零或一種 ref 類型。 `value class` 或 `value struct` 只可以從零或多個 Managed 介面繼承。  
  
 `ref class` 和 `ref struct` 關鍵字會告訴編譯器：類別或結構是在堆積上配置。 當物件做為呼叫中的參數使用，或是儲存在變數中時，實際上是傳遞或儲存該物件的參考。  
  
 `value class`和`value struct`關鍵字會告訴編譯器所配置的類別或結構的值會傳遞至函式，或儲存在成員。  
  
### <a name="requirements"></a>需求  
 編譯器選項： **/clr**  
  
## <a name="see-also"></a>另請參閱  
 [執行階段平台的元件延伸模組](../windows/component-extensions-for-runtime-platforms.md)