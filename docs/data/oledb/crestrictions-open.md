---
title: 'Crestrictions:: Open |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRestrictions.Open
- ATL::CRestrictions::Open
- ATL.CRestrictions.Open
- CRestrictions::Open
dev_langs:
- C++
helpviewer_keywords:
- Open method
ms.assetid: 0aff0cc3-543a-47d2-8d6b-ebb36926b6db
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8039d55312687cc28be27f2ed7726b9bda1b44aa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="crestrictionsopen"></a>CRestrictions::Open
傳回的結果集根據使用者所提供的限制。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Open(const CSession& session,  
   LPCTSTR lpszParam 1 = NULL,  
   LPCTSTR lpszParam 2 = NULL,  
   LPCTSTR lpszParam 3 = NULL,  
   LPCTSTR lpszParam 4 = NULL,  
   LPCTSTR lpszParam 5 = NULL,  
   LPCTSTR lpszParam 6 = NULL,  
   LPCTSTR lpszParam 7 = NULL,  
   bool bBind = true);  
```  
  
#### <a name="parameters"></a>參數  
 `session`  
 [in]指定用來連接到資料來源的現有工作階段物件。  
  
 *lpszParam*  
 [in]在結構描述資料列上指定的限制。  
  
 `bBind`  
 [in]指定是否要自動繫結資料行對應。 預設值是**true**，因而導致自動繫結的資料行對應。 設定`bBind`至**false**可防止自動繫結的資料行對應，讓您以手動方式可以繫結。 （手動繫結是 OLAP 使用者的特別感興趣的）。  
  
## <a name="return-value"></a>傳回值  
 其中一個標準`HRESULT`值。  
  
## <a name="remarks"></a>備註  
 您可以指定最多七個限制的結構描述資料列集。  
  
 請參閱[IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx)如每個結構描述資料列集上定義的限制相關資訊。  
  
## <a name="requirements"></a>需求  
 **標頭：** atldbsch.h  
  
## <a name="see-also"></a>另請參閱  
 [CRestrictions 類別](../../data/oledb/crestrictions-class.md)   
 [結構描述資料列集類別和 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)