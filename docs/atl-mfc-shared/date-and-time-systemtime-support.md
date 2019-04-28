---
title: 日期和時間：SYSTEMTIME 支援
ms.date: 11/04/2016
f1_keywords:
- SYSTEMTIME
helpviewer_keywords:
- system time
- FILETIME structure, with CTime class
- time [C++], formatting
- SYSTEMTIME structure
- dates [C++], MFC
- formatting [C++], time
ms.assetid: 201528e4-2ffa-48fc-af8f-203aa86d942a
ms.openlocfilehash: be8462858585a5530f360dae97e155b4967239b0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62236407"
---
# <a name="date-and-time-systemtime-support"></a>日期和時間：SYSTEMTIME 支援

[CTime](../atl-mfc-shared/reference/ctime-class.md)類別具有建構函式會接受來自 Win32 的系統及檔案時間。 如果您使用 `CTime` 物件來進行這些目的，則必須相應地修改其初始化，如本文章所述。

SYSTEMTIME 結構的詳細資訊，請參閱[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)。 FILETIME 結構的詳細資訊，請參閱[FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime)。

MFC 仍然提供 `CTime` 建構函式，它們接受 MS-DOS 樣式的時間引數，但從 MFC 3.0 版開始，`CTime` 類別也支援接受 Win32 `SYSTEMTIME` 結構的建構函式，以及另一個接受 Win32 `FILETIME` 結構的建構函式。

新的 `CTime` 建構函式包括：

- CTime(const SYSTEMTIME& `sysTime`);

- CTime (const FILETIME&AMP; & `fileTime`);

*FileTime*參數是 Win32 的參考`FILETIME`結構，用來表示時間為 64 位元值時，更方便的格式進行內部儲存比`SYSTEMTIME`結構和 Win32 來所使用的格式代表檔案建立時間。

如果您的程式碼包含以系統時間初始化的 `CTime` 物件，則您應該使用 Win32 中的 `SYSTEMTIME` 建構函式。

您很可能不會使用`CTime``FILETIME`直接初始化。 如果您使用`CFile`物件來管理檔案， [Cfile](../mfc/reference/cfile-class.md#getstatus)讓您透過擷取檔案時間戳記`CTime`物件初始化`FILETIME`結構。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [一般日期與時間程式設計，在 MFC 中](../atl-mfc-shared/date-and-time.md)

- [日期與時間程式設計的自動化支援](../atl-mfc-shared/date-and-time-automation-support.md)

## <a name="see-also"></a>另請參閱

[日期和時間](../atl-mfc-shared/date-and-time.md)
