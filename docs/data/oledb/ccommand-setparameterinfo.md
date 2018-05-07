---
title: 'Ccommand:: Setparameterinfo |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- SetParameterInfo
- CCommand.SetParameterInfo
- CCommand::SetParameterInfo
dev_langs:
- C++
helpviewer_keywords:
- SetParameterInfo method
ms.assetid: a70e92f4-1e73-41d7-a5b7-c6ebb45a6477
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a1bcbc30564b248991859ca2b1911e7b8a67dbe2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ccommandsetparameterinfo"></a>CCommand::SetParameterInfo
指定每一個命令參數的原生類型。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT CCommandBase::SetParameterInfo(DB_UPARAMS ulParams,  
   const DBORDINAL* pOrdinals,  
   const DBPARAMBINDINFO* pParamInfo) throw();  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[icommandwithparameters:: Setparameterinfo](https://msdn.microsoft.com/en-us/library/ms725393.aspx)中*OLE DB 程式設計人員參考*。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CCommand 類別](../../data/oledb/ccommand-class.md)