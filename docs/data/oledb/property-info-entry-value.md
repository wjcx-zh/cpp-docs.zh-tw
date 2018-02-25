---
title: PROPERTY_INFO_ENTRY_VALUE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- PROPERTY_INFO_ENTRY_VALUE
dev_langs:
- C++
helpviewer_keywords:
- PROPERTY_INFO_ENTRY_VALUE macro
ms.assetid: 9690f7f3-fb20-4a7e-a75f-8a3a1cb1ce0d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8adb8fb0c2978bdf5886d47fa0ee33cba8f8fbe4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="propertyinfoentryvalue"></a>PROPERTY_INFO_ENTRY_VALUE
代表屬性集中的特定屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp
PROPERTY_INFO_ENTRY_VALUE(dwPropID  
, value )  
```  
  
#### <a name="parameters"></a>參數  
 *dwPropID*  
 [in] [DBPROPID](https://msdn.microsoft.com/en-us/library/ms723882.aspx) 值，可搭配屬性集 GUID 以識別屬性。  
  
 *值*  
 [in] `DWORD`類型的屬性值。  
  
## <a name="remarks"></a>備註  
 使用這個巨集，您可以直接指定類型的屬性值`DWORD`。 若要設定為 ATLDB 中定義的預設值的屬性。H、 使用[PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md)。 若要設定的值、 旗標和屬性的選項，使用[PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md)。  
  
## <a name="example"></a>範例  
 請參閱 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 提供者樣板的巨集](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)   
 [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)