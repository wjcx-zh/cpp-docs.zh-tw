---
title: "連結器工具錯誤 LNK2031 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK2031"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2031"
ms.assetid: 18ed4b6e-3e75-443c-bbd8-2f6030dc89ee
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 連結器工具錯誤 LNK2031
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法產生 "function\_declaration" decorated\_name 的 p\/invoke；中繼資料內遺漏呼叫慣例  
  
 嘗試將原生函式匯入純粹影像中時，切記隱含式呼叫慣例在原生與純粹編譯之間有差異。  如需純影像的詳細資訊，請參閱[純粹的和可驗證的程式碼](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。  
  
## 範例  
 這個程式碼範例會以其呼叫慣例為隱含式 [\_\_cdecl](../../cpp/cdecl.md) 的已匯出、原生函式產生元件。  
  
```  
// LNK2031.cpp  
// compile with: /LD  
extern "C" {  
   __declspec(dllexport) int func() { return 3; }  
};  
```  
  
## 範例  
 下列範例會建立使用原生函式的純粹用戶端。  但是 **\/clr:pure** 之下的呼叫慣例是 [\_\_clrcall](../../cpp/clrcall.md)。  下列範例會產生 LNK2031。  
  
```  
// LNK2031_b.cpp  
// compile with: /clr:pure LNK2031.lib  
// LNK2031 expected  
extern "C" int func();  
  
int main() {  
   return func();  
}  
```  
  
## 範例  
 下列範例會示範如何從純粹影像使用原生函式。  請注意明確的 **\_\_cdecl** 呼叫慣例規範。  
  
```  
// LNK2031_c.cpp  
// compile with: /clr:pure LNK2031.lib  
extern "C" int __cdecl func();  
  
int main() {  
   return func();  
}  
```