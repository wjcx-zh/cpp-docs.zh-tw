---
title: "&lt;future&gt; 列舉 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- future/std::future_errc
- future/std::future_status
- future/std::launch
ms.assetid: 8c675645-db47-4cab-bc0e-7b87f8a302df
caps.latest.revision: 
manager: ghogen
ms.openlocfilehash: eebca67270d208f1e8aa233ece80818bdc40f7f1
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="ltfuturegt-enums"></a>&lt;future&gt; 列舉
||||  
|-|-|-|  
|[future_errc](#future_errc)|[future_status](#future_status)|[launch](#launch)|  
  
##  <a name="future_errc"></a>  future_errc 列舉  
 為 [future_error](../standard-library/future-error-class.md) 類別所回報的所有錯誤提供符號名稱。  
  
class future_errc { broken_promise, future_already_retrieved, promise_already_satisfied, no_state };  
  
##  <a name="future_status"></a>  future_status 列舉  
 為計時的 wait 函式可傳回的原因提供符號名稱。  
  
```
enum future_status{    ready,
    timeout,
 deferred};
```  
  
##  <a name="launch"></a>  launch 列舉  
 代表一種位元遮罩類型，描述範本函式 [async](../standard-library/future-functions.md#async) 可能的模式。  
  
class launch{ async, deferred };  
  
## <a name="see-also"></a>請參閱  
 [\<future>](../standard-library/future.md)



