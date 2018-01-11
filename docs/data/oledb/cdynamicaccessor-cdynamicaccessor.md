---
title: "Cdynamicaccessor:: Cdynamicaccessor |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDynamicAccessor::CDynamicAccessor
- ATL::CDynamicAccessor::CDynamicAccessor
- ATL.CDynamicAccessor.CDynamicAccessor
- CDynamicAccessor.CDynamicAccessor
dev_langs: C++
helpviewer_keywords: CDynamicAccessor class, constructor
ms.assetid: bf40fe81-2c85-473e-9075-51ad9b060b39
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3f063652b95cc5e778d7e1ffcbc809b9425f5425
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cdynamicaccessorcdynamicaccessor"></a>CDynamicAccessor::CDynamicAccessor
執行個體化並初始化`CDynamicAccessor`物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
      CDynamicAccessor(   
   DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,   
   DBLENGTH nBlobSize = 8000   
);  
```  
  
#### <a name="parameters"></a>參數  
 `eBlobHandling`  
 指定要處理的二進位大型物件 (BLOB) 資料的方式。 預設值是**DBBLOBHANDLING_DEFAULT**。 請參閱[SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md)的說明**cdynamicaccessor:: SETBLOBHANDLING**值。  
  
 `nBlobSize`  
 最大 BLOB 的大小 (以位元組為單位)；此值的資料行資料被視為 BLOB。 預設值為 8000。 請參閱[SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md)如需詳細資訊。  
  
## <a name="remarks"></a>備註  
 如果您使用建構函式來初始化`CDynamicAccessor`物件，您可以指定如何將繫結它的 Blob。 Blob 可包含二進位資料，例如圖形、 聲音，或編譯程式碼。 預設行為是視為資料行超過 8,000 個位元組的 Blob，並嘗試進行繫結`ISequentialStream`物件。 不過，您可以指定 BLOB 的大小不同的值。  
  
 您也可以指定如何`CDynamicAccessor`處理可作為 BLOB 資料的資料行資料： 它可以處理的預設處理方式中的 BLOB 資料，則可以略過 （不是繫結） 提供者配置的記憶體中 BLOB 資料，也可以繫結 BLOB 資料。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)