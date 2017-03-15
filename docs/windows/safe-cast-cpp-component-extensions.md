---
title: "safe_cast (C++ Component Extensions) | Microsoft Docs"
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
  - "safe_cast"
  - "safe_cast_cpp"
  - "stdcli::language::safe_cast"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "safe_cast keyword [C++]"
ms.assetid: 4fa688bf-a8ec-49bc-a4c5-f48134efa4f7
caps.latest.revision: 26
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# safe_cast (C++ Component Extensions)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果成功，`safe_cast` 作業會傳回指定的運算式做為指定的類型，否則會擲回 `InvalidCastException`。  
  
## 所有執行階段  
 \(這個語言功能沒有適用所有執行階段的備註。\)  
  
### 語法  
  
```cpp  
  
[default]:: safe_cast<  
type-id  
>(  
expression  
)  
  
```  
  
### 參數  
  
### 備註  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 `safe_cast` 可讓您變更指定運算式的類型。  在您完全預期變數或參數可轉換成特定類型的情況下，您可以使用 safe\_cast 而不需使用 try\-catch 區塊，即可在開發期間偵測程式設計錯誤。  如需詳細資訊，請參閱[轉型 \(C\+\+\/CX\)](http://msdn.microsoft.com/library/windows/apps/hh755802.aspx)。  
  
### 語法  
  
```cpp  
  
[default]:: safe_cast<  
type-id  
>(  
expression  
)  
  
```  
  
### 參數  
 *type\-id*  
 *運算式*要轉換到的類型。  一個控制代碼，可用來參考或值類型、值類型，或參考或值類型的追蹤參考。  
  
 *運算式*  
 一個運算式，可針對用來參考或值類型、值類型，或參考或值類型的追蹤參考之控制代碼進行評估。  
  
### 備註  
 如果無法將*運算式*轉換成 *type\-id* 指定的類型，`safe_cast` 就會擲回 `InvalidCastException`。  若要捕捉 `InvalidCastException`，請指定 [\/EH \(例外狀況處理模型\)](../build/reference/eh-exception-handling-model.md) 編譯器選項，並使用 try\/catch 陳述式。  
  
### 需求  
 編譯器選項：**\/ZW**  
  
### 範例  
 **範例**  
  
 下列程式碼範例示範如何搭配使用 `safe_cast` 與 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]。  
  
```cpp#  
// safe_cast_ZW.cpp  
// compile with: /ZW /EHsc  
  
using namespace default;  
using namespace Platform;  
  
interface class I1 {};  
interface class I2 {};  
interface class I3 {};  
  
ref class X : public I1, public I2 {};  
  
int main(Array<String^>^ args) {  
   I1^ i1 = ref new X;  
   I2^ i2 = safe_cast<I2^>(i1);   // OK, I1 and I2 have common type: X  
   // I2^ i3 = static_cast<I2^>(i1);   C2440 use safe_cast instead  
   try {  
      I3^ i4 = safe_cast<I3^>(i1);   // Fails because i1 is not derived from I3.  
   }   
   catch(InvalidCastException^ ic) {  
     wprintf(L"Caught expected exception: %s\n", ic->Message);  
   }  
}  
```  
  
 **輸出**  
  
  **攔截到預期的例外狀況：InvalidCastException**   
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 `safe_cast` 可讓您變更運算式的類型，並產生可驗證的 MSIL 程式碼。  
  
### 語法  
  
```cpp  
  
[cli]:: safe_cast<  
type-id  
>(  
expression  
)  
  
```  
  
### 參數  
 *type\-id*  
 一個控制代碼，可用來參考或值類型、值類型，或參考或值類型的追蹤參考。  
  
 *運算式*  
 一個運算式，可針對用來參考或值類型、值類型，或參考或值類型的追蹤參考之控制代碼進行評估。  
  
### 備註  
 運算式 `safe_cast<`*type\-id*`>(`*expression*`)` 會將運算元運算式轉換成 type\-id 類型的物件。  
  
 在將接受 `safe_cast` 的大部分位置中，編譯器會接受其中的 [static\_cast](../cpp/static-cast-operator.md)。  不過，`safe_cast` 保證能夠產生可驗證的 MSIL，其中的 `static_cast` 可能會產生無法驗證的 MSIL。  如需可驗證程式碼的詳細資訊，請參閱[純粹的和可驗證的程式碼](../dotnet/pure-and-verifiable-code-cpp-cli.md)和 [Peverify.exe \(PEVerify Tool\)](../Topic/Peverify.exe%20\(PEVerify%20Tool\).md)。  
  
 如同 `static_cast`，`safe_cast` 會叫用使用者定義的轉換。  
  
 如需轉型的詳細資訊，請參閱[轉型運算子](../cpp/casting-operators.md)。  
  
 `safe_cast` 不會套用 **const\_cast** \(沒有 **const**\)。  
  
 `safe_cast` 位於 cli 命名空間。  如需詳細資訊，請參閱 [Platform, default, and cli Namespaces](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md)。  
  
 如需 **safe\_cas**t 的詳細資訊，請參閱：  
  
-   [C\-Style Casts with \/clr \(C\+\+\/CLI\)](../windows/c-style-casts-with-clr-cpp-cli.md)  
  
-   [如何：在 C\+\+\/CLI 中使用 safe\_cast](../dotnet/how-to-use-safe-cast-in-cpp-cli.md)  
  
-   [如何：使用 safe\_cast 向下轉型](../misc/how-to-downcast-with-safe-cast.md)  
  
-   [如何：使用 safe\_cast 和泛型類型](../misc/how-to-use-safe-cast-and-generic-types.md)  
  
-   [如何：使用 safe\_cast 和使用者定義的轉換](../misc/how-to-use-safe-cast-and-user-defined-conversions.md)  
  
-   [如何：使用 safe\_cast 和 Boxing](../misc/how-to-use-safe-cast-and-boxing.md)  
  
-   [如何：使用 safe\_cast 和 Unboxing](../misc/how-to-use-safe-cast-and-unboxing.md)  
  
### 需求  
 編譯器選項：**\/clr**  
  
### 範例  
 **範例**  
  
 一個適用於不相關的介面類型之間轉型的範例，其中編譯器不會接受 `static_cast` 但接受 `safe_cast`。  使用 `safe_cast` 時，編譯器不會發出轉換錯誤，並會在執行階段上執行檢查以查看是否能轉型  
  
```cpp  
// safe_cast.cpp  
// compile with: /clr  
using namespace System;  
  
interface class I1 {};  
interface class I2 {};  
interface class I3 {};  
  
ref class X : public I1, public I2 {};  
  
int main() {  
   I1^ i1 = gcnew X;  
   I2^ i2 = safe_cast<I2^>(i1);   // OK, I1 and I2 have common type: X  
   // I2^ i3 = static_cast<I2^>(i1);   C2440 use safe_cast instead  
   try {  
      I3^ i4 = safe_cast<I3^>(i1);   // fail at runtime, no common type  
   }   
   catch(InvalidCastException^) {  
      Console::WriteLine("Caught expected exception");  
   }  
}  
```  
  
 **輸出**  
  
  **捕捉到預期的例外狀況**   
## 請參閱  
 [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)