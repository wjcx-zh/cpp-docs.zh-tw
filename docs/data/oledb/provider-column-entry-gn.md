---
title: PROVIDER_COLUMN_ENTRY_GN | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PROVIDER_COLUMN_ENTRY_GN
dev_langs:
- C++
helpviewer_keywords:
- PROVIDER_COLUMN_ENTRY_GN macro
ms.assetid: be77ba85-634c-4e28-832f-d2fa40413254
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 203f339dc031f4a21f16181043b051c4eaa5ec35
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="providercolumnentrygn"></a>PROVIDER_COLUMN_ENTRY_GN
表示提供者支援的特定資料行。  
  
## <a name="syntax"></a>語法  
  
```cpp
PROVIDER_COLUMN_ENTRY_GN (name  
, ordinal, flags, colSize, dbtype, precision, scale, guid )  
```  
  
#### <a name="parameters"></a>參數  
 *name*  
 [in]資料行名稱。  
  
 `ordinal`  
 [in] 資料行編號。 除非資料行是書籤資料行，資料行數目必須為 0。  
  
 `flags`  
 [in]指定如何傳回資料。 請參閱`dwFlags`描述[DBBINDING 結構](https://msdn.microsoft.com/en-us/library/ms716845.aspx)。  
  
 *colSize*  
 [in]資料行大小。  
  
 `dbtype`  
 [in]表示值的資料類型。 請參閱**wType**描述[DBBINDING 結構](https://msdn.microsoft.com/en-us/library/ms716845.aspx)。  
  
 *precision*  
 [in]指出如果取得資料時所要使用的有效位數*dbType*是`DBTYPE_NUMERIC`或**DBTYPE_DECIMAL**。 請參閱**bPrecision**描述[DBBINDING 結構](https://msdn.microsoft.com/en-us/library/ms716845.aspx)。  
  
 `scale`  
 [in]指出如果 dbType 是取得資料時所要使用的小數位`DBTYPE_NUMERIC`或**DBTYPE_DECIMAL**。 請參閱**bScale**描述[DBBINDING 結構](https://msdn.microsoft.com/en-us/library/ms716845.aspx)。  
  
 `guid`  
 結構描述資料列集 GUID。 請參閱[IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx)中*OLE DB 程式設計人員參考*取得一份結構描述資料列集和其 Guid。  
  
## <a name="remarks"></a>備註  
 可讓您指定資料行的大小、 資料類型、 有效位數、 小數位數和結構描述資料列集 GUID。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 提供者樣板的巨集](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)   
 [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)