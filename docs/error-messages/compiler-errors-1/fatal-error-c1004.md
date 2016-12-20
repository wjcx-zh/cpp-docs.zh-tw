---
title: "嚴重錯誤 C1004 | Microsoft Docs"
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
  - "C1004"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1004"
ms.assetid: dbe034b0-6eb0-41b4-a50c-2fccf9e78ad4
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1004
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

找到未預期的檔案結尾  
  
 編譯器在沒有解析建構情況下便遇到原始程式檔的結尾。  程式碼可能遺漏下列項目其中之一：  
  
-   右大括號  
  
-   右括號  
  
-   右邊的註解標記 \(\*\/\)  
  
-   分號  
  
 若要解決這項錯誤，請檢查下列任何一項：  
  
-   預設磁碟機空間不足，無法包含需要約原始程式檔兩倍大小的暫存檔。  
  
-   評估成 False 的 `#if` 指示詞缺少右邊的 `#endif` 指示詞。  
  
-   原始程式檔並未以歸位字元 \(Carriage Return\) 和換行字元 \(Line Feed\) 結束。  
  
 下列範例會產生 C1004：  
  
```  
// C1004.cpp  
#if TEST  
int main() {}  
// C1004  
```  
  
 可能的解決方案：  
  
```  
// C1004b.cpp  
#if TEST  
#endif  
  
int main() {}  
```