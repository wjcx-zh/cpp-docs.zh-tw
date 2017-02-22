---
title: "整數降級 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "降級整數"
ms.assetid: 51fb3654-60b0-4de7-80eb-bd910086c18a
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 整數降級
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 3.2.1.2**：將整數轉換為較短的帶正負號整數的結果，或將不帶正負號的整數轉換為長度相等的帶正負號整數的結果 \(如果值無法表示的話\)  
  
 當 **long** integer 轉型成 **short**，或者 **short** 轉型成 `char` 時，會保留最小顯著性位元組。  
  
 例如，在下列程式碼中  
  
```  
short x = (short)0x12345678L;  
```  
  
 指派值 0x5678 給 `x`，以及下列程式碼  
  
```  
char y = (char)0x1234;  
```  
  
 指派值 0x34 給 `y`。  
  
 當帶正負號的變數轉換為不帶正負號的變數 \(反之亦然\) 時，其位元模式會保持不變。  例如，將–2 \(0xFE\) 轉型為不帶正負號的值會產生 254 \(亦為 0xFE\)。  
  
## 請參閱  
 [整數](../c-language/integers.md)