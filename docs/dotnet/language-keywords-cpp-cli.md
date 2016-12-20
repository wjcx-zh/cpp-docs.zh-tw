---
title: "語言關鍵字 (C++/CLI) | Microsoft Docs"
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
  - "關鍵字 [C++]"
ms.assetid: 021013b2-70ac-4df9-aa77-4af1c67a1a67
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 語言關鍵字 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從 Managed Extensions for C\+\+ 升級為 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 之後，有多個語言關鍵字已變更。  
  
 在新的 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 語法中，所有關鍵字的雙底線前置字元都已移除 \(只保留一個例外：`__identifier`\)。  例如，現在屬性的宣告方式為 `property`，而不是 `__property`。  
  
 在 Managed Extensions 中使用兩個相連底線前置字元有兩個主要的原因：  
  
-   這是提供區域擴充功能給 ISO\-C\+\+ Standard 的一致方式。  Managed Extensions 設計的其中一個主要目標是不要造成與標準語言不相容，例如新的關鍵字和語彙基元 \(Token\)。  主要就是基於這個原因，所以選擇使用指標語法來宣告 Managed 參考型別 \(Reference Type\) 的物件。  
  
-   除了一致性的考量外，使用雙底線也是為了確保不要破壞此語言使用者現有的程式碼基底 \(Code Base\)。  這是 Managed Extensions 設計的第二個主要目標。  
  
 儘管移除雙底線，Microsoft 仍致力於保持一致性。  但是，要支援 CLR 動態物件模型 \(Object Model\) 就表示需要新的、功能更強的程式設計開發架構 \(Programming Paradigm\)。  要支援這樣新的架構就需要自己的高階關鍵字和語彙基元 \(Token\)。  我們一直設法要為這種新的開發架構提供最佳的表示方式，同時加以整合並且支援標準語言。  新的語法設計為這兩種沒有共同點的物件模型提供一流的程式設計經驗。  
  
 同樣地，我們也注意要盡可能讓新語言關鍵字不破壞現有程式碼的特性。  因此，我們採用了內容關鍵字以及含空格的關鍵字。  在我們進一步說明新的語言語法之前，讓我們先解釋這兩種特殊關鍵字的特性。  
  
 內容關鍵字在特定的程式內容中具有特殊意義。  例如，在一般的程式中會將 `sealed` 視為普通的識別項，  但是，當它出現在 Managed 參考類別型別的宣告部分時，則會將它視為該類別 \(Class\) 宣告內容中的關鍵字。  這麼做可以減少在語言中引入新的關鍵字時所可能造成的破壞性影響，我們認為這點對目前已有程式碼基底的使用者來說非常重要。  同時，這麼做也可以讓新功能的使用者充分體驗到新增加之語言功能的好處，這是使用 Managed Extensions 所做不到的。  如需如何使用 `sealed` 的範例，請參閱 [Managed 類別類型的宣告](../dotnet/declaration-of-a-managed-class-type.md)。  
  
 含空格的關鍵字 \(例如 `value class`\) 是內容關鍵字的一種特殊案例。  它將現有的關鍵字與內容修飾詞 \(Modifier\) 配成對，並以空格分隔。  此配對被視為一個單位，而不是兩個單獨的關鍵字。  
  
## 請參閱  
 [C\+\+\/CLI 移轉入門](../dotnet/cpp-cli-migration-primer.md)   
 [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)