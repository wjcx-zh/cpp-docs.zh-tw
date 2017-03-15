---
title: "類型 int | Microsoft Docs"
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
  - "int 資料類型"
  - "可移植性 [C++], 類型 int"
  - "帶正負號的整數"
  - "類型 int"
ms.assetid: 0067ce9a-281e-491a-ae63-632952981e13
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 類型 int
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

帶正負號或不帶正負號 `int` 項目的大小是特定電腦上整數的標準大小。  例如，在 16 位元作業系統中，`int` 類型通常是 16 位元或 2 個位元組。  在 32 位元作業系統中，`int` 類型通常是 32 位元或 4 個位元組。  因此，根據目標環境而定，`int` 類型相當於 `short int` 或 **long int** 類型，而 `unsigned int` 類型相當於 **unsigned short** 或 `unsigned long` 類型。  除非另有指定，否則 `int` 類型皆表示帶正負號的值。  
  
 類型規範 `int` 和 `unsigned int` \(或 `unsigned`\) 會定義 C 語言的某些功能 \(例如，`enum` 類型\)。  在這些情況下，`int` 的定義和特定實作的 unsigned int 會判斷實際儲存區。  
  
 **Microsoft 特定的**  
  
 帶正負號的整數以二補數格式表示。  最高有效位元會保存此正負號：1 為負數，0 為正數及零。  值的範圍在 [C\+\+ 整數限制](../c-language/cpp-integer-limits.md) 中指定 \(可從 LIMITS.H 標頭檔中取得\)。  
  
 **END Microsoft 特定的**  
  
> [!NOTE]
>  int 和 unsigned int 類型規範廣泛使用在 C 程式中，因為它們允許特定電腦以該電腦的最有效的方法處理整數值。  不過，由於 int 和 unsigned int 類型的大小不同，取決於特定 int 大小的程式可能無法移植至其他電腦。  若要使程式更具有可攜性，您可以使用含 sizeof 運算子的運算式 \(如 [sizeof 運算子](../c-language/sizeof-operator-c.md) 中所述\) 而不是硬式編碼的資料大小。  
  
## 請參閱  
 [基本類型的儲存空間](../c-language/storage-of-basic-types.md)