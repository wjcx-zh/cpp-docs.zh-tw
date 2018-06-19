---
title: 'Ccommand:: Unprepare |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- Unprepare
- CCommand.Unprepare
- CCommand::Unprepare
dev_langs:
- C++
helpviewer_keywords:
- Unprepare method
ms.assetid: 4fe59988-fe51-4c7c-a156-72b68e3d642b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ab5fdd595e646e181aa3815d6385595f3fee21a8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094354"
---
# <a name="ccommandunprepare"></a>CCommand::Unprepare
捨棄目前的命令執行計畫。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT CCommandBase::Unprepare() throw();  
  
```  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 這個方法會包裝 OLE DB 方法[icommandprepare:: Unprepare](https://msdn.microsoft.com/en-us/library/ms719635.aspx)。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CCommand 類別](../../data/oledb/ccommand-class.md)