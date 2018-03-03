---
title: "SOCKADDR 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SOCKADDR
dev_langs:
- C++
helpviewer_keywords:
- SOCKADDR structure [MFC]
ms.assetid: df1ed66a-f4b8-43f8-8db8-8c2533d25f68
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 55b310ec83aae35c7386d61849663752811651d4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
 **標頭：** winsock2.h  
  
## <a name="see-also"></a>請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [SOCKADDR_IN 結構](../../mfc/reference/sockaddr-in-structure.md)   
 [CAsyncSocket::Create](../../mfc/reference/casyncsocket-class.md#create)   
 [CSocket::Create](../../mfc/reference/csocket-class.md#create)

