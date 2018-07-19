---
title: SOCKADDR_IN 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- SOCKADDR_IN
dev_langs:
- C++
helpviewer_keywords:
- SOCKADDR_IN structure [MFC]
ms.assetid: e8cd7c34-78bd-4e28-a990-eb3ca070b7a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5e5ec6ebf4329ff03c75240dc7cec93e9ba46331
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37885734"
---
# <a name="sockaddrin-structure"></a>SOCKADDR_IN 結構
在網際網路位址家族，`SOCKADDR_IN`結構由 Windows 通訊端用來指定要連接的通訊端的本機或遠端端點位址。  
  
## <a name="syntax"></a>語法  
  
```  
struct sockaddr_in{  
    short sin_family;  
    unsigned short sin_port;  
struct in_addr sin_addr;  
    char sin_zero[8];  
};  
```  
  
#### <a name="parameters"></a>參數  
 *sin_family*  
 通訊協定家族 （必須是 AF_INET）。  
  
 *sin_port*  
 IP 通訊埠。  
  
 *sin_addr*  
 IP 位址。  
  
 *sin_zero*  
 讓結構大小相同的填補`SOCKADDR`。  
  
## <a name="remarks"></a>備註  
 這是種`SOCKADDR`結構特有的網際網路位址家族，並可以轉換成`SOCKADDR`。  
  
 此結構的 IP 位址元件是型別的`IN_ADDR`。 `IN_ADDR` Windows Sockets 標頭檔 WINSOCK 來定義結構。H，如下所示：  
  
```  
struct in_addr {
    union {
        struct {  
            unsigned char s_b1, s_b2, s_b3, s_b4;  
        } S_un_b;  
        struct {  
            unsigned short s_w1, s_w2;
        } S_un_w;
        unsigned long S_addr;
    } S_un;  
};  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** winsock2.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [SOCKADDR 結構](../../mfc/reference/sockaddr-structure.md)
