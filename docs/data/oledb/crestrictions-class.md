---
title: "CRestrictions 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CRestrictions
- CRestrictions
- ATL.CRestrictions
dev_langs: C++
helpviewer_keywords: CRestrictions class
ms.assetid: 0aaa2364-641c-4318-b110-7446aada4b4f
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 23b01a776a624f0fa463c7071e164b70111b2e8b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="crestrictions-class"></a>CRestrictions 類別
泛型類別，可讓您指定的結構描述資料列限制。  
  
## <a name="syntax"></a>語法  
  
```  
template <   
   class T,   
   short nRestrictions,   
   const GUID* pguid   
>  
class CRestrictions : public CSchemaRowset <   
   T,   
   nRestrictions   
>  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 用來存取子類別。  
  
 `nRestrictions`  
 限制資料行的結構描述資料列集數目。  
  
 `pguid`  
 結構描述的 GUID 指標。  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[開啟](../../data/oledb/crestrictions-open.md)|傳回的結果集根據使用者所提供的限制。|  
  
## <a name="requirements"></a>需求  
 **標頭：** atldbsch.h  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)