---
title: 'Cdynamicstringaccessor:: Setstring |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicStringAccessor::SetString
- CDynamicStringAccessor.SetString
dev_langs:
- C++
helpviewer_keywords:
- SetString method
ms.assetid: 94846d8b-4c1b-47fe-acdc-1752981cee25
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f5f4b7f9354de7f6c6ad10ba472bfd31873a0355
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095901"
---
# <a name="cdynamicstringaccessorsetstring"></a>CDynamicStringAccessor::SetString
設定指定資料行的資料做為字串。  
  
## <a name="syntax"></a>語法  
  
```
HRESULT SetString(DBORDINAL nColumn,  
  BaseType* data) throw();  


HRESULT SetString(const CHAR* pColumnName,  
   BaseType* data) throw();  


HRESULT SetString(const WCHAR* pColumnName,  
   BaseType* data) throw();  
```  
  
#### <a name="parameters"></a>參數  
 `nColumn`  
 [in] 資料行編號。 資料行數字開頭為 1。 特殊值為 0 參考的書籤資料行中，如果有的話。  
  
 `pColumnName`  
 [in]包含資料行名稱的字元字串指標。  
  
 `data`  
 [in]要寫入至指定的資料行的字串資料指標。  
  
## <a name="return-value"></a>傳回值  
 設定指定之資料行的字串值指標。 值為類型`BaseType`，這將成為`CHAR`或`WCHAR`取決於是否`_UNICODE`未定義。  
  
## <a name="remarks"></a>備註  
 第二個覆寫表單會採用資料行名稱做為 ANSI 字串和第三個覆寫表單會以 Unicode 字串資料行名稱。  
  
 如果`_SECURE_ATL`定義具有非零值，執行階段判斷提示失敗則會產生輸入`data`字串的長度超過參考的資料行的最大容許長度。 否則，請輸入的字串會被截斷，如果它是長度超過最大容許長度。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CDynamicStringAccessor 類別](../../data/oledb/cdynamicstringaccessor-class.md)