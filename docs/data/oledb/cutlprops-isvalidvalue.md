---
title: "Cutlprops:: Isvalidvalue |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CUtlProps::IsValidValue
- CUtlProps.IsValidValue
- IsValidValue
dev_langs: C++
helpviewer_keywords: IsValidValue method
ms.assetid: 1164556e-8d98-429c-a396-fc9a699e0e97
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 06193b8c560c5ac6006698813222e698a98bccc3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cutlpropsisvalidvalue"></a>CUtlProps::IsValidValue
用來驗證之前設定屬性的值。  
  
## <a name="syntax"></a>語法  
  
```  
  
      virtual HRESULT CUtlPropsBase::IsValidValue(  
   ULONG /* iCurSet */,  
   DBPROP* pDBProp   
);  
```  
  
#### <a name="parameters"></a>參數  
 `iCurSet`  
 屬性集陣列; 中的索引零，如果只有一個屬性集。  
  
 `pDBProp`  
 內容識別碼和新值[DBPROP](https://msdn.microsoft.com/en-us/library/ms717970.aspx)結構。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。 預設會傳回值為`S_OK`。  
  
## <a name="remarks"></a>備註  
 如果您有想要在您要用來設定屬性的值上執行任何驗證常式，您應該覆寫這個函式。 例如，您也可以驗證**DBPROP_AUTH_PASSWORD**針對密碼資料表來判斷有效的值。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [CUtlProps 類別](../../data/oledb/cutlprops-class.md)