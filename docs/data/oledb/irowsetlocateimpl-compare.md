---
title: 'Irowsetlocateimpl:: Compare |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IRowsetLocateImpl.Compare
- IRowsetLocateImpl::Compare
- IRowsetLocateImpl.Compare
- ATL::IRowsetLocateImpl::Compare
dev_langs:
- C++
helpviewer_keywords:
- Compare method
ms.assetid: 6f84052c-c68c-480a-982f-03748faa7d5d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 208f912e92045daec36066e1dcc06fc38b5a8ed2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33105279"
---
# <a name="irowsetlocateimplcompare"></a>IRowsetLocateImpl::Compare
比較兩個書籤。  
  
## <a name="syntax"></a>語法  
  
```cpp
      STDMETHOD (Compare )(HCHAPTER /* hReserved */,  
   DBBKMARK cbBookmark1,  
   const BYTE* pBookmark1,  
   DBBKMARK cbBookmark2,  
   const BYTE* pBookmark2,  
   DBCOMPARE* pComparison);  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[IRowsetLocate::Compare](https://msdn.microsoft.com/en-us/library/ms709539.aspx)中*OLE DB 程式設計人員參考*。  
  
## <a name="remarks"></a>備註  
 其中一個書籤可以是一種標準 OLE DB 定義[標準的書籤](https://msdn.microsoft.com/en-us/library/ms712954.aspx)(**DBBMK_FIRST**， **DBBMK_LAST**，或**DBBMK_INVALID**)。 中傳回的值`pComparison`指出兩個書籤之間的關聯性：  
  
-   **DBCOMPARE_LT** (`cbBookmark1`之前`cbBookmark2`。)  
  
-   **DBCOMPARE_EQ** (`cbBookmark1`等於`cbBookmark2`。)  
  
-   **DBCOMPARE_GT** (`cbBookmark1`之後`cbBookmark2`。)  
  
-   **DBCOMPARE_NE** （書籤是相等和不排序）。  
  
-   **DBCOMPARE_NOTCOMPARABLE** （無法比較的書籤。）  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [IRowsetLocateImpl 類別](../../data/oledb/irowsetlocateimpl-class.md)