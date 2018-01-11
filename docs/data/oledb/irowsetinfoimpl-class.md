---
title: "IRowsetInfoImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.IRowsetInfoImpl
- IRowsetInfoImpl
- ATL::IRowsetInfoImpl
dev_langs: C++
helpviewer_keywords: IRowsetInfoImpl class
ms.assetid: 9c654155-7727-464e-bd31-143e68391a47
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cba03cfdda0b7a55c8f4719d5340566ee5dc6050
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="irowsetinfoimpl-class"></a>IRowsetInfoImpl 類別
提供的實作[IRowsetInfo](https://msdn.microsoft.com/en-us/library/ms724541.aspx)介面。  
  
## <a name="syntax"></a>語法  
  
```  
template <class T, class PropClass = T>  
class ATL_NO_VTABLE IRowsetInfoImpl :   
   public IRowsetInfo,    
   public CUtlProps<PropClass>  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`IRowsetInfoImpl`。  
  
 `PropClass`  
 預設為使用者定義的屬性類別`T`。  
  
## <a name="members"></a>成員  
  
### <a name="interface-methods"></a>介面方法  
  
|||  
|-|-|  
|[GetProperties](../../data/oledb/irowsetinfoimpl-getproperties.md)|傳回資料列集所支援的所有屬性的目前的設定。|  
|[GetReferencedRowset](../../data/oledb/irowsetinfoimpl-getreferencedrowset.md)|傳回資料列集的書籤所套用的介面指標。|  
|[GetSpecification](../../data/oledb/irowsetinfoimpl-getspecification.md)|傳回介面指標上建立此資料列集的物件 （命令或工作階段）。|  
  
## <a name="remarks"></a>備註  
 資料列集上的強制介面。 這個類別會實作資料列集屬性使用[屬性集對應](../../data/oledb/begin-propset-map.md)命令類別中定義。 雖然資料列集類別使用的命令類別屬性設定，資料列集都會有它自己的複本，在執行階段內容的命令或工作階段物件建立時。  
  
## <a name="requirements"></a>需求  
 **標頭：** altdb.h  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)