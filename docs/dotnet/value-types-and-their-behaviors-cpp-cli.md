---
title: "實值類型和行為 (C++/CLI) | Microsoft Docs"
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
  - "實值類型"
ms.assetid: 5cb872a6-1e0a-429d-853d-df4ab47e8f2a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 實值類型和行為 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從 Managed Extensions for C\+\+ 升級為 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 之後，實值型別 \(Value Type\) 已有許多方面的改變。  在本節中，將會探討 CLR 列舉型別以及實值類別型別、在 CLR 堆積 \(Heap\) 上 Boxing 和存取 Boxed 執行個體，以及內部和 Pin 指標。  在本區域中已有許多語言變更。  
  
## 本章節內容  
 [CLR Enum Type](../dotnet/value-types-and-their-behaviors-cpp-cli.md)  
 討論列舉宣告和行為的變更。  
  
 [實值類型的隱含 Boxing](../dotnet/implicit-boxing-of-value-types.md)  
 討論針對實值型別之隱含 Boxing 的動機，以及在行為上隨之而來的變更。  
  
 [Boxed 值的追蹤控制代碼](../dotnet/a-tracking-handle-to-a-boxed-value.md)  
 討論如何將實值型別的隱含 Boxing 轉譯至追蹤控制代碼，再轉譯至 Boxed 實值物件。  
  
 [實值類型語意](../dotnet/value-type-semantics.md)  
 討論實值型別語意 \(Semantics\) 的變更，包括繼承的虛擬方法、類別預設建構函式 \(Constructor\)、內部指標和 Pin 指標。  
  
## 請參閱  
 [C\+\+\/CLI 移轉入門](../dotnet/cpp-cli-migration-primer.md)   
 [Classes and Structs](../windows/classes-and-structs-cpp-component-extensions.md)