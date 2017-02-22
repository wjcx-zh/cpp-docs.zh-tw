---
title: "編譯器錯誤 C2390 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2390"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2390"
ms.assetid: 06b749ee-d072-4db1-b229-715f2c0728b5
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器錯誤 C2390
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 不正確的儲存類別 'specifier'  
  
 此儲存類別不是全域範圍識別項的有效儲存類別。  預設的儲存類別將取代無效的類別。  
  
 可能的解決方案：  
  
-   如果識別項為函式，請以 `extern` 儲存類別來宣告它。  
  
-   如果識別項為型式參數或區域變數，請以自動儲存類別來宣告它。  
  
-   如果識別項為全域變數，請以無儲存類別 \(自動儲存類別\) 來宣告它。  
  
## 範例  
  
-   下列範例會產生 C2390：  
  
```  
// C2390.cpp  
register int i;   // C2390  
  
int main() {  
   register int j;   // OK  
}  
```