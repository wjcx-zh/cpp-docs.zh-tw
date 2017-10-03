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
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: e23ea06002dc840997a0e7202f581cd81ef407c5
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

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




