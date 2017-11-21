---
title: "BEGIN_PROPERTY_SET_EX |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BEGIN_PROPERTY_SET_EX
dev_langs: C++
helpviewer_keywords: BEGIN_PROPERTY_SET_EX macro
ms.assetid: c95e7fab-edce-47b8-b282-200e53a2ea8a
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 57e1b6b75404bf2ccef7cff76adc3d23a3609b1a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="beginpropertysetex"></a>BEGIN_PROPERTY_SET_EX
在屬性中設定屬性的開頭的標記集合對應。  
  
## <a name="syntax"></a>語法  
  
```  
  
BEGIN_PROPERTY_SET_EX(  
guid  
, flags )  
```  
  
#### <a name="parameters"></a>參數  
 `guid`  
 [in]GUID 屬性。  
  
 `flags`  
 [in]**UPROPSET_HIDDEN**的任何屬性集，您不想公開，或**UPROPSET_PASSTHROUGH**提供者公開的範圍以外的提供者定義的屬性。  
  
## <a name="example"></a>範例  
 請參閱 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 提供者樣板的巨集](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)   
 [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)