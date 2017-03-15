---
title: "delegate (C++ 元件擴充功能) | Microsoft Docs"
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
  - "delegate_cpp"
  - "delegate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "delegate 關鍵字 [C++]"
ms.assetid: 03caf23d-7873-4a23-9b34-becf42aaf429
caps.latest.revision: 26
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# delegate (C++ 元件擴充功能)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

宣告表示函式指標的型別。  
  
## 所有執行階段  
 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 和 Common Language Runtime 兩者都支援委派。  
  
### 備註  
 `delegate` 是內容相關性關鍵字。  如需詳細資訊，請參閱[視內容而有所區別的關鍵字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。  
  
 若要在編譯時期偵測型別是否為委派，請使用 `__is_delegate()` 型別特性。  如需詳細資訊，請參閱[Compiler Support for Type Traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。  
  
## Windows Runtime \- Windows 執行階段  
 C\+\+\/CX 支援下列語法的支援委派。  
  
### 語法  
  
```cpp  
  
access delegate return-type delegate-type-identifier ([ parameters ])  
```  
  
### 參數  
 *access*  
 \(選擇性\) 委派的存取範圍，可以是 `public` \(預設值\) 或 `private`。  函式原型也可以使用 `const` 或 `volatile` 關鍵字來限定。  
  
 *return\-type*  
 函式原型的傳回型別。  
  
 *delegate\-type\-identifier*  
 宣告的委派型別名稱。  
  
 *parameters*  
 \(選擇性\) 函式原型的型別和識別項。  
  
### 備註  
 使用*delegate\-type\-identifier*來宣告具有和委派相同原型的事件。  如需詳細資訊，請參閱[委派 \(C\+\+\/CX\)](../Topic/Delegates%20\(C++-CX\).md)。  
  
### 需求  
 編譯器選項：**\/ZW**  
  
## Common Language Runtime  
 Common Language Runtime 支援具有下列語法的委派。  
  
### 語法  
  
```cpp  
  
access delegate function_declaration  
```  
  
### 參數  
 *access*  
 \(選擇性\) 組件外之委派的存取範圍可以是公用或私用。預設為私用。在類別中，委派可以有任何存取範圍。  
  
 *function\_declaration*  
 可繫結至委派之函式的簽章。  委派的傳回型別可以是任何 Managed 型別。  基於互通性的原因，建議委派的傳回型別使用 CLS 型別。  
  
 若要定義未繫結的委派，*function\_declaration* 中的第一個參數應該是物件 `this` 指標的型別。  如需詳細資訊，請參閱[取消繫結委派](../misc/unbound-delegates.md)。  
  
### 備註  
 委派為多點傳送：「函式指標」可以繫結至 Managed 類別中的一個或多個方法。  **delegate** 關鍵字會定義具有特定方法簽章的多點傳送委派型別。  
  
 委派也可以繫結至實值類別的方法，例如靜態方法。  
  
 委派具有下列特性：  
  
-   它繼承自 **System::MulticastDelegate**。  
  
-   其中的建構函式會接受兩個引數：Managed 類別或 **NULL** \(適用於繫結至靜態方法的情況\) 的指標，以及指定之型別的完整方法。  
  
-   它擁有稱為 `Invoke` 的方法，其簽章與宣告的委派簽章相符。  
  
 叫用委派時，是依照原先附加其函式的順序呼叫函式。  
  
 委派的傳回值是其最後一個附加成員函式的傳回值。  
  
 委派無法被多載。  
  
 委派可以是繫結或未繫結的。  
  
 當您將繫結的委派執行個體化時，第一個引數會是物件參考。委派具現化的第二個引數必須是 Managed 類別物件之方法的位址或實值型別之方法的指標。委派具現化的第二個引數必須以完整類別範圍語法為方法命名，並套用傳址運算子。  
  
 當您將繫結的委派執行個體化時，第一個引數會是 Managed 類別物件之方法的位址，或是實值型別之方法的指標。引數必須以完整類別範圍語法為方法命名，並套用傳址運算子。  
  
 建立靜態或全域函式的委派時，只需要一個參數：函式 \(或者，函式的位址\)。  
  
 如需委派的詳細資訊，請參閱  
  
-   [取消繫結委派](../misc/unbound-delegates.md)  
  
-   [如何：定義和使用委派](../dotnet/how-to-define-and-use-delegates-cpp-cli.md)  
  
-   [實值類別成員的委派](../misc/how-to-associate-delegates-to-members-of-a-value-class.md)  
  
-   [Unmanaged 函式的委派](../misc/how-to-associate-delegates-to-unmanaged-functions.md)  
  
-   [組合委派](../misc/how-to-compose-delegates.md)  
  
-   [如何：將委派^ 傳遞至預期函式指標的原生函式](../misc/how-to-pass-a-delegate-hat-to-a-native-function-expecting-a-function-pointer.md)  
  
-   [Generic Delegates \(Visual C\+\+\)](../windows/generic-delegates-visual-cpp.md)  
  
### 需求  
 編譯器選項：**\/clr**  
  
### 範例  
 **範例**  
  
 下列範例說明如何宣告、初始化和叫用委派。  
  
```cpp  
// mcppv2_delegate.cpp  
// compile with: /clr  
using namespace System;  
  
// declare a delegate  
public delegate void MyDel(int i);  
  
ref class A {  
public:  
   void func1(int i) {  
      Console::WriteLine("in func1 {0}", i);  
   }  
  
   void func2(int i) {  
      Console::WriteLine("in func2 {0}", i);  
   }  
  
   static void func3(int i) {  
      Console::WriteLine("in static func3 {0}", i);  
   }  
};  
  
int main () {  
   A ^ a = gcnew A;  
  
   // declare a delegate instance  
   MyDel^ DelInst;  
  
   // test if delegate is initialized  
   if (DelInst)  
      DelInst(7);  
  
   // assigning to delegate  
   DelInst = gcnew MyDel(a, &A::func1);  
  
   // invoke delegate  
   if (DelInst)  
      DelInst(8);  
  
   // add a function  
   DelInst += gcnew MyDel(a, &A::func2);  
  
   DelInst(9);  
  
   // remove a function  
   DelInst -= gcnew MyDel(a, &A::func1);  
  
   // invoke delegate with Invoke  
   DelInst->Invoke(10);  
  
   // make delegate to static function  
   MyDel ^ StaticDelInst = gcnew MyDel(&A::func3);  
   StaticDelInst(11);  
}  
```  
  
 **Output**  
  
  **在 func1 8 中**  
 **在 func1 9**  
 **在 func2 9 中**  
 **在 func2 10**  
 **在靜態 func3 11 中**   
## 請參閱  
 [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)