---
title: "&lt;future&gt; 列舉 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c675645-db47-4cab-bc0e-7b87f8a302df
caps.latest.revision: 11
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: b1f8c56de97789bea4f0923cd87e8144382e1ed0
ms.lasthandoff: 02/24/2017

---
# <a name="ltfuturegt-enums"></a>&lt;future&gt; 列舉
||||  
|-|-|-|  
|[future_errc 列舉](#future_errc_enumeration)|[future_status 列舉](#future_status_enumeration)|[launch 列舉](#launch_enumeration)|  
  
##  <a name="a-namefutureerrcenumerationa--futureerrc-enumeration"></a><a name="future_errc_enumeration"></a>  future_errc 列舉  
 為 [future_error](../standard-library/future-error-class.md) 類別所回報的所有錯誤提供符號名稱。  
  
class future_errc { broken_promise, future_already_retrieved, promise_already_satisfied, no_state };  
  
##  <a name="a-namefuturestatusenumerationa--futurestatus-enumeration"></a><a name="future_status_enumeration"></a>  future_status 列舉  
 為計時的 wait 函式可傳回的原因提供符號名稱。  
  
```
enum future_status{    ready,
    timeout,
 deferred};
```  
  
##  <a name="a-namelaunchenumerationa--launch-enumeration"></a><a name="launch_enumeration"></a>  launch 列舉  
 代表一種位元遮罩類型，描述範本函式 [async](../standard-library/future-functions.md#async_function) 可能的模式。  
  
class launch{ async, deferred };  
  
## <a name="see-also"></a>另請參閱  
 [\<future>](../standard-library/future.md)




