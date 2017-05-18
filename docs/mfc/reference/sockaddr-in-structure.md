---
title: "SOCKADDR_IN 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SOCKADDR_IN
dev_langs:
- C++
helpviewer_keywords:
- SOCKADDR_IN structure
ms.assetid: e8cd7c34-78bd-4e28-a990-eb3ca070b7a6
caps.latest.revision: 13
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: a1283740c0abb0538e5912efa11500c46b45bb9f
ms.contentlocale: zh-tw
ms.lasthandoff: 04/04/2017

---
# <a name="sockaddrin-structure"></a>SOCKADDR_IN 結構
在網際網路位址系列產品中`SOCKADDR_IN`結構可由 Windows 通訊端來指定連接通訊端的本機或遠端的端點位址。  
  
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
 位址家族 (必須是**AF_INET**)。  
  
 *sin_port*  
 IP 通訊埠。  
  
 *sin_addr*  
 IP 位址。  
  
 *sin_zero*  
 將結構做為相同的調整大小的填補`SOCKADDR`。  
  
## <a name="remarks"></a>備註  
 這是的形式`SOCKADDR`結構特有的網際網路位址系列，而且可以轉換成`SOCKADDR`。  
  
 此結構的 IP 位址元件屬於型別**IN_ADDR**。 **IN_ADDR** Windows Sockets 標頭檔 WINSOCK 中所定義的結構。H，如下所示︰  
  
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
 **標頭︰** winsock2.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [SOCKADDR 結構](../../mfc/reference/sockaddr-structure.md)

