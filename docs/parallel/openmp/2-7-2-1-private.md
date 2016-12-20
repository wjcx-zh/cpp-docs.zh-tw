---
title: "2.7.2.1 private | Microsoft Docs"
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
ms.assetid: 079b4b84-f2b3-4050-a0ac-289493c36b3d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.7.2.1 private
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`private`子句宣告為私用給小組中的每個執行緒的變數清單中的變數。  語法`private`子句是，如下所示：  
  
```  
private(variable-list)  
```  
  
 變數中所指定的行為`private`子句是，如下所示。  此建構配置新的物件自動存放工期的任務。  新物件的對齊方式和調整是由變數的型別所決定。  此配置發生一次每個執行緒在小組成員，並叫用預設建構函式類別物件，如有必要的。 否則預設值是不確定的。  變數所參考的原始物件的不定的值到建構函式進入時，絕不能修改建構，動態範圍內並具有在建構從結束時的不定值。  
  
 在此指示詞建構之語彙範圍內，變數會參考由執行緒配置新的私用物件。  
  
 若要限制`private`子句如下：  
  
-   類別型別中所指定的變數`private`子句必須要有一個可存取的、 模稜兩可的預設建構函式。  
  
-   在指定的變數`private`子句不能 **const**\-限定型別，除非它具有類別型別，有`mutable`成員。  
  
-   在指定的變數`private`子句必須沒有不完整型別或參考型別。  
  
-   在出現的變數`reduction`的子句**平行**指示詞不能在指定`private`工作共用的指示詞，以便繫結到平行建構函式上的子句。