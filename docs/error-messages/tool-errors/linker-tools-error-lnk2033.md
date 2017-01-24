---
title: "連結器工具錯誤 LNK2033 | Microsoft Docs"
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
  - "LNK2033"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2033"
ms.assetid: d61db467-9328-4788-bf54-e2a20537f13f
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具錯誤 LNK2033
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法解析的 typeref 語彙基元 \(token\) \(對 'type' 而言\)  
  
 型別在 MSIL 中繼資料內沒有定義。  
  
 以 **\/clr:safe** 進行編譯時，可能會發生 LNK2033：在 MSIL 模組中只有型別的轉送宣告，但型別卻在 MSIL 模組中進行參考。  
  
 型別必須在 **\/clr:safe** 下加以定義。  
  
 如需詳細資訊，請參閱[\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
## 範例  
 下列範例會產生 LNK2033。  
  
```  
// LNK2033.cpp  
// compile with: /clr:safe  
// LNK2033 expected  
ref class A;  
ref class B {};  
  
int main() {  
   A ^ aa = nullptr;  
   B ^ bb = nullptr;   // OK  
};  
```