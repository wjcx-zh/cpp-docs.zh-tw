---
title: "Boxing (C++/CLI) | Microsoft Docs"
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
ms.assetid: f4ee27a8-6a34-432d-b9ec-39285d513b23
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Boxing (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Boxing 是轉換實值型別處理序對`object` 型別或是由實值型別實作的任何介面型別。  當 Common Language Runtime \(CLR\) 對實值型別進行 Box 動作時，會在 Managed 堆積包裝在 `System.Object` 的值並儲存它。  Unbox 處理則會從物件中擷取實值類型。  Boxing 是隱含處理，unboxing 則是明確處理。  
  
## 相關文章  
  
|標題|說明|  
|--------|--------|  
|[如何：明確要求 Boxing](../dotnet/how-to-explicitly-request-boxing.md)|描述如何明確要求在變數的 Boxing。|  
|[如何：使用 gcnew 建立實值類型及使用隱含 Boxing](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)|示範如何使用 `gcnew` 建立在 Managed 可放置的 Boxed 實值型別，記憶體回收的堆積。|  
|[如何：Unbox](../dotnet/how-to-unbox.md)|顯示如何 Unbox 和修改值。|  
|[標準轉換和隱含 Boxing](../dotnet/standard-conversions-and-implicit-boxing.md)|表示標準轉換由要求 Boxing 轉換的編譯器選項。|  
|[以 C\+\+\/CLI 進行 .NET 程式設計](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|以 Visual C\+\+ 文件的 .NET 的父文件。|