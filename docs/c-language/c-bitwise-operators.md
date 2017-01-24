---
title: "C 位元運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "& 運算子, 位元運算子"
  - "^ 運算子"
  - "^ 運算子, 位元運算子"
  - "| 運算子, 位元運算子"
  - "Ampersand 運算子 (&)"
  - "AND 運算子"
  - "位元運算子"
  - "位元運算子, Visual C"
  - "運算子 [C], 位元"
ms.assetid: e22127b1-9a2d-4876-b01d-c8f72cec3317
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C 位元運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

位元運算子執行位元 AND \(**&**\)，位元 Exclusive\-OR \(**^**\)，以及位元 Inclusive\-OR \(       **&#124;** \) 運算。  
  
 **語法**  
  
 *AND 運算式* :  
 *相等運算式*  
  
 *AND 運算式*  **&**  *相等運算式*  
  
 *Exclusive\-OR 運算式*:  
 *AND 運算式。*  
  
 *Exclusive\-OR 運算式*  **^**  *AND 運算式*  
  
 *Inclusive\-OR 運算式*:  
 *Exclusive\-OR 運算式*  
  
 *Ixclusive\-OR 運算式* &#124; *Exclusive\-OR 運算式*  
  
 位元運算子的運算元必須為整數，不過，它們的型別可以是不同的。  此類運算子執行一般算術轉換; 轉換結果的型別與運算元的型別相同。  
  
 C 位元運算子如下:  
  
|運算子|描述|  
|---------|--------|  
|**&**|位元 AND 運算子將第一個運算元與第二個運算元的每個對應位元作比較。  如果兩個位元都是 1，對應的結果位元設為 1。  否則，對應的結果位元設為 0。|  
|**^**|位元 exclusive\-OR 運算子將第一個運算元與第二個運算元的每個對應位元作比較。  如果一個位元為 0，而另一個位元為 1，對應的結果位元設為 1。  否則，對應的結果位元設為 0。|  
|**&#124;**|位元 inclusive\-OR 運算子將第一個運算元與第二個運算元的每個對應位元作比較。  如果任一位元為 1，對應的結果位元設為 1。  否則，對應的結果位元設為 0。|  
  
## 範例  
 這些宣告為下列三個範例所使用:  
  
```  
short i = 0xAB00;  
short j = 0xABCD;  
short n;  
  
n = i & j;  
```  
  
 第一個範例中結果賦值至 `n` 與 `i` 0xAB00 \(十六位元\) 相同。  
  
```  
n = i | j;  
  
n = i ^ j;  
```  
  
 第二個範例中位元 Inclusive\-OR 結果為 0xABCD \(十六位元\)，而在第三個範例位元 Exclusive\-OR 產生 0xCD \(十六位元\)。  
  
 **Microsoft 專有的**  
  
 在帶正負號的整數上的位元運算結果是由遵循 ANSI C 標準的實作環境決定。  如果是 Microsoft C 編譯器，帶正負號的整數的位元運算運作方式與不帶正負號的整數的位元運算相同。  例如，`-16 & 99` 可以用二進制表示為  
  
```  
  11111111 11110000  
& 00000000 01100011  
  _________________  
  00000000 01100000  
```  
  
 位元 AND 的結果為十進位的 96。  
  
 **END Microsoft 專有**  
  
## 請參閱  
 [位元 AND 運算子：&](../cpp/bitwise-and-operator-amp.md)   
 [位元互斥 OR 運算子：^](../cpp/bitwise-exclusive-or-operator-hat.md)   
 [位元非互斥 OR 運算子：&#124;](../cpp/bitwise-inclusive-or-operator-pipe.md)