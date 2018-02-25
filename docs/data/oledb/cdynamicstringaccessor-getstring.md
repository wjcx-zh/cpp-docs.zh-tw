---
title: CDynamicStringAccessor::GetString | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDynamicStringAccessor.GetString
- CDynamicStringAccessor::GetString
dev_langs:
- C++
helpviewer_keywords:
- GetString method
ms.assetid: 4af27f27-7589-49f5-93d8-6ef05c023c8a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7c6a2340ddd0e123720cd59bb2ee0bf8ca58504f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="cdynamicstringaccessorgetstring"></a>CDynamicStringAccessor::GetString
擷取指定資料行的資料做為字串。  
  
## <a name="syntax"></a>語法  
  
```cpp
      BaseType* GetString(DBORDINAL nColumn) const throw();  

BaseType* GetString(const CHAR* pColumnName) const throw();  

BaseType* GetString(const WCHAR* pColumnName) const throw();  
```  
  
#### <a name="parameters"></a>參數  
 `nColumn`  
 [in] 資料行編號。 資料行數字開頭為 1。 值為 0 參考的書籤資料行中，如果有的話。  
  
 `pColumnName`  
 [in]包含資料行名稱的字元字串指標。  
  
## <a name="return-value"></a>傳回值  
 從指定的資料行擷取的字串值的指標。 值為類型***BaseType***，這將成為**CHAR**或**WCHAR**根據 _UNICODE 是否已定義。 如果找不到指定的資料行，傳回 NULL。  
  
## <a name="remarks"></a>備註  
 第二個覆寫表單會採用資料行名稱做為 ANSI 字串。 第三個覆寫表單會採用資料行名稱為 Unicode 字串。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CDynamicStringAccessor 類別](../../data/oledb/cdynamicstringaccessor-class.md)