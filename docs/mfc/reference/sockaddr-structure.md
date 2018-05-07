---
title: SOCKADDR 結構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- SOCKADDR
dev_langs:
- C++
helpviewer_keywords:
- SOCKADDR structure [MFC]
ms.assetid: df1ed66a-f4b8-43f8-8db8-8c2533d25f68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f468a0a68dcfedab3b92deea492b48f7876c1610
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
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
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [SOCKADDR_IN 結構](../../mfc/reference/sockaddr-in-structure.md)   
 [CAsyncSocket::Create](../../mfc/reference/casyncsocket-class.md#create)   
 [CSocket::Create](../../mfc/reference/csocket-class.md#create)

