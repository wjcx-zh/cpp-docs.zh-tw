---
title: "C++ 位元欄位 | Microsoft Docs"
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
helpviewer_keywords: 
  - "位元欄位"
  - "bitfields"
  - "欄位 [C++], 位元"
ms.assetid: 6f4b62e3-cc1d-4e5d-bf34-05904104f71a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C++ 位元欄位
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

類別和結構可包含比整數類型佔用較少儲存區的成員。  這些成員指定為位元欄位。  位元欄位 *member\-declarator* 規格的語法如下：  
  
## 語法  
  
```  
  
declarator  : constant-expression  
```  
  
## 備註  
 \(選擇性\) `declarator` 是在程式中用來存取成員的名稱。  它必須是整數類資料類型 \(包括列舉類型\)。  *constant\-expression* 指定成員在結構中佔用的位元數目。  匿名位元欄位 \(亦即沒有識別項的位元欄位成員\) 可用於填補。  
  
> [!NOTE]
>  未命名且寬度 0 的位元欄位會將下一個位元欄位強制對齊到下一個 `type` 界限，其中 `type` 為成員的類型。  
  
 下列範例宣告包含位元欄位的結構：  
  
```  
// bit_fields1.cpp  
// compile with: /LD  
struct Date {  
   unsigned short nWeekDay  : 3;    // 0..7   (3 bits)  
   unsigned short nMonthDay : 6;    // 0..31  (6 bits)  
   unsigned short nMonth    : 5;    // 0..12  (5 bits)  
   unsigned short nYear     : 8;    // 0..100 (8 bits)  
};  
```  
  
 `Date` 類型物件的概念性記憶體配置如下圖所示。  
  
 ![Date 物件的記憶體配置](../cpp/media/vc38uq1.png "vc38UQ1")  
Date 物件的記憶體配置  
  
 請注意 `nYear` 長度為 8 位元且會造成宣告類型 **unsigned short** 的字邊界溢位。  因此，它會在新 **unsigned short** 的開頭處開始。  不需要所有位元欄位都調整至基礎類型的一個物件中；新的單位儲存根據宣告所要求的位元數目進行配置。  
  
 **Microsoft 特定的**  
  
 宣告為位元欄位的資料之順序是由低至高位元，如上面的圖所示。  
  
 **END Microsoft 特定的**  
  
 如果結構的宣告包含未命名且長度為 0 的欄位，如下列範例所示：  
  
```  
// bit_fields2.cpp  
// compile with: /LD  
struct Date {  
   unsigned nWeekDay  : 3;    // 0..7   (3 bits)  
   unsigned nMonthDay : 6;    // 0..31  (6 bits)  
   unsigned           : 0;    // Force alignment to next boundary.  
   unsigned nMonth    : 5;    // 0..12  (5 bits)  
   unsigned nYear     : 8;    // 0..100 (8 bits)  
};  
```  
  
 記憶體配置如下圖所示。  
  
 ![具有長度為零之位元欄位的 Date 物件配置](../cpp/media/vc38uq2.png "vc38UQ2")  
具有長度為零之位元欄位的 Date 物件配置  
  
 位元欄位的基礎類型必須是整數類資料類型，如[基本類型](../cpp/fundamental-types-cpp.md)中所述。  
  
## 位元欄位的限制  
 下列清單詳細說明位元欄位的錯誤作業：  
  
1.  取得位元欄位的位址。  
  
2.  使用位元欄位初始化參考。  
  
## 請參閱  
 [類別和結構](../cpp/classes-and-structs-cpp.md)