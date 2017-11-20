---
title: "日期和時間： SYSTEMTIME 支援 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: SYSTEMTIME
dev_langs: C++
helpviewer_keywords:
- system time
- FILETIME structure, with CTime class
- time [C++], formatting
- SYSTEMTIME structure
- dates [C++], MFC
- formatting [C++], time
ms.assetid: 201528e4-2ffa-48fc-af8f-203aa86d942a
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e656bac248ac95bb1f4d9501070fd0f5778d4753
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="date-and-time-systemtime-support"></a>日期和時間： SYSTEMTIME 支援
[CTime](../atl-mfc-shared/reference/ctime-class.md)類別具有建構函式會接受從 Win32 系統及檔案時間。 如果您使用 `CTime` 物件來進行這些目的，則必須相應地修改其初始化，如本文章所述。  
  
 SYSTEMTIME 結構的詳細資訊，請參閱[SYSTEMTIME](../mfc/reference/systemtime-structure1.md)。 FILETIME 結構的詳細資訊，請參閱[FILETIME](../mfc/reference/filetime-structure.md)。  
  
 MFC 仍然提供 `CTime` 建構函式，它們接受 MS-DOS 樣式的時間引數，但從 MFC 3.0 版開始，`CTime` 類別也支援接受 Win32 `SYSTEMTIME` 結構的建構函式，以及另一個接受 Win32 `FILETIME` 結構的建構函式。  
  
 新的 `CTime` 建構函式包括：  
  
-   CTime (const SYSTEMTIME&AMP; & `sysTime`);  
  
-   CTime (const FILETIME&AMP; & `fileTime`);  
  
 `fileTime` 參數是對 Win32 `FILETIME` 結構的參考，後者以 64 位元的值來代表時間，這種格式比 `SYSTEMTIME` 結構更方便用於內部儲存，也是 Win32 用來代表檔案建立時間的格式。  
  
 如果您的程式碼包含以系統時間初始化的 `CTime` 物件，則您應該使用 Win32 中的 `SYSTEMTIME` 建構函式。  
  
 您很可能不會使用`CTime``FILETIME`直接初始化。 如果您使用`CFile`物件來操作檔案、 [Getstatus](../mfc/reference/cfile-class.md#getstatus)透過擷取檔案時間戳記`CTime`物件使用初始化`FILETIME`結構。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [一般日期與時間程式設計，在 MFC 中](../atl-mfc-shared/date-and-time.md)  
  
-   [日期與時間程式設計的自動化支援](../atl-mfc-shared/date-and-time-automation-support.md)  
  
-   [日期與時間程式設計的一般用途類別](../atl-mfc-shared/date-and-time-general-purpose-classes.md)  
  
## <a name="see-also"></a>另請參閱  
 [日期和時間](../atl-mfc-shared/date-and-time.md)

