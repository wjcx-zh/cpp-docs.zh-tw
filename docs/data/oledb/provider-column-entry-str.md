---
title: PROVIDER_COLUMN_ENTRY_STR |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- PROVIDER_COLUMN_ENTRY_STR
dev_langs:
- C++
helpviewer_keywords:
- PROVIDER_COLUMN_ENTRY_STR macro
ms.assetid: f1c27dd6-9ab8-4821-8685-d4dd15e76e88
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9ede31951c916c8b70b4942c3077442b5e2e3313
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="providercolumnentrystr"></a>PROVIDER_COLUMN_ENTRY_STR
表示提供者支援的特定資料行。  
  
## <a name="syntax"></a>語法  
  
```cpp
PROVIDER_COLUMN_ENTRY_STR(name  
, ordinal, member )  
```  
  
#### <a name="parameters"></a>參數  
 *name*  
 [in]資料行名稱。  
  
 `ordinal`  
 [in] 資料行編號。 除非資料行是書籤資料行，資料行數目必須為 0。  
  
 `member`  
 [in]中儲存資料的資料類別的成員變數。  
  
## <a name="remarks"></a>備註  
 使用這個巨集，當資料行的資料會被假設為[DBTYPE_STR](https://msdn.microsoft.com/en-us/library/ms711251.aspx)。  
  
## <a name="example"></a>範例  
 請參閱[BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md)。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 提供者樣板的巨集](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)   
 [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)