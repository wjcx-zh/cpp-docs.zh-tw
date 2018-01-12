---
title: "_bstr_t:: wchar_t*，_bstr_t:: char* |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _bstr_t::wchar_t*
- _bstr_t::char*
dev_langs: C++
helpviewer_keywords:
- operator wchar_t* [C++]
- operator char* [C++]
ms.assetid: acd9f4a7-b427-42c2-aaae-acae21cab317
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c8dc91f76e31b124235347d7bef3e95f7cc5bf48
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="bstrtwchart-bstrtchar"></a>_bstr_t:: wchar_t*，_bstr_t:: char*
**Microsoft 特定的**  
  
 將 BSTR 字元做為窄字元或寬字元陣列傳回。  
  
## <a name="syntax"></a>語法  
  
```  
  
      operator const wchar_t*( ) const throw( );   
operator wchar_t*( ) const throw( );   
operator const char*( ) const;   
operator char*( ) const;  
```  
  
## <a name="remarks"></a>備註  
 這些運算子可用來擷取 `BSTR` 物件所封裝的字元資料。 指派新值給傳回的指標並不會修改原始 BSTR 資料。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [_bstr_t 類別](../cpp/bstr-t-class.md)