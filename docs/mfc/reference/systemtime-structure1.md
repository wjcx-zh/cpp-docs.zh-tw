---
title: SYSTEMTIME 結構 1 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- SYSTEMTIME
dev_langs:
- C++
helpviewer_keywords:
- SYSTEMTIME structure [MFC]
ms.assetid: 9aaef4d6-de79-4fa1-8158-86b245ef5bff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 97a0042adaa223fc5898c057f191f7b750fa230f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372388"
---
# <a name="systemtime-structure1"></a>SYSTEMTIME 結構 1
`SYSTEMTIME`結構代表日期和時間使用個別的成員，如月、 日、 年、 週間日、 小時、 分鐘、 秒和毫秒。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct _SYSTEMTIME {  
    WORD wYear;  
    WORD wMonth;  
    WORD wDayOfWeek;  
    WORD wDay;  
    WORD wHour;  
    WORD wMinute;  
    WORD wSecond;  
    WORD wMilliseconds;  
} SYSTEMTIME;  
```  
  
#### <a name="parameters"></a>參數  
 *wYear*  
 目前的年份。  
  
 *wMonth*  
 目前的月份。年 1 月為 1。  
  
 *wDayOfWeek*  
 目前日期的星期幾。星期日是 0，星期一為 1，依此類推。  
  
 *wDay*  
 目前的月份天數。  
  
 *wHour*  
 目前的小時。  
  
 *wMinute*  
 目前的分鐘。  
  
 *wSecond*  
 目前的秒數。  
  
 *wMilliseconds*  
 目前的毫秒。  
  
## <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities#39](../../mfc/codesnippet/cpp/systemtime-structure1_1.cpp)]  
  
## <a name="requirements"></a>需求  
 **標頭：** winbase.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CTime::CTime](../../atl-mfc-shared/reference/ctime-class.md#ctime)

