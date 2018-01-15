---
title: "緩衝區溢位 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- buffers [C++], character sizes
- buffer overflows [C++]
- MBCS [C++], buffer overflow
ms.assetid: f2b7e40a-f02b-46d8-a449-51d26fc0c663
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4bfad181ee7c6b702af87bc8ff0a49ccfb42cb65
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="buffer-overflow"></a>緩衝區溢位
變動字元大小會造成問題，當您將字元放到緩衝區。 請考慮下列程式碼中的字串字元複製到， `sz`，緩衝區`rgch`:  
  
```  
cb = 0;  
while( cb < sizeof( rgch ) )  
    rgch[ cb++ ] = *sz++;  
```  
  
 問題是： 最後一個位元組複製前導位元？ 以下不能解決問題因為它會溢位緩衝區：  
  
```  
cb = 0;  
while( cb < sizeof( rgch ) )  
{  
    _mbccpy( rgch + cb, sz );  
    cb += _mbclen( sz );  
    sz = _mbsinc( sz );  
}  
```  
  
 `_mbccpy`呼叫會嘗試執行正確的動作，複製完整的字元，不論它是 1 或 2 個位元組。 但它不會考量複製的最後一個字元可能不符合緩衝區如果字元是 2 個位元組寬。 正確的解決方案是：  
  
```  
cb = 0;  
while( (cb + _mbclen( sz )) <= sizeof( rgch ) )  
{  
    _mbccpy( rgch + cb, sz );  
    cb += _mbclen( sz );  
    sz = _mbsinc( sz );  
}  
```  
  
 此程式碼測試可能會發生緩衝區溢位在迴圈中測試，請使用`_mbclen`來測試所指向的目前字元大小`sz`。 藉由呼叫`_mbsnbcpy`函式，您可以取代中的程式碼`while`迴圈使用一行程式碼。 例如:   
  
```  
_mbsnbcpy( rgch, sz, sizeof( rgch ) );  
```  
  
## <a name="see-also"></a>請參閱  
 [MBCS 程式設計提示](../text/mbcs-programming-tips.md)