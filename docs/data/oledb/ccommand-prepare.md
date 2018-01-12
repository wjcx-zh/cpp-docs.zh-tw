---
title: "Ccommand:: Prepare |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CCommand.Prepare
- CCommand::Prepare
- Prepare
dev_langs: C++
helpviewer_keywords: Prepare method
ms.assetid: f0e473fc-2f7a-4d29-96c2-1328dc21e702
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 68bce43b0b3fe1799cbbc51841fc1232c5527700
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ccommandprepare"></a>CCommand::Prepare
驗證並最佳化目前的命令。  
  
## <a name="syntax"></a>語法  
  
```  
  
      HRESULT CCommandBase::Prepare(  
   ULONG cExpectedRuns = 0   
) throw( );  
```  
  
#### <a name="parameters"></a>參數  
 *cExpectedRuns*  
 [in]您要執行命令的次數。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 這個方法會包裝 OLE DB 方法[icommandprepare:: Prepare](https://msdn.microsoft.com/en-us/library/ms718370.aspx)。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CCommand 類別](../../data/oledb/ccommand-class.md)