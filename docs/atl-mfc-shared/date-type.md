---
title: 日期類型
ms.date: 11/04/2016
f1_keywords:
- DATE
helpviewer_keywords:
- Date data type, implementing
- Date data type
- DATE type
- Date data type, about Date data type
- MFC, date and time
- hour values representation
ms.assetid: 695853ed-b614-4575-b793-b8c287372038
ms.openlocfilehash: 6fd9fde83474ff4f439c0dd3989d4dc35fe1241a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317912"
---
# <a name="date-type"></a>日期類型

日期類型使用 8 位元組浮點編號實現。 天數由從 1899 年 12 月 30 日開始的整數增量表示,午夜為時間零。 小時值則以小數點後數字部分的絕對值來表示。 下表說明了多個日期及其 DATE 類型數值等效項:

|日期和時間|表示法|
|-------------------|--------------------|
|1899年12月30日,午夜|0.00|
|1900年1月1日,午夜|2.00|
|1900年1月4日,午夜|5.00|
|1900年1月4日,上午6時|5.25|
|1900年1月4日中午|5.50|
|1900年1月4日,晚上9時|5.875|

日期日期類型以及`COleDateTime`類將日期和時間表示為經典數字行。 該`COleDateTime`類包含幾種用於操作 DATE 值的方法,包括轉換到其他常見日期格式和轉換。

在自動化中使用這些日期和時間格式時,應注意以下幾點:

- 日期在本地時間指定;在不同時區處理日期時,必須手動執行同步。

- 日期類型不考慮夏令時。

- 日期時間線對於小於 0 的日期值變得不連續(1899 年 12 月 30 日之前)。 這是因為日期值的整數部分被視為已簽名,而小數部分則被視為未簽名。 換句話說,日期值的整數部分可以是正數或負數,而日期值的小數部分始終添加到整個邏輯日期。 下表說明了幾個範例:

|日期和時間|表示法|
|-------------------|--------------------|
|1899年12月27日,午夜|-3.00|
|1899年12月28日中午|-2.50|
|1899年12月28日,午夜|-2.00|
|1899年12月29日,午夜|-1.00|
|1899年12月30日下午6時|-0.75|
|1899年12月30日中午|-0.50|
|1899年12月30日,上午6時|-0.25|
|1899年12月30日,午夜|0.00|
|1899年12月30日,上午6時|0.25|
|1899年12月30日中午|0.50|
|1899年12月30日下午6時|0.75|
|1899年12月31日,午夜|1.00|
|1900年1月1日,午夜|2.00|
|1900年1月1日中午|2.50|
|1900年1月2日,午夜|3.00|

> [!CAUTION]
> 請注意,由於 6:00 AM 始終由分數值 0.25 表示,而不考慮表示該日期的整數是正數(1899 年 12 月 30 日之後)還是負值(1899 年 1 2 月 30 日之前),因此簡單的浮點比較會錯誤地將早於 12/30/1899 的一天 6:00 的 DATE 排序,以*晚於*當天 7:00 表示的日期。

有關日期和`COleDateTime`類型相關問題的詳細資訊,請參閱[COleDateTime 類別](../atl-mfc-shared/reference/coledatetime-class.md)和[日期和時間:自動化支援](../atl-mfc-shared/date-and-time-automation-support.md)。

## <a name="see-also"></a>另請參閱

[日期與時間](../atl-mfc-shared/date-and-time.md)<br/>
[COleDateTime 類別](../atl-mfc-shared/reference/coledatetime-class.md)
