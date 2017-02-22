---
title: "連結器工具錯誤 LNK1301 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1301"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1301"
ms.assetid: 760da428-7182-4b25-b20a-de90d4b9a9cd
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 連結器工具錯誤 LNK1301
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

找到 LTCG clr 模組，與 \/LTCG:parameter 不相容  
  
 傳遞了使用 \/clr 和 \/GL 編譯的模組給連結器，並附上 \/LTCG 的其中一個特性指引最佳化 \(PGO\) 參數。  
  
 特性指引最佳化不支援 \/clr 模組。  
  
 如需詳細資訊，請參閱：  
  
-   [\/GL \(整個程式最佳化\)](../../build/reference/gl-whole-program-optimization.md)  
  
-   [\/LTCG \(連結時間產生程式碼\)](../../build/reference/ltcg-link-time-code-generation.md)  
  
-   [\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [特性指引最佳化](../../build/reference/profile-guided-optimizations.md)  
  
### 更正這個錯誤  
  
1.  請不要使用 \/clr 編譯，也不要使用其中一個 PGO 參數與 \/LTCG 連結。  
  
## 範例  
 下列範例會產生 LNK1301：  
  
```  
// LNK1301.cpp  
// compile with: /clr /GL /link /LTCG:PGI LNK1301.obj  
// LNK1301 expected  
class MyClass {  
public:  
   int i;  
};  
```