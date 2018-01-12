---
title: "Ccommand:: Getparameterinfo |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GetParameterInfo
- CCommand.GetParameterInfo
- CCommand::GetParameterInfo
dev_langs: C++
helpviewer_keywords: GetParameterInfo method
ms.assetid: 9cd9277f-0161-4bd8-ad24-58e5e90b92a7
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c89b91ccd5dd7b0c9f6ed9235024cd446370c897
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ccommandgetparameterinfo"></a>CCommand::GetParameterInfo
取得命令的參數，其名稱，以及它們的型別清單。  
  
## <a name="syntax"></a>語法  
  
```  
  
      HRESULT CCommandBase::GetParameterInfo(  
   DB_UPARAMS* pParams,  
   DBPARAMINFO** ppParamInfo,  
   OLECHAR** ppNamesBuffer   
) throw ( );  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[icommandwithparameters:: Getparameterinfo](https://msdn.microsoft.com/en-us/library/ms714917.aspx)中*OLE DB 程式設計人員參考*。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CCommand 類別](../../data/oledb/ccommand-class.md)