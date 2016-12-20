---
title: "轉換運算子的變更 | Microsoft Docs"
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
  - "轉換運算子"
  - "轉換, explicit"
  - "explicit 關鍵字 [C++]"
  - "運算子 [C++], 明確類型轉換"
  - "類型轉換, 明確轉換"
ms.assetid: 9b83925c-71b7-4bd3-ac2e-843dd7c7f184
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 轉換運算子的變更
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從 Managed Extensions for C\+\+ 升級為 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 之後，轉換運算子的語法已變更。  
  
 一個範例是撰寫 `op_Implicit` 來指定轉換。  下列是取自語言規格之 `MyDouble` 的定義：  
  
```  
__gc struct MyDouble {  
   static MyDouble* op_Implicit( int i );   
   static int op_Explicit( MyDouble* val );  
   static String* op_Explicit( MyDouble* val );   
};  
```  
  
 這是指，如果指定一個整數，則將該整數轉換為 `MyDouble` 的演算法是由 `op_Implicit` 運算子提供。  此外，該轉換必須由編譯器 \(Compiler\) 隱含地執行。  同樣地，若指定 `MyDouble` 物件，則兩個 `op_Explicit` 運算子會提供個別的運算法，以便將該物件轉換為整數或 Managed `String` 實體 \(Entity\)。  不過，只有在使用者明確要求時，編譯器才會執行這項轉換。  
  
 在 C\# 中，程式碼看起來如下：  
  
```  
class MyDouble {  
   public static implicit operator MyDouble( int i );   
   public static explicit operator int( MyDouble val );  
   public static explicit operator string( MyDouble val );   
};  
```  
  
 C\# 程式碼看起比 Managed Extensions for C\+\+ 更像 C\+\+，  但採用新語法之後就不是這樣了。  
  
 ISO\-C\+\+ 委員會引入 `explicit` 關鍵字，來減輕誤用的後果，例如 `Array` 類別會接收單一整數引數做為維度，此類別會隱含將任何整數轉換成 `Array` 物件，而這並不是您要的。  這裡的一個防止方法就是依設計慣例，為建構函式引進空的第二個引數。  
  
 另一方面，您在 C\+\+ 中設計類別型別時不應該提供轉換組。  最好的範例就是標準字串類別。  隱含轉換就是使用 C\-Style 字串的單一引數建構函式。  然而，它不會提供對應的隱含轉換運算子 \(將字串物件轉換為 C\-Style 字串的運算子\)，但是會要求使用者必須明確地叫用 \(Invoke\) 具名函式，在此情況下為 `c_str()`。  
  
 所以，建立轉換運算子上隱含\/明確行為的關聯性 \(而且隨著將一組轉換封裝成單一的宣告形式\) 似乎改善了原本 C\+\+ 的轉換運算子支援，最終不免產生 `explicit` 關鍵字。  [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 語言對轉換運算子的支援如下所示，它比 C\# 的轉換運算子更為簡潔，因為運算子的預設行為支援轉換演算法的隱含使用：  
  
```  
ref struct MyDouble {  
public:  
   static operator MyDouble^ ( int i );  
   static explicit operator int ( MyDouble^ val );  
   static explicit operator String^ ( MyDouble^ val );  
};  
```  
  
 另一項變更是，單一引數建構函式被視為宣告為 `explicit` 處理。  這表示必須經過明確轉換，才會觸發 \(Trigger\) 引動過程。  不過，請注意，如果定義明確轉換運算子，則會叫用明確轉換運算子，而不會叫用單一引數建構函式。  
  
## 請參閱  
 [在類別或介面中的成員宣告 \(C\+\+\/CLI\)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)