---
title: "SYSTEMTIME 結構&1; |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SYSTEMTIME
dev_langs:
- C++
helpviewer_keywords:
- SYSTEMTIME structure
ms.assetid: 9aaef4d6-de79-4fa1-8158-86b245ef5bff
caps.latest.revision: 15
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 298b2673a3eb05525683f8269fcd415d5be1c80a
ms.lasthandoff: 02/24/2017

---
# <a name="systemtime-structure1"></a>SYSTEMTIME 結構&1;
`SYSTEMTIME`結構表示的日期和時間使用月、 日、 年、 工作日、 小時、 分鐘、 秒和毫秒的個別成員。  
  
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
 目前的月份。一月是 1。  
  
 *wDayOfWeek*  
 目前日期的星期幾;星期日是 0，星期一是 1，依此類推。  
  
 *wDay*  
 目前的月份日期。  
  
 *wHour*  
 目前的小時。  
  
 *wMinute*  
 目前的分鐘。  
  
 *wSecond*  
 目前的秒數。  
  
 *wMilliseconds*  
 目前的毫秒數。  
  
## <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities #&39;](../../mfc/codesnippet/cpp/systemtime-structure1_1.cpp)]  
  
## <a name="requirements"></a>需求  
 **標頭︰** winbase.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CTime::CTime](../../atl-mfc-shared/reference/ctime-class.md#ctime)


