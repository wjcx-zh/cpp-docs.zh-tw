---
title: '_bstr_t:: wchar_t*，_bstr_t:: char* |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::wchar_t*
- _bstr_t::char*
dev_langs:
- C++
helpviewer_keywords:
- operator wchar_t* [C++]
- operator char* [C++]
ms.assetid: acd9f4a7-b427-42c2-aaae-acae21cab317
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 55225ba97848b2b503742d15ccf032e99342f0be
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
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
  
## <a name="see-also"></a>另請參閱  
 [_bstr_t 類別](../cpp/bstr-t-class.md)