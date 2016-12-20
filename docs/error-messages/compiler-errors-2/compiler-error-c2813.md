---
title: "編譯器錯誤 C2813 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2813"
ms.assetid: 6cf2135f-7b82-42d1-909a-5e864308a09c
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2813
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 \/MP 時不支援 \#import  
  
 如果您在編譯器命令中指定 **\/MP** 編譯器選項以及要編譯的兩個以上檔案，而且一個或多個檔案包含 [\#import](../../preprocessor/hash-import-directive-cpp.md) 前置處理器指示詞，則會發出 C2813。[\#import](../../preprocessor/hash-import-directive-cpp.md) 指示詞會從所指定類型程式庫的類型中產生 C\+\+ 類別，然後將這些類別寫入至兩個標頭檔。 不支援 [\#import](../../preprocessor/hash-import-directive-cpp.md) 指示詞，因為如果多個編譯單位匯入相同的類型程式庫，而這些單位在嘗試同時寫入相同的標頭檔時會衝突。  
  
 這個編譯器錯誤和 **\/MP** 編譯器選項是 [!INCLUDE[vs_orcas_long](../../atl/reference/includes/vs_orcas_long_md.md)] 中的新項目。  
  
## 範例  
 下列範例會產生 C2813。 "compile with:" 註解中的命令列表示編譯器使用 **\/MP** 和 **\/c** 編譯器選項來編譯數個檔案。 其中至少有一個檔案包含 [\#import](../../preprocessor/hash-import-directive-cpp.md) 指示詞。 我們為了測試這個範例使用相同的檔案兩次。  
  
```  
// C2813.cpp // compile with: /MP /c C2813.cpp C2813.cpp #import "C:\windows\system32\stdole2.tlb"   // C2813 int main() { }  
```