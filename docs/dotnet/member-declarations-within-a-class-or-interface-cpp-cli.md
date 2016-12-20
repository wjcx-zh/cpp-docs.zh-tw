---
title: "在類別或介面中的成員宣告 (C++/CLI) | Microsoft Docs"
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
  - "類別成員, 宣告語法"
  - "成員, 宣告語法"
ms.assetid: 95d312a4-198b-46f0-b8f5-15253807c55e
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在類別或介面中的成員宣告 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從 Managed Extensions for C\+\+ 升級為 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 之後，屬性和運算子的宣告已大幅變更，它隱藏了 Managed Extensions 設計中公開 \(Expose\) 的基礎實作 \(Implementation\) 的詳細資料。  事件宣告也已有所修改。  
  
 在沒有 Managed Extensions 支援的變更類別中，靜態建構函式 \(Constructor\) 現在可以非正規的方式定義 \(以前它們必須在 Managed Extensions 中內嵌地定義\)，並且引進了委派建構函式的概念。  
  
## 本章節內容  
 [屬性宣告](../dotnet/property-declaration.md)  
 討論屬性宣告的變更。  
  
 [屬性索引宣告](../dotnet/property-index-declaration.md)  
 討論索引屬性宣告的變更。  
  
 [委派和事件](../dotnet/delegates-and-events.md)  
 討論用於宣告委派 \(Delegate\) 和事件的語法變更。  
  
 [密封虛擬函式](../dotnet/sealing-a-virtual-function.md)  
 討論用於密封函式的語法變更。  
  
 [多載運算子](../dotnet/overloaded-operators.md)  
 討論運算子多載的變更。  
  
 [轉換運算子的變更](../dotnet/changes-to-conversion-operators.md)  
 討論轉換運算子的變更。  
  
 [介面成員的明確覆寫](../dotnet/explicit-override-of-an-interface-member.md)  
 討論明確覆寫介面成員的方法變更。  
  
 [私用虛擬函式](../dotnet/private-virtual-functions.md)  
 討論私用虛擬函式 \(Virtual Function\) 在衍生類別中處理方式的變更。  
  
 [靜態 Const 整數連結不再是常值](../dotnet/static-const-int-linkage-is-no-longer-literal.md)  
 討論 `static const` 整數成員連結方式，以及如何使用新的 `literal` 關鍵字宣告常數的變更。  
  
## 請參閱  
 [C\+\+\/CLI 移轉入門](../dotnet/cpp-cli-migration-primer.md)