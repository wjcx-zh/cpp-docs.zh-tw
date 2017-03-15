---
title: "Managed 類型 (C++/CL) | Microsoft Docs"
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
  - "__gc 類型"
  - "類型 [C++], CLR"
ms.assetid: 1ddd114e-be02-4de7-a4dd-a2d72ad8ff81
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Managed 類型 (C++/CL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從 Managed Extensions for C\+\+ 升級為 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 之後，Managed 型別的宣告以及建立和使用這些型別物件的語法已變更。  這麼做是為了在 ISO\-C\+\+ 型別系統中提升這些項目的整合性。  下列小節會詳細描述這些變更。  
  
## 本章節內容  
 [Managed 類別類型的宣告](../dotnet/declaration-of-a-managed-class-type.md)  
 討論如何宣告 Managed `class`、`struct` 或 `interface`。  
  
 [CLR 參考類別物件的宣告](../dotnet/declaration-of-a-clr-reference-class-object.md)  
 討論如何使用追蹤控制代碼宣告參考類別型別物件。  
  
 [CLR 陣列的宣告](../dotnet/declaration-of-a-clr-array.md)  
 解釋如何宣告及初始化陣列。  
  
 [建構函式初始設定順序的變更](../dotnet/changes-in-constructor-initialization-order.md)  
 討論類別建構函式初始設定順序的重大變更。  
  
 [解構函式語意的變更](../dotnet/changes-in-destructor-semantics.md)  
 討論不具決定性最終化、`Finalize` 和 `Dispose` 的比較、參考物件的細節，以及明確 `Finalize` 的使用。  
  
 **注意**：稍後在[委派和事件](../dotnet/delegates-and-events.md)的部分才會討論委派，因為要和類別中的事件成員以及[在類別或介面中的成員宣告 \(C\+\+\/CLI\)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)的一般主題同時說明委派  
  
## 請參閱  
 [C\+\+\/CLI 移轉入門](../dotnet/cpp-cli-migration-primer.md)   
 [Classes and Structs](../windows/classes-and-structs-cpp-component-extensions.md)   
 [Arrays](../windows/arrays-cpp-component-extensions.md)