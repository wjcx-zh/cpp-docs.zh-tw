---
title: "DATE Type | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "DATE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Date 資料型別"
  - "Date 資料型別, about Date data type"
  - "Date 資料型別, 實作"
  - "DATE type"
  - "hour values representation"
  - "MFC, 日期和時間"
ms.assetid: 695853ed-b614-4575-b793-b8c287372038
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# DATE Type
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用 SHA\-1 雜湊的浮點數值， **日期** 型別的實作。  天數由啟動整數的加入表示用而年 12 月將日，做為時間零的小時數。  小時值是以這個數字小數部分的絕對值。  下列資料表與其 **日期** 型別數字對等用法說明數個日期:  
  
|日期和時間。|表示|  
|------------|--------|  
|而年 12 月將日午夜，|0.00|  
|年年一月一日午夜，|2.00|  
|年年 1 月、日午夜，|5.00|  
|年年 1 月、日上午、點，..|5.25|  
|年年 1 月、日，中午|5.50|  
|年年 1 月、日下午一點，..|5.875|  
  
 **日期** 型別，以及 `COleDateTime` 類別，它表示日期和時間為傳統資料列編號。  `COleDateTime` 類別將與其他常見的資料格式中操作的日期值數種方法，其中包括轉換。  
  
 應注意下列問題，當與這些一起使用在 Automation 時的日期和時間格式:  
  
-   日期是以本地時間指定;，當使用日期不同時區時，必須手動執行同步處理。  
  
-   型別不佔日光節約時間。  
  
-   日期時間表變得不連續的日期值小於零 \(而 12 月將日之前\)。  這是因為，日期值的整數部分會分正負號，，而這個分數部分視為不帶正負號。  換句話說，反之，日期值的小數部分永遠會加入到整體邏輯日期，日期值的整數部分可能是正數或負數。  下表說明一些範例:  
  
|日期和時間。|表示|  
|------------|--------|  
|而年 12 月例日午夜，|\-3.00|  
|而年 12 月小數點日，中午|\-2.50|  
|而年 12 月小數點日午夜，|\-2.00|  
|而年 12 月多日午夜，|\-1.00|  
|而年 12 月將日下午、點，..|\-0.75|  
|而年 12 月將日，中午|\-0.50|  
|而年 12 月將日上午、點，..|\-0.25|  
|而年 12 月將日午夜，|0.00|  
|而年 12 月將日上午、點，..|0.25|  
|而年 12 月將日，中午|0.50|  
|而年 12 月將日下午、點，..|0.75|  
|而年 12 月有日午夜，|1.00|  
|年年一月一日午夜，|2.00|  
|年年一月一日，中午|2.50|  
|年年一月二日午夜，|3.00|  
  
> [!CAUTION]
>  請注意，因為 6:00 上午由分數值為 0.5，0.25 晚於表示相同的日期 **日期** 永遠表示不論表示日期是否為正數 \(在 12 月而將日以後\) 或負 \(而 12 月將日之前\)，簡單的浮動數比較會錯誤地排序代表 6:00 AM 的所有 **日期** 一日早於 12\/30\/1899 如 7:00 AM。  
  
 如需問題的詳細資訊 **日期** 和 `COleDateTime` 型別相關的功能可以在[COleDateTime Class](../atl-mfc-shared/reference/coledatetime-class.md) 和 [Date and Time: Automation Support](../atl-mfc-shared/date-and-time-automation-support.md)下。  
  
## 請參閱  
 [Date and Time](../atl-mfc-shared/date-and-time.md)   
 [COleDateTime Class](../atl-mfc-shared/reference/coledatetime-class.md)