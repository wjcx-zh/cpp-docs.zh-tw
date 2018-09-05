---
title: 日期和時間： Automation 支援 |Microsoft Docs
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
ms.openlocfilehash: 38933847065544f97d60dfc109436f059a025f7a
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43763850"
---
# <a name="date-and-time-automation-support"></a>日期和時間： Automation 支援

本文說明如何利用的日期和時間的管理相關的類別程式庫服務。 所述的程序包括：

- [取得目前的時間](../atl-mfc-shared/current-time-automation-classes.md)

- [計算已耗用時間](../atl-mfc-shared/elapsed-time-automation-classes.md)

- [格式化日期/時間的字串表示法](../atl-mfc-shared/formatting-time-automation-classes.md)

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)類別提供一個方式來表示日期和時間資訊。 它提供更精細的資料粒度和更高的範圍比[CTime](../atl-mfc-shared/reference/ctime-class.md)類別。 [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md)類別代表經過時間，例如兩個之間的差異`COleDateTime`物件。

`COleDateTime`並`COleDateTimeSpan`類別設計來搭配`COleVariant`在自動化中使用的類別。 `COleDateTime` 和`COleDateTimeSpan`同樣也適用於 MFC 資料庫程式設計，但它們可以用每當您想要操作的日期和時間值。 雖然`COleDateTime`類別具有較大範圍的值和更細微的資料粒度比`CTime`類別，它需要更多的儲存體，每個物件，而非`CTime`。 使用基礎的日期類型時，也會產生一些特殊考量。 請參閱[日期類型](../atl-mfc-shared/date-type.md)如需詳細資訊，實作的日期。

`COleDateTime` 物件可用來代表 100 年 1 月 1 日和年 12 月 31 日之間的日期到 9999。 `COleDateTime` 物件浮動點值，其大約的解析度為 1 毫秒。 `COleDateTime` 下方之 MFC 文件中定義的日期資料類型根據[COleDateTime::operator 日期](../atl-mfc-shared/reference/coledatetime-class.md#operator_date)。 日期的實際實作延伸超出這些範圍。 `COleDateTime`實作加諸這些界限，為了方便處理的類別。

`COleDateTime` 不支援凱撒曆日期。 西曆會假設為及時往回擴充到 100 年 1 月 1 日。

`COleDateTime` 會忽略日光節約時間 (DST)。 下列程式碼範例會比較兩種方法可以計算跨越 DST 轉換日期的時間範圍： 一個使用 CRT，以及其他使用`COleDateTime`。 DST 切換，在大部分的地區設定中的第二週年 4 月和年 10 月的第三。

第一種方法可以設定兩個`CTime`物件， *time1*並*time2*年 4 月 5 和 6 年 4 月，分別使用標準的 C 類型結構`tm`和`time_t`。 程式碼會顯示*time1*並*time2*和它們之間的時間範圍。

第二個方法會建立兩個`COleDateTime`物件，`oletime1`並`oletime2`，並將它們設為相同的日期*time1*並*time2*。 它會顯示`oletime1`和`oletime2`和它們之間的時間範圍。

CRT 正確計算 23 個小時的差異。 `COleDateTimeSpan` 計算差異的 24 小時。

請注意，因應措施用於範例的結尾附近顯示正確使用日期`COleDateTime::Format`。 請參閱知識庫文章 「 BUG: Format("%D") 失敗`COleDateTime`和`COleDateTimeSpan`」 (Q167338)。

[!code-cpp[NVC_ATLMFC_Utilities#176](../atl-mfc-shared/codesnippet/cpp/date-and-time-automation-support_1.cpp)]

## <a name="see-also"></a>另請參閱

[日期和時間](../atl-mfc-shared/date-and-time.md)

