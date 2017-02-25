---
title: "實值類型的隱含 Boxing | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__box 關鍵字"
  - "Boxing"
  - "Boxing, __box 關鍵字"
  - "Boxing, Visual C++"
  - "實值類型, Boxed"
ms.assetid: 9597c92f-a3fe-44af-ad80-f9d656847a35
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 實值類型的隱含 Boxing
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從 Managed Extensions for C\+\+ 升級為 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 之後，實值型別 \(Value Type\) 的 Boxing 已變更。  
  
 如果以語言設計而言，我們是用一種理性的觀點代替了有關功能的實務經驗，但事實上，這是錯誤的。  依此類推，在原始的多重繼承 \(Inheritance\) 語言設計中，Stroustrup 決定了虛擬基底類別 \(Virtual Base Class\) 的子物件不能在衍生類別 \(Derived Class\) 建構函式 \(Constructor\) 中初始化，因此語言要求任何做為虛擬基底類別的類別都必須定義預設的建構函式。  所有後續的虛擬衍生都會叫用 \(Invoke\) 預設建構函式。  
  
 虛擬基底類別階層架構的問題在於，共用虛擬子物件之初始設定的責任會隨每個後續衍生而轉移。  例如，如果定義基底類別，而基底類別的初始設定需要緩衝區配置，則該緩衝區的使用者指定大小可能會當做引數傳遞到建構函式。  如果後來提供兩個後續的虛擬衍生 \(稱為 `inputb` 和 `outputb`\)，則每個衍生都會提供特定的值給基底類別建構函式。  現在，從 `inputb` 和 `outputb` 衍生了 `in_out` 類別之後，那些共用虛擬基底類別子物件的值都不會明確允許加以評估。  
  
 因此，在原始語言設計中，Stroustrup 不允許在衍生類別建構函式的成員初始設定清單中，明確初始化虛擬基底類別。  儘管這解決了問題，但事實上無法導向虛擬基底類別的初始設定也證實了無法實行。  國家衛生研究院 \(National Institute of Health\) 的 Keith Gorlen 曾經實作過名為 nihcl 的免費軟體版本 SmallTalk 集合程式庫 \(Collection Library\)，他是說服 Stroustrup 必須提出更有彈性之語言設計的主要人物。  
  
 物件導向階層式設計的原則主張，衍生類別應該只會對它的直接基底類別的非私用實作 \(Implementation\) 產生影響。  為了支援虛擬繼承 \(Virtual Inheritance\) 的彈性初始設定設計，Stroustrup 不得不違反這個原則。  階層架構中最高層的衍生類別會為所有虛擬子物件的初始設定負責，不論它出現在多深的階層架構中。  例如，`inputb` 和 `outputb` 都負責明確初始化它們的立即虛擬基底類別。  `in_out` 衍生自 `inputb` 和 `outputb` 之後，`in_out` 便會為曾經移除之虛擬基底類別的初始設定負責，而在 `inputb` 和 `outputb` 中明確執行的初始設定會被隱藏起來。  
  
 這提供語言開發人員所需的彈性，但代價是必須使用複雜的語意 \(Semantics\)。  如果要限制虛擬基底類別不具有狀態，並且只允許指定介面，便可以消除複雜語意帶來的負擔。  這是建議在 C\+\+ 中使用的設計用法。  在 CLR 程式設計中，它會提升為具有介面型別 \(Interface Type\) 的原則。  
  
 以下是簡單的程式碼範例，而且在這裡，明確 Boxing 是不必要的：  
  
```  
// Managed Extensions for C++ requires explicit __box operation  
int my1DIntArray __gc[] = { 1, 2, 3, 4, 5 };  
Object* myObjArray __gc[] = {   
   __box(26), __box(27), __box(28), __box(29), __box(30)  
};  
  
Console::WriteLine( "{0}\t{1}\t{2}", __box(0),  
   __box(my1DIntArray->GetLowerBound(0)),  
   __box(my1DIntArray->GetUpperBound(0)) );  
```  
  
 如您所見，有很多 Boxing 正在進行。  在 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 下，實值型別 Boxing 是隱含的：  
  
```  
// new syntax makes boxing implicit  
array<int>^ my1DIntArray = {1,2,3,4,5};  
array<Object^>^ myObjArray = {26,27,28,29,30};  
  
Console::WriteLine( "{0}\t{1}\t{2}", 0,   
   my1DIntArray->GetLowerBound( 0 ),   
   my1DIntArray->GetUpperBound( 0 ) );  
```  
  
## 請參閱  
 [實值類型和行為 \(C\+\+\/CLI\)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [Boxing](../windows/boxing-cpp-component-extensions.md)