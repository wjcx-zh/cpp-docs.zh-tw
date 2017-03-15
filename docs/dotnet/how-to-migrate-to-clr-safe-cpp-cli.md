---
title: "如何：移轉至 /clr:safe (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/clr 編譯器選項 [C++], 移轉至 /clr:safe"
  - "移轉 [C++], 可驗證的組件"
  - "升級 Visual C++ 應用程式, 可驗證的組件"
  - "可驗證的組件 [C++], 移轉至"
ms.assetid: 75f9aae9-1dcc-448a-aa11-2d96f972f9d2
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：移轉至 /clr:safe (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 可使用 **\/clr:safe** 產生可驗證的元件，這會使編譯器對每一個不可驗證的程式碼建構都產生錯誤。  
  
## 備註  
 下列問題會產生可驗證性的錯誤：  
  
-   原生 \(Native\) 型別。  就算不使用，原生類別 \(Class\)、結構、指標或陣列的宣告也會妨礙編譯。  
  
-   全域變數  
  
-   任何會進入 Unmanaged 程式庫的函式呼叫，包括 Common Language Runtime 的函式呼叫。  
  
-   可驗證的函式不能包含用於向下轉型 \(Down Casting\) 的 [static\_cast 運算子](../cpp/static-cast-operator.md)。  [static\_cast 運算子](../cpp/static-cast-operator.md) 可以用來在基本型別 \(Primitive Type\) 之間轉型，但是向下轉型則必須使用 [safe\_cast](../windows/safe-cast-cpp-component-extensions.md) 或 C\-Style 轉型 \(實作為 [safe\_cast](../windows/safe-cast-cpp-component-extensions.md)\)。  
  
-   可驗證的函式不能包含 [reinterpret\_cast 運算子](../cpp/reinterpret-cast-operator.md) \(或任何 C\-style 轉型的對等用法\)。  
  
-   可驗證的函式不能在 [interior\_ptr \(C\+\+\/CLI\)](../windows/interior-ptr-cpp-cli.md) 上進行演算。  它可能僅指派並取消參考。  
  
-   可驗證的函式只能擲回或攔截參考型別 \(Reference Type\) 的指標，所以實值型別 \(Value Type\) 在擲回之前必須先進行 Box 處理。  
  
-   可驗證的函式只能呼叫可驗證的函式 \(這樣就不允許呼叫 Common Language Runtime，其中包括 `AtEntry``AtExit`，因此不允許全域建構函式\)。  
  
-   可驗證的類別不能使用 <xref:System.Runtime.InteropServices.LayoutKind>。  
  
-   如果是建置 EXE，則 main 函式不能宣告任何參數，所以必須使用 <xref:System.Environment.GetCommandLineArgs%2A> 來擷取命令列引數。  
  
-   對虛擬函式 \(Virtual Function\) 進行非虛擬呼叫。  例如：  
  
    ```  
    // not_verifiable.cpp  
    // compile with: /clr  
    ref struct A {  
       virtual void Test() {}  
    };  
  
    ref struct B : A {};  
  
    int main() {  
       B^ b1 = gcnew B;  
       b1->A::Test();   // Non-virtual call to virtual function  
    }  
    ```  
  
 此外，請勿在可驗證程式碼中使用下列關鍵字：  
  
-   [unmanaged](../preprocessor/managed-unmanaged.md) 和 [pack](../preprocessor/pack.md) Pragma  
  
-   [naked](../cpp/naked-cpp.md) 和 [align](../cpp/align-cpp.md) [\_\_declspec](../cpp/declspec.md) 修飾詞 \(Modifier\)  
  
-   [\_\_asm](../assembler/inline/asm.md)  
  
-   [\_\_based](../cpp/based-grammar.md)  
  
-   [\_\_try](../cpp/try-except-statement.md) 和 `__except`  
  
## 請參閱  
 [純粹的和可驗證的程式碼](../dotnet/pure-and-verifiable-code-cpp-cli.md)