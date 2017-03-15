---
title: "內嵌組譯碼中的類型和變數大小 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "length"
  - "Type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "內嵌組譯碼, 運算子"
  - "LENGTH 運算子"
  - "大小"
  - "SIZE 運算子"
  - "大小, 在內嵌組譯碼中取得"
  - "TYPE 運算子"
  - "變數, 長度"
  - "變數, 大小"
  - "變數, 類型"
ms.assetid: b62c2f2b-a7ad-4145-bae4-d890db86d348
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 內嵌組譯碼中的類型和變數大小
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定**  
  
 **長度**， **大小**，和 **型別**運算子在內嵌組譯碼中有限制的意義。  它們不能完全與`DUP`運算子 \(因為您不能定義 MASM 指示詞或運算子的資料\)。  但是，您可以使用它們來尋找 C 或 c \+ \+ 的變數或型別的大小：  
  
-   **長度**運算子可傳回陣列中的元素數目。  它會傳回非陣列變數的值 1。  
  
-   **大小**運算子可傳回 C 或 c \+ \+ 變數的大小。  變數的大小是其**長度** 和 **型別**。  
  
-   **型別**運算子可傳回 C 或 c \+ \+ 型別或變數的大小。  如果變數是陣列中， **型別**會傳回單一元素陣列的大小。  
  
 例如，如果您的程式有 8\-項目`int`陣列，  
  
```  
int arr[8];  
```  
  
 下列的 C 和組件運算式產生的大小`arr`和其項目。  
  
|\_\_asm|C|大小|  
|-------------|-------|--------|  
|**長度** arr|`sizeof`\(arr\)\/`sizeof`\(arr\[0\]\)|8|  
|**大小** arr|`sizeof`\(\) arr|32|  
|**TYPE** arr|`sizeof`\(arr\[0\]\)|4|  
  
 **結束 Microsoft 特定**  
  
## 請參閱  
 [在 \_\_asm 區塊中使用組合語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)