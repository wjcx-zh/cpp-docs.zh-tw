---
title: 日期和時間
ms.date: 08/13/2019
helpviewer_keywords:
- time, MFC programming
- time
- MFC, date and time
- dates, MFC
ms.assetid: ecf56dc5-d418-4603-ad3e-af7e205a6403
ms.openlocfilehash: 2a5e6977acfca51b8074399f6f9b3166c8a358bc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491303"
---
# <a name="date-and-time"></a>日期和時間

MFC 支援數種不同的日期和時間處理方式:

- Automation [DATE 資料類型](../atl-mfc-shared/date-type.md)的支援。 日期支援日期、時間和日期/時間值。 [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)和[COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md)類別會封裝這種功能。 它們會使用自動化支援來處理[COleVariant](../mfc/reference/colevariant-class.md)類別。

- 一般用途的時間類別。 [CTime](../atl-mfc-shared/reference/ctime-class.md)和[CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md)類別會封裝與 ANSI 標準時間程式庫相關聯的大部分功能, 這是以時間宣告。H.

- 系統時鐘的支援。 使用 MFC 3.0 版時, 會針對 Win32 `CTime` `SYSTEMTIME`和`FILETIME`資料類型, 將支援新增至。

## <a name="date-and-time-automation-support"></a>日期和時間:自動化支援

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)類別提供一種方式來表示日期和時間資訊。 它提供更細微的細微性, 而且範圍比[CTime](../atl-mfc-shared/reference/ctime-class.md)類別更大。 [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md)類別代表經過時間, 例如兩個`COleDateTime`物件之間的差異。

和類別是設計用來與類別搭配使用。`COleVariant` `COleDateTimeSpan` `COleDateTime` `COleDateTime`和`COleDateTimeSpan`在 MFC 資料庫程式設計中也很有用, 但只要您想要操作日期和時間值, 就可以使用這些方法。 雖然類別具有較大範圍的值和`CTime`比類別更精細的細微性, 但它需要每個物件的儲存空間超過。 `CTime` `COleDateTime` 使用基礎日期類型時, 也有一些特殊的考慮。 如需日期執行的詳細資訊, 請參閱[日期類型](../atl-mfc-shared/date-type.md)。

`COleDateTime`物件可以用來代表100年1月1日到9999年12月31日之間的日期。 `COleDateTime`物件是浮點值, 其近似解析度為1毫秒。 `COleDateTime`是以 DATE 資料類型為基礎, 在 MFC 檔的[COleDateTime:: OPERATOR DATE](../atl-mfc-shared/reference/coledatetime-class.md#operator_date)底下定義。 實際的日期執行延伸超出這些界限。 `COleDateTime`執行會強加這些界限, 讓您更輕鬆地使用類別。

`COleDateTime`不支援 Julian 日期。 會假設西曆以100年1月1日的時間延長。

`COleDateTime`忽略日光節約時間 (DST)。 下列程式碼範例會比較兩個方法來計算跨越 DST 切換日期的時間範圍: 一個使用 CRT, 另一個使用`COleDateTime`。

第一個方法會使用`CTime`標準 C 類型結構 `tm`和`time_t`, 分別將兩個物件 ( *time1*和 time2) 設定為4月5日到4月6。 程式碼會顯示*time1*和*time2* , 以及它們之間的時間範圍。

第二個方法會`COleDateTime`建立兩`oletime1`個`oletime2`物件 (和), 並將其設定為與*time1*和*time2*相同的日期。 它會`oletime1`顯示`oletime2`和, 以及它們之間的時間範圍。

CRT 會正確計算23小時的差異。 `COleDateTimeSpan`計算24小時的差異。

[!code-cpp[NVC_ATLMFC_Utilities#176](../atl-mfc-shared/codesnippet/cpp/date-and-time-automation-support_1.cpp)]

### <a name="get-the-current-time"></a>取得目前時間

下列程式說明如何建立`COleDateTime`物件, 並使用目前的時間將它初始化。

#### <a name="to-get-the-current-time"></a>取得目前的時間

1. 建立 `COleDateTime` 物件。

1. 呼叫 `GetCurrentTime`。

   [!code-cpp[NVC_ATLMFC_Utilities#177](../atl-mfc-shared/codesnippet/cpp/current-time-automation-classes_1.cpp)]

### <a name="calculate-elapsed-time"></a>計算經過時間

此程式說明如何計算兩個`COleDateTime`物件之間的差異並`COleDateTimeSpan`取得結果。

#### <a name="to-calculate-elapsed-time"></a>計算經過時間

1. 建立兩`COleDateTime`個物件。

1. 將其中一個`COleDateTime`物件設定為目前的時間。

1. 執行一些耗時的工作。

1. 將其他`COleDateTime`物件設定為目前的時間。

1. 取兩次的差異。

   [!code-cpp[NVC_ATLMFC_Utilities#178](../atl-mfc-shared/codesnippet/cpp/elapsed-time-automation-classes_1.cpp)]

### <a name="format-a-time"></a>格式化時間

#### <a name="to-format-a-time"></a>格式化時間

您可以`Format`使用[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)或[COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md)的成員函式, 建立代表時間或經過時間的字元字串。

   [!code-cpp[NVC_ATLMFC_Utilities#179](../atl-mfc-shared/codesnippet/cpp/formatting-time-automation-classes_1.cpp)]

如需詳細資訊, 請參閱類別[COleVariant](../mfc/reference/colevariant-class.md)。

## <a name="date-and-time-database-support"></a>日期和時間:資料庫支援

從4.0 版開始, MFC 資料庫程式設計會使用[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)和[COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md)類別來代表日期和時間資料。 這些類別也用於自動化, 衍生自類別[COleVariant](../mfc/reference/colevariant-class.md)。 其提供比執行[CTime](../atl-mfc-shared/reference/ctime-class.md)和[CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md)更好的日期和時間資料管理支援。

## <a name="date-and-time-systemtime-support"></a>日期和時間:SYSTEMTIME 支援

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)類別具有可接受 Win32 系統和檔案時間的函式。

Win32 `FILETIME`結構以64位值表示時間。 對於內部儲存而言, 這是比`SYSTEMTIME`結構更方便的格式, 而 Win32 用來代表檔案建立時間的格式。 如需 SYSTEMTIME 結構的詳細資訊, 請參閱[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)。 如需 FILETIME 結構的詳細資訊, 請參閱[filetime](/windows/desktop/api/minwinbase/ns-minwinbase-filetime)。

## <a name="see-also"></a>另請參閱

[概念](../mfc/mfc-concepts.md)\
[一般 MFC 主題](../mfc/general-mfc-topics.md)
