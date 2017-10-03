---
title: "&lt;forward_list&gt; 函式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- forward_list/std::swap
ms.assetid: 0d6bc656-7049-4651-a4bd-c9a805e47756
caps.latest.revision: 11
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 6696f42d2ba7cb6daabb8f2ff38093911838c1ca
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="ltforwardlistgt-functions"></a>&lt;forward_list&gt; 函式
||  
|-|  
|[swap](#swap)|  
  
##  <a name="swap"></a>  swap  
 交換兩個轉送清單的項目。  
  
```
void swap(
    forward_list <Type, Allocator>& left,
    forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`left`|`forward_list` 類型的物件。|  
|`right`|`forward_list` 類型的物件。|  
  
### <a name="remarks"></a>備註  
 此範本函式會執行 `left.swap(right)`。  
  
## <a name="see-also"></a>另請參閱  
 [<forward_list>](../standard-library/forward-list.md)




