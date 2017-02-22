---
title: "連結器工具錯誤 LNK2028 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK2028"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2028"
ms.assetid: e2b03293-6066-464d-a050-ce747bcf7f0e
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# 連結器工具錯誤 LNK2028
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

"exported\_function" \(decorated\_name\) 在函式 "function\_containing\_function\_call" \(decorated\_name\) 中進行參考  
  
 嘗試將原生函式匯入純粹影像中時，切記隱含式呼叫慣例在原生與純粹編譯之間有差異。  
  
## 範例  
 這個程式碼範例會以其呼叫慣例為隱含式 [\_\_cdecl](../../cpp/cdecl.md) 的已匯出、原生函式產生元件。  
  
```  
// LNK2028.cpp  
// compile with: /LD  
__declspec(dllexport) int func() {  
   return 3;  
}  
```  
  
## 範例  
 下列範例會建立使用原生函式的純粹用戶端。  但是 **\/clr:pure** 之下的呼叫慣例是 [\_\_clrcall](../../cpp/clrcall.md)。  下列範例會產生 LNK2028。  
  
```  
// LNK2028_b.cpp  
// compile with: /clr:pure lnk2028.lib  
// LNK2028 expected  
int func();  
  
int main() {  
   return func();  
}  
```