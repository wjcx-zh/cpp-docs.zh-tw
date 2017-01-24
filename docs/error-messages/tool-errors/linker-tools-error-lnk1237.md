---
title: "連結器工具錯誤 LNK1237 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1237"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1237"
ms.assetid: 8722ffa8-096a-4bb0-85f9-f3aa0e10872a
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具錯誤 LNK1237
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在程式碼產生期間，編譯器引入了符號 'symbol' \(在以 \/GL 編譯的模組 'module' 中定義\) 的參考  
  
 在程式碼產生期間，編譯器不應該引入稍後將解析成 **\/GL** 所編譯定義的符號。  `symbol` 就是引入的符號，且稍後將解析成用 **\/GL** 編譯的定義。  
  
 如需詳細資訊，請參閱[\/GL \(整個程式最佳化\)](../../build/reference/gl-whole-program-optimization.md)。  
  
 若要解決 LNK1237 錯誤，請不要使用 **\/GL** 編譯符號，也不要使用 [\/INCLUDE \(強制符號參考\)](../../build/reference/include-force-symbol-references.md) 強制執行符號參考。  
  
## 範例  
 下列範例將產生 LNK1237。  若要解決這個問題，請不要初始化 LNK1237\_a.cpp 中的陣列並將 **\/include:\_\_chkstk** 加入到連結命令。  
  
```  
// LNK1237_a.cpp  
int main() {  
   char c[5000] = {0};  
}  
```  
  
```  
// LNK1237_b.cpp  
// compile with: /GS- /GL /c LNK1237_a.cpp  
// processor: x86  
// post-build command: (lib LNK1237_b.obj /LTCG & link LNK1237_a.obj LNK1237_b.lib /nodefaultlib /entry:main /LTCG)  
extern "C" void _chkstk(size_t s) {}  
```