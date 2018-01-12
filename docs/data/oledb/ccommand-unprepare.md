---
title: "Ccommand:: Unprepare |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Unprepare
- CCommand.Unprepare
- CCommand::Unprepare
dev_langs: C++
helpviewer_keywords: Unprepare method
ms.assetid: 4fe59988-fe51-4c7c-a156-72b68e3d642b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 19622da4735d4dba86079c9009ddc52ffabd1e9d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ccommandunprepare"></a>CCommand::Unprepare
捨棄目前的命令執行計畫。  
  
## <a name="syntax"></a>語法  
  
```  
  
HRESULT CCommandBase::Unprepare( ) throw( );  
  
```  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 這個方法會包裝 OLE DB 方法[icommandprepare:: Unprepare](https://msdn.microsoft.com/en-us/library/ms719635.aspx)。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CCommand 類別](../../data/oledb/ccommand-class.md)