---
title: "Cdynamicaccessor:: Getblobsizelimit |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CDynamicAccessor::GetBlobSizeLimit
- CDynamicAccessor.GetBlobSizeLimit
- CDynamicAccessor::GetBlobSizeLimit
- GetBlobSizeLimit
- ATL.CDynamicAccessor.GetBlobSizeLimit
dev_langs: C++
helpviewer_keywords: GetBlobSizeLimit method
ms.assetid: 7131e7c4-6e05-42f3-9d87-110301b672f2
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3162ee335902b887facbc6e3aec33523622be5f5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cdynamicaccessorgetblobsizelimit"></a>CDynamicAccessor::GetBlobSizeLimit
擷取最大 BLOB 大小 （位元組）。  
  
## <a name="syntax"></a>語法  
  
```  
  
const DBLENGTH GetBlobSizeLimit( ) const;  
  
```  
  
## <a name="remarks"></a>備註  
 傳回處理值的 BLOB`nBlobSize`為設定由[SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md)。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)