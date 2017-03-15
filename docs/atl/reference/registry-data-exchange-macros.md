---
title: "登錄資料交換巨集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- RegistryDataExchange function, macros
ms.assetid: c1bc5e79-2307-43d2-9d10-3a62ffadf473
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: ee3c1d639ee4a6c6bd6cf26a8c59bb1a37a4fa02
ms.lasthandoff: 02/24/2017

---
# <a name="registry-data-exchange-macros"></a>登錄資料交換巨集
這些巨集執行登錄資料交換作業。  
  
|||  
|-|-|  
|[BEGIN_RDX_MAP](#begin_rdx_map)|標記登錄資料交換對應的開頭。|  
|[END_RDX_MAP](#end_rdx_map)|登錄資料交換對應結束標記。|  
|[RDX_BINARY](#rdx_binary)|關聯型別為 BYTE 的指定的成員變數中指定的登錄項目。|  
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|關聯類型 CString 的指定的成員變數中指定的登錄項目。|  
|[RDX_DWORD](#rdx_dword)|指定的登錄項目關聯至指定的成員變數的類型為 DWORD。|  
|[RDX_TEXT](#rdx_text)|將指定的登錄項目與指定的成員變數的型別 TCHAR 產生關聯。|  

## <a name="requirements"></a>需求  
 **標頭︰** atlplus.h  
   
##  <a name="a-namebeginrdxmapa--beginrdxmap"></a><a name="begin_rdx_map"></a>BEGIN_RDX_MAP  
 標記登錄資料交換對應的開頭。  
  
```
BEGIN_RDX_MAP
```  
  
### <a name="remarks"></a>備註  
 登錄資料交換對應內會使用下列巨集，來讀取和寫入系統登錄中的項目︰  
  
|巨集|說明|  
|-----------|-----------------|  
|[RDX_BINARY](#rdx_binary)|關聯型別為 BYTE 的指定的成員變數中指定的登錄項目。|  
|[RDX_DWORD](#rdx_dword)|指定的登錄項目關聯至指定的成員變數的類型為 DWORD。|  
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|關聯類型 CString 的指定的成員變數中指定的登錄項目。|  
|[RDX_TEXT](#rdx_text)|將指定的登錄項目與指定的成員變數的型別 TCHAR 產生關聯。|  
  
 全域函式[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)，或建立具有相同名稱的成員函式`BEGIN_RDX_MAP`和`END_RDX_MAP`巨集，應該使用，只要您的程式碼需要系統登錄和 RDX 對應所指定的變數之間交換資料。  
  
##  <a name="a-nameendrdxmapa--endrdxmap"></a><a name="end_rdx_map"></a>END_RDX_MAP  
 登錄資料交換對應結束標記。  
  
```
END_RDX_MAP
```  
  
##  <a name="a-namerdxbinarya--rdxbinary"></a><a name="rdx_binary"></a>RDX_BINARY  
 關聯型別為 BYTE 的指定的成員變數中指定的登錄項目。  
  
```
RDX_BINARY(
    rootkey, 
    subkey, 
    valuename, 
    member, 
    member_size )
```  
  
### <a name="parameters"></a>參數  
 `rootkey`  
 登錄索引鍵的根目錄中。  
  
 `subkey`  
 登錄子機碼。  
  
 `valuename`  
 登錄機碼。  
  
 `member`  
 要與指定的登錄項目相關的成員變數。  
  
 `member_size`  
 以位元組為單位的成員變數大小。  
  
### <a name="remarks"></a>備註  
 這個巨集用於搭配`BEGIN_RDX_MAP`和`END_RDX_MAP`巨集，以指定的登錄項目相關聯的成員變數。 全域函式[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)，或建立具有相同名稱的成員函式`BEGIN_RDX_MAP`和`END_RDX_MAP`巨集，應該用來執行 RDX 對應中的系統登錄和成員變數之間交換資料。  
  
##  <a name="a-namerdxcstringtexta--rdxcstringtext"></a><a name="rdx_cstring_text"></a>RDX_CSTRING_TEXT  
 關聯類型 CString 的指定的成員變數中指定的登錄項目。  
  
```
RDX_CSTRING_TEXT(
    rootkey, 
    subkey, 
    valuename, 
    member, 
    member_size )
```  
  
### <a name="parameters"></a>參數  
 `rootkey`  
 登錄索引鍵的根目錄中。  
  
 `subkey`  
 登錄子機碼。  
  
 `valuename`  
 登錄機碼。  
  
 `member`  
 要與指定的登錄項目相關的成員變數。  
  
 `member_size`  
 以位元組為單位的成員變數大小。  
  
### <a name="remarks"></a>備註  
 這個巨集用於搭配`BEGIN_RDX_MAP`和`END_RDX_MAP`巨集，以指定的登錄項目相關聯的成員變數。 全域函式[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)，或建立具有相同名稱的成員函式`BEGIN_RDX_MAP`和`END_RDX_MAP`巨集，應該用來執行 RDX 對應中的系統登錄和成員變數之間交換資料。  
  
##  <a name="a-namerdxdworda--rdxdword"></a><a name="rdx_dword"></a>RDX_DWORD  
 指定的登錄項目關聯至指定的成員變數的類型為 DWORD。  
  
```
RDX_DWORD(
    rootkey, 
    subkey, 
    valuename, 
    member, 
    member_size )
```  
  
### <a name="parameters"></a>參數  
 `rootkey`  
 登錄索引鍵的根目錄中。  
  
 `subkey`  
 登錄子機碼。  
  
 `valuename`  
 登錄機碼。  
  
 `member`  
 要與指定的登錄項目相關的成員變數。  
  
 `member_size`  
 以位元組為單位的成員變數大小。  
  
### <a name="remarks"></a>備註  
 這個巨集用於搭配`BEGIN_RDX_MAP`和`END_RDX_MAP`巨集，以指定的登錄項目相關聯的成員變數。 全域函式[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)，或建立具有相同名稱的成員函式`BEGIN_RDX_MAP`和`END_RDX_MAP`巨集，應該用來執行 RDX 對應中的系統登錄和成員變數之間交換資料。  
  
##  <a name="a-namerdxtexta--rdxtext"></a><a name="rdx_text"></a>RDX_TEXT  
 將指定的登錄項目與指定的成員變數的型別 TCHAR 產生關聯。  
  
```
RDX_TEXT(
    rootkey, 
    subkey, 
    valuename, 
    member, 
    member_size )
```  
  
### <a name="parameters"></a>參數  
 `rootkey`  
 登錄索引鍵的根目錄中。  
  
 `subkey`  
 登錄子機碼。  
  
 `valuename`  
 登錄機碼。  
  
 `member`  
 要與指定的登錄項目相關的成員變數。  
  
 `member_size`  
 以位元組為單位的成員變數大小。  
  
### <a name="remarks"></a>備註  
 這個巨集用於搭配`BEGIN_RDX_MAP`和`END_RDX_MAP`巨集，以指定的登錄項目相關聯的成員變數。 全域函式[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)，或建立具有相同名稱的成員函式`BEGIN_RDX_MAP`和`END_RDX_MAP`巨集，應該用來執行 RDX 對應中的系統登錄和成員變數之間交換資料。  
  
## <a name="see-also"></a>另請參閱  
 [巨集](../../atl/reference/atl-macros.md)   
 [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)








