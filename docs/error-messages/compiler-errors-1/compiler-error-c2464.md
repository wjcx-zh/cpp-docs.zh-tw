---
title: "編譯器錯誤 C2464 | Microsoft Docs"
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
  - "C2464"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2464"
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2464
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 無法使用 'new' 來配置參考  
  
 參考識別項是以 `new` 運算子配置。  參考並非記憶體物件，因此 `new` 無法傳回它們的指標。  請使用標準的變數宣告語法來宣告參考。  
  
 下列範例會產生 C2464：  
  
```  
// C2464.cpp  
int main() {  
   new ( int& ir );   // C2464  
}  
```