---
title: "如何：在 /clr 編譯中使用原生類型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/clr 編譯器選項 [C++], 使用原生類型"
  - "編譯, /clr 中的原生類型"
ms.assetid: 3a505c90-4adb-4942-9cf9-7d1fdcbc01e7
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：在 /clr 編譯中使用原生類型
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以在 **\/clr** 編譯中定義原生型別，而且在組件內任意使用該原生型別都是有效的。  但是，無法從參考的中繼資料 \(Metadata\) 使用原生型別。  
  
 每個組件都必須包含將使用之每個原生型別的定義。  
  
 如需詳細資訊，請參閱[\/clr \(Common Language Runtime 編譯\)](../build/reference/clr-common-language-runtime-compilation.md)。  
  
## 範例  
 本範例會建立定義及使用原生型別的元件。  
  
```  
// use_native_type_in_clr.cpp  
// compile with: /clr /LD  
public struct NativeClass {  
   static int Test() { return 98; }  
};  
  
public ref struct ManagedClass {  
   static int i = NativeClass::Test();  
   void Test() {  
      System::Console::WriteLine(i);  
   }  
};  
```  
  
## 範例  
 本範例會定義使用元件的用戶端。  請注意，除非已在編譯單位 \(Compiland\) 中定義原生型別，否則存取該原生型別時會發生錯誤。  
  
```  
// use_native_type_in_clr_2.cpp  
// compile with: /clr  
#using "use_native_type_in_clr.dll"  
// Uncomment the following 3 lines to resolve.  
// public struct NativeClass {  
//    static int Test() { return 98; }  
// };  
  
int main() {  
   ManagedClass x;  
   x.Test();  
  
   System::Console::WriteLine(NativeClass::Test());   // C2653  
}  
```  
  
## 請參閱  
 [使用 C\+\+ Interop \(隱含 PInvoke\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)