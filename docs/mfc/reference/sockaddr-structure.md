---
title: "SOCKADDR 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SOCKADDR
dev_langs:
- C++
helpviewer_keywords:
- SOCKADDR structure
ms.assetid: df1ed66a-f4b8-43f8-8db8-8c2533d25f68
caps.latest.revision: 12
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
ms.openlocfilehash: 28984fcc5614a5f901a01ffdeff4ea5f360f63fc
ms.lasthandoff: 02/24/2017

---
# <a name="sockaddr-structure"></a>SOCKADDR 結構
`SOCKADDR` 結構是用來儲存參與 Windows Sockets 通訊的電腦之網際網路通訊協定 (IP) 位址。  
  
## <a name="syntax"></a>語法  
  
```  
struct sockaddr {  
    unsigned short sa_family;  
    char sa_data[14];  
};  
```  
  
#### <a name="parameters"></a>參數  
 *sa_family*  
 通訊端位址系列。  
  
 *sa_data*  
 所有不同通訊端位址結構的最大大小。  
  
## <a name="remarks"></a>備註  
 Microsoft TCP/IP 通訊端開發人員套件只支援網際網路位址網域。 若要實際填入地址的每個部分的值，請使用 `SOCKADDR_IN` 資料結構，這是特別用於這個位址格式。 `SOCKADDR` 和 `SOCKADDR_IN` 資料結構有相同的大小。 只要轉型，即可在這兩個結構類型之間切換。  
  
## <a name="requirements"></a>需求  
 **標頭︰** winsock2.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [SOCKADDR_IN 結構](../../mfc/reference/sockaddr-in-structure.md)   
 [CAsyncSocket::Create](../../mfc/reference/casyncsocket-class.md#create)   
 [CSocket::Create](../../mfc/reference/csocket-class.md#create)


