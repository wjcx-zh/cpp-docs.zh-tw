---
title: "LINGER 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LINGER
dev_langs:
- C++
helpviewer_keywords:
- LINGER structure [MFC]
ms.assetid: 1fb1c5bf-a64e-4a6c-89d6-1734e4fdbb1b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 747a793e64e7f3ec1e76f383a807f15c67417a83
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linger-structure"></a>LINGER 結構
`LINGER`結構用於操作**SO_LINGER**和**SO_DONTLINGER**選項`CAsyncSocket::GetSockOpt`。  
  
## <a name="syntax"></a>語法  
  
```  
struct linger {  
    u_short l_onoff;            // option on/off  
    u_short l_linger;           // linger time  
};  
```  
  
## <a name="remarks"></a>備註  
 設定**SO_DONTLINGER**選項可防止封鎖成員函式**關閉**等候要傳送的未傳送資料。 設定此選項相當於設定**SO_LINGER**與**l_onoff**設為 0。  
  
## <a name="requirements"></a>需求  
 **標頭：** winsock2.h  
  
## <a name="see-also"></a>請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CAsyncSocket::GetSockOpt](../../mfc/reference/casyncsocket-class.md#getsockopt)   
 [CAsyncSocket::SetSockOpt](../../mfc/reference/casyncsocket-class.md#setsockopt)

