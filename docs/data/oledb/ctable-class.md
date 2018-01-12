---
title: "CTable 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CTable
- ATL.CTable
- CTable
dev_langs: C++
helpviewer_keywords: CTable class
ms.assetid: f13fdaa3-e198-4557-977d-54b0bbc3454d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 14d127804c1fb9a58b0408f080f7b029e56227d8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ctable-class"></a>CTable 類別
提供方法來直接存取簡單資料列集 （不含任何參數）。  
  
## <a name="syntax"></a>語法  
  
```  
template <   
   class TAccessor = CNoAccessor,    
   template <typename T> class TRowset = CRowset    
>  
class CTable :    
   public CAccessorRowset <   
      TAccessor,    
      TRowset    
   >  
```  
  
#### <a name="parameters"></a>參數  
 `TAccessor`  
 存取子類別。  
  
 `TRowset`  
 資料列集類別。  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[開啟](../../data/oledb/ctable-open.md)|開啟資料表。|  
  
## <a name="remarks"></a>備註  
 請參閱[CCommand](../../data/oledb/ccommand-class.md)如需有關如何執行命令，以存取資料列集資訊。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [Iopenrowset:: Openrowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx)