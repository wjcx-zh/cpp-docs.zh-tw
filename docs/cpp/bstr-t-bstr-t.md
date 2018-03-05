---
title: "_bstr_t::_bstr_t |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _bstr_t::_bstr_t
dev_langs:
- C++
helpviewer_keywords:
- BSTR object
- _bstr_t method [C++]
- _bstr_t class
ms.assetid: 116d994e-5a72-4351-afbe-866c80b4c165
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c0dc49e5fa6b8899e4c9ca6bb15feeebb9cc0fe3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="bstrtbstrt"></a>_bstr_t::_bstr_t
**Microsoft 特定的**  
  
 建構 `_bstr_t` 物件。  
  
## <a name="syntax"></a>語法  
  
```  
_bstr_t( ) throw( );   
_bstr_t(  
   const _bstr_t& s1   
) throw( );  
_bstr_t(  
   const char* s2   
);  
_bstr_t(  
   const wchar_t* s3   
);  
_bstr_t(  
   const _variant_t& var   
);  
_bstr_t(  
   BSTR bstr,  
   bool fCopy   
);  
```  
  
#### <a name="parameters"></a>參數  
 `s1`  
 要複製的 `_bstr_t` 物件。  
  
 `s2`  
 多位元組字串。  
  
 `s3`  
 Unicode 字串  
  
 `var`  
 A [_variant_t](../cpp/variant-t-class.md)物件。  
  
 `bstr`  
 現有的 `BSTR` 物件。  
  
 `fCopy`  
 如果是 `false`，則 `bstr` 引數會附加至新的物件，而不需要藉由呼叫 `SysAllocString` 製作複本。  
  
## <a name="remarks"></a>備註  
 下表將說明 `_bstr_t`建構函式。  
  
|建構函式|描述|  
|-----------------|-----------------|  
|`_bstr_t( )`|建構預設`_bstr_t`封裝 null 物件`BSTR`物件。|  
|`_bstr_t( _bstr_t&`  `s1`  `)`|將 `_bstr_t` 物件建構為另一個物件的複本。<br /><br /> 這是*淺層*遞增參考計數的封裝的複本`BSTR`而不是建立一個新的物件。|  
|`_bstr_t( char*`  `s2`  `)`|透過呼叫 `_bstr_t` 建構 `SysAllocString` 以建立新的 `BSTR` 物件並加以封裝。<br /><br /> 這個建構函式會先執行多位元組對 Unicode 的轉換。|  
|`_bstr_t( wchar_t*`  `s3`  `)`|透過呼叫 `_bstr_t` 建構 `SysAllocString` 以建立新的 `BSTR` 物件並加以封裝。|  
|`_bstr_t( _variant_t&`  `var`  `)`|先從封裝的 VARIANT 物件擷取 `_bstr_t` 物件，以從 `_variant_t` 物件建構 `BSTR` 物件。|  
|`_bstr_t( BSTR`  `bstr` `, bool`  `fCopy`  `)`|從現有的 `_bstr_t` 建構 `BSTR` 物件 (而非 `wchar_t*` 字串)。 如果 `fCopy` 是 false，則供應的 `BSTR` 會附加至新的物件，而不使用 `SysAllocString` 製作新複本。<br /><br /> 類型程式庫標題中的包裝函式會使用此建構函式封裝，並取得以介面方法傳回之 `BSTR` 的擁有權。|  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [_bstr_t 類別](../cpp/bstr-t-class.md)   
 [_variant_t 類別](../cpp/variant-t-class.md)