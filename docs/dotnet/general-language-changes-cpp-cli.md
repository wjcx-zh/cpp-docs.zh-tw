---
title: "一般的語言變更 (C++/CLI) | Microsoft Docs"
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
ms.assetid: 79a70768-225c-4ae2-84d1-178b20a9b042
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 一般的語言變更 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從 Managed Extensions for C\+\+ 升級為 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 之後，某些 CLR 語言的功能都已變更。  
  
 本節所描述的變更算是一種語言雜錄。  內容包含字串常值 \(String Literal\) 處理的變更、省略和 `Param` 屬性之間進行多載解析 \(Overload Resolution\) 的變更、將 `typeof` 改成 `typeid` 的變更、建構函式初始設定式清單呼叫的變更，以及屬於 `safe_cast` 之新轉型標記法的引入。  
  
 [字串常值](../dotnet/string-literal.md)  
 討論字串常值的處理如何變更。  
  
 [Param 陣列和省略](../dotnet/param-array-and-ellipsis.md)  
 討論當使用變動數目的引數解析函式呼叫 \(Function Call\) 時，`ParamArray` 如何優先於省略符號 \(`…`\)。  
  
 [typeof 變成 T::typeid](../dotnet/typeof-goes-to-t-typeid.md)  
 討論已由 `typeid` 取代 `typeof` 運算子的情形。  
  
 [初始設定式清單](../dotnet/initializer-lists.md)  
 討論初始設定式清單的呼叫順序變更。  
  
 [safe\_cast\<\> 的轉換通知和簡介](../dotnet/cast-notation-and-introduction-of-safe-cast-angles.md)  
 討論轉換通知的變更，特別是 `safe_cast` 的簡介。  
  
## 請參閱  
 [C\+\+\/CLI 移轉入門](../dotnet/cpp-cli-migration-primer.md)