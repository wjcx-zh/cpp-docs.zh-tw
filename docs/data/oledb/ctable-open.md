---
title: 'Ctable:: Open |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CTable.Open
- ATL::CTable::Open
- CTable::Open
- CTable.Open
dev_langs:
- C++
helpviewer_keywords:
- Open method
ms.assetid: 5d006d95-74d7-4e2b-b243-a33bc53b5455
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ca271d8a88035151e6845db6b7cb9423c71c73ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33102234"
---
# <a name="ctableopen"></a>CTable::Open
開啟資料表。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Open(const CSession& session,  
   LPCWSTR wszTableName,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0) throw ();  


HRESULT Open(const CSession& session,  
   LPCSTR szTableName,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0) throw ();  


HRESULT Open(const CSession& session,  
   DBID& dbid,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0) throw ();  
```  
  
#### <a name="parameters"></a>參數  
 `session`  
 [in]工作階段，開啟該表格。  
  
 *wszTableName*  
 [in]若要開啟，資料表的名稱傳遞為 Unicode 字串。  
  
 *szTableName*  
 [in]若要開啟，資料表的名稱傳遞為 ANSI 字串。  
  
 *dbid*  
 [in]**DBID**来開啟的資料表。  
  
 *pPropSet*  
 [in]陣列的指標[DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx)結構，其中包含要設定屬性和值。 請參閱[屬性集和屬性群組](https://msdn.microsoft.com/en-us/library/ms713696.aspx)中*OLE DB 程式設計人員參考*Windows SDK 中。 預設值是 NULL，指定沒有屬性。  
  
 `ulPropSets`  
 [in]數目[DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx)結構傳入*Dbpropset*引數。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[iopenrowset:: Openrowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx)中*OLE DB 程式設計人員參考*。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CTable 類別](../../data/oledb/ctable-class.md)