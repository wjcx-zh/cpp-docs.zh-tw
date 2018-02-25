---
title: PROVIDER_COLUMN_ENTRY | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- PROVIDER_COLUMN_ENTRY
dev_langs:
- C++
helpviewer_keywords:
- PROVIDER_COLUMN_ENTRY macro
ms.assetid: 7921cfc1-aa9c-493e-8fc4-9d4294cafe72
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 982f15ad5f04aead259adabb362d249354f3421f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="providercolumnentry"></a>PROVIDER_COLUMN_ENTRY
表示提供者支援的特定資料行。  
  
## <a name="syntax"></a>語法  
  
```cpp
PROVIDER_COLUMN_ENTRY (name  
, ordinal, member )  
```  
  
#### <a name="parameters"></a>參數  
 *name*  
 [in]資料行名稱。  
  
 `ordinal`  
 [in] 資料行編號。 除非資料行是書籤資料行，資料行數目必須為 0。  
  
 `member`  
 [in]中的成員變數`dataClass`對應此資料行。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 提供者樣板的巨集](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)   
 [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)