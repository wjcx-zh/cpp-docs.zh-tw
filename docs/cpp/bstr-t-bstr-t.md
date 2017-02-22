---
title: "_bstr_t::_bstr_t | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_bstr_t::_bstr_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_bstr_t 類別"
  - "_bstr_t 方法"
  - "BSTR 物件"
ms.assetid: 116d994e-5a72-4351-afbe-866c80b4c165
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# _bstr_t::_bstr_t
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 建構 `_bstr_t` 物件。  
  
## 語法  
  
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
  
#### 參數  
 `s1`  
 要複製的 `_bstr_t` 物件。  
  
 `s2`  
 多位元組字串。  
  
 `s3`  
 Unicode 字串  
  
 `var`  
 [\_variant\_t](../cpp/variant-t-class.md) 物件。  
  
 `bstr`  
 現有的 `BSTR` 物件。  
  
 `fCopy`  
 如果是 `false`，則 `bstr` 引數會附加至新的物件，而不需要藉由呼叫 `SysAllocString` 製作複本。  
  
## 備註  
 下表將說明 `_bstr_t`建構函式。  
  
|建構函式|說明|  
|----------|--------|  
|`_bstr_t( )`|建構封裝 null `BSTR` 物件的預設 `_bstr_t` 物件。|  
|`_bstr_t( _bstr_t&`  `s1`  `)`|將 `_bstr_t` 物件建構為另一個物件的複本。<br /><br /> 這是「*淺層*」\(shallow\) 複本，它會累加封裝的 `BSTR` 物件參考計數，而不會建立新的物件。|  
|`_bstr_t( char*`  `s2`  `)`|透過呼叫 `SysAllocString` 建構 `_bstr_t` 以建立新的 `BSTR` 物件並加以封裝。<br /><br /> 這個建構函式會先執行多位元組對 Unicode 的轉換。|  
|`_bstr_t( wchar_t*`  `s3`  `)`|透過呼叫 `SysAllocString` 建構 `_bstr_t` 以建立新的 `BSTR` 物件並加以封裝。|  
|`_bstr_t( _variant_t&`  `var`  `)`|先從封裝的 VARIANT 物件擷取 `BSTR` 物件，以從 `_variant_t` 物件建構 `_bstr_t` 物件。|  
|`_bstr_t( BSTR`  `bstr` `, bool`  `fCopy`  `)`|從現有的 `BSTR` 建構 `_bstr_t` 物件 \(而非 `wchar_t*` 字串\)。  如果 `fCopy` 是 false，則供應的 `BSTR` 會附加至新的物件，而不使用 `SysAllocString` 製作新複本。<br /><br /> 類型程式庫標題中的包裝函式會使用此建構函式封裝，並取得以介面方法傳回之 `BSTR` 的擁有權。|  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_bstr\_t 類別](../cpp/bstr-t-class.md)   
 [\_variant\_t 類別](../cpp/variant-t-class.md)