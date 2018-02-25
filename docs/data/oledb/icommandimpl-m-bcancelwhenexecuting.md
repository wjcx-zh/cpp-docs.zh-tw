---
title: "Icommandimpl:: M_bcancelwhenexecuting |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ICommandImpl::m_bCancelWhenExecuting
- ICommandImpl.m_bCancelWhenExecuting
- ATL::ICommandImpl::m_bCancelWhenExecuting
- m_bCancelWhenExecuting
- ATL.ICommandImpl.m_bCancelWhenExecuting
dev_langs:
- C++
helpviewer_keywords:
- m_bCancelWhenExecuting
ms.assetid: d7d33e4c-a862-4e6d-a9a1-4400bfe45b88
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0f0e5d3708cbcba01630f1096bc31197c82fdb8f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="icommandimplmbcancelwhenexecuting"></a>ICommandImpl::m_bCancelWhenExecuting
指出執行時，是否可以取消命令。  
  
## <a name="syntax"></a>語法  
  
```cpp
unsigned m_bCancelWhenExecuting:1;  
  
```  
  
## <a name="remarks"></a>備註  
 預設為**true** （您可以取消）。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [ICommandImpl 類別](../../data/oledb/icommandimpl-class.md)   
 [ICommandImpl::m_bCancel](../../data/oledb/icommandimpl-m-bcancel.md)