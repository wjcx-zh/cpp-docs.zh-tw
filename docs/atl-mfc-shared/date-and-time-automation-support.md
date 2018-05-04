---
title: 日期和時間： 自動化支援 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- adding dates
- calculating dates and times
- formatting [Visual Studio], dates
- dates, Automation support
- elapsed time, calculating in Automation
- COleDateTime class, Automation date/time support
- COleDateTimeSpan class, Automation date/time support
- Automation, date and time support
- formatting [Visual Studio], time
- calculations, date and time
- time [Visual Studio], Automation support
ms.assetid: 6eee94c4-943d-4ffc-bf7c-bdda89337ab0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 915bcd5487f423b6240061a0e85f5554a3224397
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="date-and-time-automation-support"></a>日期和時間： 自動化支援
本文說明如何利用的日期和時間管理相關的類別程式庫服務。 描述程序包括：  
  
-   [取得目前的時間](../atl-mfc-shared/current-time-automation-classes.md)  
  
-   [計算已耗用時間](../atl-mfc-shared/elapsed-time-automation-classes.md)  
  
-   [格式化日期/時間的字串表示法](../atl-mfc-shared/formatting-time-automation-classes.md)  
  
 [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)類別會提供方法來表示日期和時間資訊。 它提供更精細的資料粒度和更高的範圍比[CTime](../atl-mfc-shared/reference/ctime-class.md)類別。 [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md)類別代表經過時間，例如兩個之間的差異`COleDateTime`物件。  
  
 `COleDateTime`和`COleDateTimeSpan`類別設計來搭配`COleVariant`在自動化中使用的類別。 `COleDateTime` 和`COleDateTimeSpan`同樣也適用於 MFC 資料庫程式撰寫，但它們可以在每當您想要處理日期和時間值。 雖然`COleDateTime`類別具有較大範圍的值和更精細的資料粒度比`CTime`類別，它需要更多的存放裝置，每個物件，而非`CTime`。 另外還有一些特殊考量使用的基礎時**日期**型別。 請參閱[日期類型](../atl-mfc-shared/date-type.md)詳細的實作**日期**。  
  
 `COleDateTime` 物件可以用來代表 100 年 1 月 1 日和年 12 月 31 日之間的日期到 9999。 `COleDateTime` 物件浮動點值，其大約的解析度為 1 毫秒。 `COleDateTime` 根據**日期**下 MFC 文件中所定義的資料類型[COleDateTime::operator 日期](../atl-mfc-shared/reference/coledatetime-class.md#operator_date)。 實際實作**日期**超出這些範圍。 `COleDateTime`實作會加諸這些範圍，以方便使用的類別。  
  
 `COleDateTime` 不支援凱撒曆日期。 假設西曆回到過去擴充到 100 年 1 月 1 日。  
  
 `COleDateTime` 會忽略日光節約時間 (DST)。 下列程式碼範例會比較計算跨越 DST 轉換日期的時間範圍的兩種方法： 一個使用 CRT 的資訊，以及其他使用`COleDateTime`。 DST 切換，在大部分的地區設定中的第二週年 4 月和年 10 月的第三。  
  
 第一種方法可以設定兩個`CTime`物件*time1*和*time2*5 年 4 月和年 4 月 6 分別使用標準的 C 類型結構**tm**和`time_t`. 程式碼會顯示*time1*和*time2*和它們之間的時間範圍。  
  
 第二個方法會建立兩個`COleDateTime`物件`oletime1`和`oletime2`，並將它們設定為相同的日期做為*time1*和*time2*。 它會顯示`oletime1`和`oletime2`和它們之間的時間範圍。  
  
 CRT 正確計算 23 小時的差異。 `COleDateTimeSpan` 計算的 24 小時內的差異。  
  
 請注意的因應措施範例結尾附近用來顯示日期正確使用`COleDateTime::Format`。 請參閱知識庫文章 「 錯誤： Format("%D") 失敗`COleDateTime`和`COleDateTimeSpan`」 (Q167338)。  
  
 [!code-cpp[NVC_ATLMFC_Utilities#176](../atl-mfc-shared/codesnippet/cpp/date-and-time-automation-support_1.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [日期和時間](../atl-mfc-shared/date-and-time.md)

