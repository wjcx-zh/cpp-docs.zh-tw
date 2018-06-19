---
title: PROVIDER_COLUMN_ENTRY_TYPE_LENGTH |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- PROVIDER_COLUMN_ENTRY_TYPE_LENGTH
dev_langs:
- C++
helpviewer_keywords:
- PROVIDER_COLUMN_ENTRY_TYPE_LENGTH macro
ms.assetid: a60b1a8b-0903-4ff4-91ec-ed62126449fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ef9af591bff5a13a5780cc27ef169a8447c64cc7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106605"
---
# <a name="providercolumnentrytypelength"></a>PROVIDER_COLUMN_ENTRY_TYPE_LENGTH
表示提供者支援的特定資料行。  
  
## <a name="syntax"></a>語法  
  
```cpp
PROVIDER_COLUMN_ENTRY_TYPE_LENGTH(name  
, ordinal, dbtype, size, member )  
```  
  
#### <a name="parameters"></a>參數  
 *name*  
  
 [in]資料行名稱。  
  
 `ordinal`  
 [in] 資料行編號。 除非資料行是書籤資料行，資料行數目必須為 0。  
  
 `dbtype`  
 [in]中的資料類型[DBTYPE](https://msdn.microsoft.com/en-us/library/ms711251.aspx)。  
  
 `size`  
 [in]資料行大小，以位元組為單位。  
  
 `member`  
 [in]中儲存資料的資料類別的成員變數。  
  
## <a name="remarks"></a>備註  
 類似於[PROVIDER_COLUMN_ENTRY_LENGTH](../../data/oledb/provider-column-entry-length.md)但也可讓您指定資料行的資料類型，以及大小。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 提供者樣板的巨集](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)   
 [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)