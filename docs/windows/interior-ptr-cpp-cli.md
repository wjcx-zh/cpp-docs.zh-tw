---
title: "interior_ptr (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "stdcli::language::interior_ptr"
  - "interior_ptr_cpp"
  - "interior_ptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "interior_ptr keyword [C++]"
ms.assetid: 25160f74-569e-492d-9e3c-67ece7486baa
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# interior_ptr (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

*內部指標* 對所參考型別內宣告指標，而不是對物件本身。  內部指標可以指向參考控制項、實值型別、 Boxed 型別控制項、Managed 型別的成員、或指向 Managed 陣列的元素。  
  
## 所有執行階段  
 \(這個語言功能沒有適用於所有執行階段的備註\)。  
  
## Windows Runtime \- Windows 執行階段  
 \(這個語言功能沒有只適用於 Windows 執行階段的備註。\)  
  
### 需求  
 編譯器選項：**\/ZW**  
  
## Common Language Runtime  
 下列語法範例示範內部指標。  
  
### 語法  
  
```cpp  
cli::interior_ptr<cv_qualifier type> var = &initializer;  
```  
  
### 參數  
 *cv\_qualifier*  
 **const** 或 `volatile` 限定詞。  
  
 *type*  
 *initializer* 的型別。  
  
 *var*  
 `interior_ptr`變數的名稱。  
  
 *initializer*  
 參考型別，項目的 Managed 陣列，或任何其他的成員可以指派到原生指標的物件。  
  
### 備註  
 原生指標不可以追蹤項目，因為它的位置在 Managed 堆積上變更，由物件的記憶體回收行程移動的執行個體。  為了正確參考的指標可以執行個體，執行階段必須更新指標到新位置的物件。  
  
 `interior_ptr` 表示原生指標功能的超集。因此，可以指派至原生指標的任何物件也可以指派至 `interior_ptr`。內部指標被允許執行同一組作業與原生指標，包括比較和指標算術。  
  
 內部指標只能在堆疊宣告。內部指標不可以宣告為類別的成員。  
  
 因為內部指標只存在於堆疊，採用內部指標的位址會產生 Unmanaged 指標。  
  
 `interior_ptr` 具有 `bool`的隱含轉換，允許其在條件陳述式的用法。  
  
 如需如何宣告點到物件在記憶體回收堆積無法移動的內部指標的詳細資訊，請參閱 [pin\_ptr](../windows/pin-ptr-cpp-cli.md)。  
  
 `interior_ptr` 是在 cli 命名空間中。如需詳細資訊，請參閱[Platform, default, and cli Namespaces](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md)。  
  
 如需內部指標的詳細資訊，請參閱  
  
-   [How to: Declare and Use Interior Pointers and Managed Arrays \(C\+\+\/CLI\)](../windows/how-to-declare-and-use-interior-pointers-and-managed-arrays-cpp-cli.md)  
  
-   [How to: Declare Value Types with the interior\_ptr Keyword \(C\+\+\/CLI\)](../windows/how-to-declare-value-types-with-the-interior-ptr-keyword-cpp-cli.md)  
  
-   [How to: Overload Functions with Interior Pointers and Native Pointers \(C\+\+\/CLI\)](../windows/how-to-overload-functions-with-interior-pointers-and-native-pointers-cpp-cli.md)  
  
-   [How to: Declare Interior Pointers with the const Keyword \(C\+\+\/CLI\)](../windows/how-to-declare-interior-pointers-with-the-const-keyword-cpp-cli.md)  
  
### 需求  
 編譯器選項：**\/clr**  
  
### 範例  
 **範例**  
  
 下列範例顯示如何宣告和使用內部指標的參考型別。  
  
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
  
 **Output**  
  
 **1**   
**2**   
**3**   
## 請參閱  
 [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)