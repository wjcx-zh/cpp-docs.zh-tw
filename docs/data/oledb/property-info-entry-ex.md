---
title: PROPERTY_INFO_ENTRY_EX | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- PROPERTY_INFO_ENTRY_EX
dev_langs:
- C++
helpviewer_keywords:
- PROPERTY_INFO_ENTRY_EX macro
ms.assetid: af32dfcd-4c50-449d-af3b-48d21bd67a04
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6696067e94a10e57d52f5875b712f100c5ac6902
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="propertyinfoentryex"></a>PROPERTY_INFO_ENTRY_EX
代表屬性集中的特定屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp
PROPERTY_INFO_ENTRY_EX(dwPropID  
, vt, dwFlags, value, options )  
```  
  
#### <a name="parameters"></a>參數  
 *dwPropID*  
 [in] [DBPROPID](https://msdn.microsoft.com/en-us/library/ms723882.aspx) 值，可搭配屬性集 GUID 以識別屬性。  
  
 *vt*  
 [in] 此屬性項目的 [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4) 。  
  
 `dwFlags`  
 [in] 描述此屬性項目的 [DBPROPFLAGS](https://msdn.microsoft.com/en-us/library/ms724342.aspx) 值。  
  
 *值*  
 [in] `DWORD`類型的屬性值。  
  
 `options`  
 **DBPROPOPTIONS_REQUIRED** 或 **DBPROPOPTIONS_SETIFCHEAP**。 一般而言，提供者不需要設定 `options` ，因為它是由消費者所設定。  
  
## <a name="remarks"></a>備註  
 透過這個巨集，您可以直接指定 `DWORD` 類型的屬性值，以及選項和旗標。 若只要將屬性設定為 ATLDB.H 中定義的預設值，請使用 [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md)。 若要將屬性設定為您選擇的值，請使用 [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md)，而不需要設定屬性的選項或旗標。  
  
## <a name="example"></a>範例  
 請參閱 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 提供者樣板的巨集](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)   
 [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)