---
title: '&lt;new&gt; typedef | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
caps.latest.revision: 7
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: b652d0a1eac1615d1e1b0aed1df05d6a9ee661a3
ms.lasthandoff: 02/24/2017

---
# <a name="ltnewgt-typedefs"></a>&lt;new&gt; typedef
||  
|-|  
|[new_handler](#new_handler)|  
  
##  <a name="new_handler"></a>  new_handler  
 此類型會指向適合用來作為新處理常式的函式。  
  
```
typedef void (*new_handler)();
```  
  
### <a name="remarks"></a>備註  
 當 **operatornew** 或 `operator new[]` 無法滿足提供額外儲存體的要求時，便會呼叫此類型的處理常式函式。  
  
### <a name="example"></a>範例  
  如需使用 `new_handler` 作為傳回值的範例，請參閱 [set_new_handler](../standard-library/new-functions.md#set_new_handler)。  
  
## <a name="see-also"></a>另請參閱  
 [\<new>](../standard-library/new.md)




