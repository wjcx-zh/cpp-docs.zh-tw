---
title: "PROPERTY_INFO_ENTRY_VALUE |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PROPERTY_INFO_ENTRY_VALUE
dev_langs: C++
helpviewer_keywords: PROPERTY_INFO_ENTRY_VALUE macro
ms.assetid: 9690f7f3-fb20-4a7e-a75f-8a3a1cb1ce0d
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 25eb1627f4024fd18dbf0d22114c2e762ab8b897
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="propertyinfoentryvalue"></a>PROPERTY_INFO_ENTRY_VALUE
代表屬性集中的特定屬性。  
  
## <a name="syntax"></a>語法  
  
```  
  
PROPERTY_INFO_ENTRY_VALUE(  
dwPropID  
, value )  
```  
  
#### <a name="parameters"></a>參數  
 *dwPropID*  
 [in] [DBPROPID](https://msdn.microsoft.com/en-us/library/ms723882.aspx) 值，可搭配屬性集 GUID 以識別屬性。  
  
 *value*  
 [in] `DWORD`類型的屬性值。  
  
## <a name="remarks"></a>備註  
 使用這個巨集，您可以直接指定類型的屬性值`DWORD`。 若要設定為 ATLDB 中定義的預設值的屬性。H、 使用[PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md)。 若要設定的值、 旗標和屬性的選項，使用[PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md)。  
  
## <a name="example"></a>範例  
 請參閱 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 提供者樣板的巨集](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)   
 [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)