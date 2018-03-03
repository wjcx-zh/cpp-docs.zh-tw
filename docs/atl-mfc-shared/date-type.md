---
title: "DATE 類型 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- DATE
dev_langs:
- C++
helpviewer_keywords:
- Date data type, implementing
- Date data type
- DATE type
- Date data type, about Date data type
- MFC, date and time
- hour values representation
ms.assetid: 695853ed-b614-4575-b793-b8c287372038
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1f1ed7eb2b467fd52545f65f98b87e8e34ad71f3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="date-type"></a>DATE 類型
**日期**類型會實作使用 8 位元組浮點數。 日期會以累進整數從 1899 年 12 月 30 日午夜時間為零。 小時值會表示為絕對值的數字的小數部分。 下表說明數個日期，連同其**日期**類型數值對等項目：  
  
|日期和時間|表示法|  
|-------------------|--------------------|  
|1899 年 12 月 30日日午夜|0.00|  
|1900 年 1 月 1日日午夜|2.00|  
|1900 年 1 月 4日日午夜|5.00|  
|1900 年 1 月 4日日上午 6|5.25|  
|4 1900 年 1 月中午|5.50|  
|1900 年 1 月 4日日下午 9|5.875|  
  
 **日期**日期類型，並將`COleDateTime`類別，表示日期和時間做為傳統的數字一行。 `COleDateTime`類別包含數個方法來操作日期值，包括其他常見的日期格式的來回轉換。  
  
 在自動化中的這些日期和時間格式使用時，應該注意下列幾點：  
  
-   日期會指定以本地時間;使用不同的時區中的日期時，必須手動執行同步處理。  
  
-   日期型別不會考慮日光節約時間。  
  
-   日期時間軸會變成不連續的日期值小於 0 （1899年前的 30 年 12 月）。 這是因為日期值的整數部分會視為帶正負號，而分數部分會被視為為不帶正負號。 換句話說，日期值的整數部分可能正或負的而日期值的小數部分永遠會加入到整個邏輯日期。 下表將說明一些範例：  
  
|日期和時間|表示法|  
|-------------------|--------------------|  
|1899 年 12 月 27日日午夜|-3.00|  
|28 1899 年中午|-2.50|  
|1899 年 12 月 28日日午夜|-2.00|  
|1899 年 12 月 29日日午夜|-1.00|  
|1899 年 12 月 30日日下午 6 點。|-0.75|  
|30 1899 年中午|-0.50|  
|1899 年 12 月 30日日上午 6 點|-0.25|  
|1899 年 12 月 30日日午夜|0.00|  
|1899 年 12 月 30日日上午 6 點|0.25|  
|30 1899 年中午|0.50|  
|1899 年 12 月 30日日下午 6 點。|0.75|  
|1899 年 12 月 31日日午夜|1.00|  
|1900 年 1 月 1日日午夜|2.00|  
|1 年 1 月 1900 年中午|2.50|  
|1900 年 1 月 2日日午夜|3.00|  
  
> [!CAUTION]
>  請注意，因為 6:00 AM 一律由小數值 0.25 不論代表日期的整數 （之後 1899 年 12 月 30 日) 中是否正或負 （之前 1899 年 12 月 30 日)，簡單的浮動點比較會錯誤地排序任何**日期**代表早於 12/30/1899 做為每日上午 6:00*稍後*比**日期**代表該相同日上午 7:00。  
  
 問題的詳細資訊與相關**日期**和`COleDateTime`類型可以在下找到[COleDateTime 類別](../atl-mfc-shared/reference/coledatetime-class.md)和[日期和時間： 自動化支援](../atl-mfc-shared/date-and-time-automation-support.md)。  
  
## <a name="see-also"></a>請參閱  
 [日期和時間](../atl-mfc-shared/date-and-time.md)   
 [COleDateTime 類別](../atl-mfc-shared/reference/coledatetime-class.md)

