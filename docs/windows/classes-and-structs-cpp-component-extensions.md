---
title: "Classes and Structs  (C++ Component Extensions) | Microsoft Docs"
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
  - "public"
  - "ref struct"
  - "value_CPP"
  - "ref class"
  - "value struct"
  - "ref struct_cpp"
  - "ref class_cpp"
  - "value class_cpp"
  - "value struct_cpp"
  - "value class"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ref class keyword [C++]"
  - "value class keyword [C++]"
  - "value struct keyword [C++]"
  - "ref struct keyword [C++]"
ms.assetid: 5c360764-b229-49c6-9357-66213afbc372
caps.latest.revision: 32
caps.handback.revision: 32
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Classes and Structs  (C++ Component Extensions)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

宣告其*物件存留期*會自動管理的類別或結構。  當物件不再可存取或超出範圍時，Visual C\+\+ 會自動捨棄配置給物件的記憶體。  
  
## 所有執行階段  
 **語法**  
  
```  
  
          class_access ref class    name modifier :  inherit_access base_type {};  
class_access ref struct   name modifier :  inherit_access base_type {};  
class_access value class  name modifier :  inherit_access base_type {};  
class_access value struct name modifier :  inherit_access base_type {};  
  
```  
  
 **參數**  
  
 *class\_access* \(選擇性\)  
 組件外部的類別或結構的存取範圍。  可能的值為 **public** 和 `private` \(`private` 是預設值\)。  巢狀類別或結構不可以有 *class\_access* 規範。  
  
 *name*  
 類別或結構的名稱。  
  
 *modifier* \(選擇性\)  
 [abstract](../windows/abstract-cpp-component-extensions.md) 和 [sealed](../windows/sealed-cpp-component-extensions.md) 為有效的修飾詞。  
  
 *inherit\_access* \(選擇性\)  
 `base_type` 的存取範圍。  唯一允許的存取範圍是 `public` \(`public` 是預設值\)。  
  
 *base\_type* \(選擇性\)  
 基底類型。  不過，值類型無法做為基底類型。  
  
 如需詳細資訊，請參閱 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 和 [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)] 區段中此參數的特定語言描述。  
  
 **備註**  
  
 使用 **ref 類別**或 **value 類別**宣告之物件的預設成員存取範圍是 `private`。  此外，使用 **ref struct** 或 **value struct** 宣告之物件的預設成員存取範圍是 `public`。  
  
 當參考類型繼承自另一個參考類型時，必須以 [override](../windows/override-cpp-component-extensions.md) 明確覆寫，或以 [new \(new slot in vtable\)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md) 隱藏基底類別中的虛擬函式。  必須將衍生的類別函式明確標示為 `virtual`。  
  
 若要在編譯時期偵測類型為 `ref class`、`ref struct`、`value class` 還是 `value struct`，請使用 `__is_ref_class (``type``)`、`__is_value_class (``type``)` 或  `__is_simple_value_class (``type``)`。  如需詳細資訊，請參閱[Compiler Support for Type Traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。  
  
 如需類別和結構的詳細資訊，請參閱  
  
-   [具現化類別和結構](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)  
  
-   [實值類型和參考類型中 this 指標的語意](../misc/semantics-of-the-this-pointer-in-value-and-reference-types.md)  
  
-   [參考類型的 C\+\+ 堆疊語意](../dotnet/cpp-stack-semantics-for-reference-types.md)  
  
-   [類別、結構和等位](../cpp/classes-and-structs-cpp.md)  
  
-   [原生類別上的公用和私用](../misc/how-to-declare-public-and-private-on-native-classes.md)  
  
-   [隱含抽象類別](../misc/implicitly-abstract-classes.md)  
  
-   [在類別或結構中定義靜態建構函式](../misc/how-to-define-static-constructors-in-a-class-or-struct.md)  
  
-   [無法產生複製建構函式](../misc/copy-constructor-may-not-be-generated.md)  
  
-   [參考類型中的依簽章隱藏型函式](../misc/hide-by-signature-functions-in-reference-types.md)  
  
-   [Visual C\+\+ 中的解構函式和完成項](../misc/destructors-and-finalizers-in-visual-cpp.md)  
  
-   [類型和成員可視性](../misc/type-and-member-visibility.md)  
  
-   [使用者定義的運算子](../dotnet/user-defined-operators-cpp-cli.md)  
  
-   [使用者定義轉換](../dotnet/user-defined-conversions-cpp-cli.md)  
  
-   [如何：包裝原生類別以便讓 C\# 使用](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)  
  
-   [Generic Classes \(C\+\+\/CLI\)](../windows/generic-classes-cpp-cli.md)  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 **備註**  
  
 請參閱 [Ref 類別與結構](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx) 和[實值類別與結構](http://msdn.microsoft.com/library/windows/apps/hh699861.aspx)。  
  
 **參數**  
  
 *base\_type* \(選擇性\)  
 基底類型。  `ref class` 或 `ref struct` 可以繼承自零或多個介面，以及零或一種 `ref` 類型。  `value class` 或 `value struct` 只可以從零或多個介面繼承。  
  
 當您使用 `ref class` 或 `ref struct` 關鍵字宣告物件時，控制代碼可針對物件存取物件；也就是物件的參考計數器指標。  當宣告的變數超出範圍時，編譯器會自動刪除基礎物件。  當物件做為呼叫中的參數使用，或是儲存在變數中時，實際上是傳遞或儲存該物件的控制代碼。  
  
 當您使用 `value class` 或 `value struct` 關鍵字宣告物件時，不會監督宣告之物件的物件存留期。  此物件類似任何其他標準 C\+\+ 類別或結構。  
  
### 需求  
 編譯器選項：**\/ZW**  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **備註**  
  
 下表列出 C\+\+\/CLI 特有的**所有執行階段**區段中顯示的語法差異。  
  
 **參數**  
  
 *base\_type* \(選擇性\)  
 基底類型。  `ref class` 或 `ref struct` 可以繼承自零或多個 Managed 介面及零或一種 ref 類型。  `value class` 或 `value struct` 只可以從零或多個 Managed 介面繼承。  
  
 `ref class` 和 `ref struct` 關鍵字會告訴編譯器：類別或結構是在堆積上配置。  當物件做為呼叫中的參數使用，或是儲存在變數中時，實際上是傳遞或儲存該物件的參考。  
  
 `value class` 和 `value struct` 關鍵字會告訴編譯器，所配置類別或結構的值已傳遞給函式或儲存在成員中。  
  
### 需求  
 編譯器選項：**\/clr**  
  
## 請參閱  
 [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)