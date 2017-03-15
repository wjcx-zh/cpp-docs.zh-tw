---
title: "LINGER 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LINGER
dev_langs:
- C++
helpviewer_keywords:
- LINGER structure
ms.assetid: 1fb1c5bf-a64e-4a6c-89d6-1734e4fdbb1b
caps.latest.revision: 11
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
ms.openlocfilehash: ed880c29f43c074ba61f52b11f812a79eece0416
ms.lasthandoff: 02/24/2017

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
 設定**SO_DONTLINGER**選項可防止封鎖成員函式**關閉**等候傳送未傳送的資料。 設定這個選項相當於設定**SO_LINGER**與**l_onoff**設為 0。  
  
## <a name="requirements"></a>需求  
 **標頭︰** winsock2.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CAsyncSocket::GetSockOpt](../../mfc/reference/casyncsocket-class.md#getsockopt)   
 [CAsyncSocket::SetSockOpt](../../mfc/reference/casyncsocket-class.md#setsockopt)


