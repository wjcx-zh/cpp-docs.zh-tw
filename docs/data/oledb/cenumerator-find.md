---
title: "Cenumerator:: Find |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CEnumerator::Find
- ATL::CEnumerator::Find
- ATL.CEnumerator.Find
- CEnumerator.Find
dev_langs:
- C++
helpviewer_keywords:
- Find method
ms.assetid: 69a153af-d6c3-40fd-9018-27c7d2f344c6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 66298c4be2bb1e43aa37899fe652ccbf6694faae
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="cenumeratorfind"></a>CEnumerator::Find
在可用提供者中尋找指定的名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp
      bool Find(TCHAR* szSearchName) throw();  
```  
  
#### <a name="parameters"></a>參數  
 *szSearchName*  
 [in] 要搜尋的名稱。  
  
## <a name="return-value"></a>傳回值  
 **true**如果找不到名稱。 否則， **false**。  
  
## <a name="remarks"></a>備註  
 這個名稱會對應到**ISOURCESROWSET**隸屬[ISourcesRowset](https://msdn.microsoft.com/en-us/library/ms715969.aspx)介面。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CEnumerator 類別](../../data/oledb/cenumerator-class.md)