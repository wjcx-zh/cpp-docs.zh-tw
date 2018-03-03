---
title: "FILETIME 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- FILETIME
dev_langs:
- C++
helpviewer_keywords:
- FILETIME structure [MFC]
ms.assetid: e09557e2-b6d7-4dd5-a5b9-6328bca88595
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f23f9d4a508158b392de6eb5c872f0b5762e1ae3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="filetime-structure"></a>FILETIME 結構
`FILETIME`結構是 64 位元值的 100 奈秒間隔數表示自 1601 年 1 月 1 日。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct _FILETIME {  
    DWORD dwLowDateTime;   /* low 32 bits */  
    DWORD dwHighDateTime;  /* high 32 bits */  
} FILETIME, *PFILETIME, *LPFILETIME;  
```  
  
#### <a name="parameters"></a>參數  
 *dwLowDateTime*  
 指定的低 32 位元檔案的時間。  
  
 *dwHighDateTime*  
 指定的高 32 位元檔案的時間。  
  
## <a name="requirements"></a>需求  
 **標頭：** windef.h  
  
## <a name="see-also"></a>請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CTime::CTime](../../atl-mfc-shared/reference/ctime-class.md#ctime)

