---
title: 登錄資料交換巨集 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- atlplus/ATL::BEGIN_RDX_MAP
- atlplus/ATL::END_RDX_MAP
- atlplus/ATL::RDX_BINARY
- atlplus/ATL::RDX_CSTRING_TEXT
- atlplus/ATL::RDX_DWORD
- atlplus/ATL::RDX_TEXT
dev_langs:
- C++
helpviewer_keywords:
- RegistryDataExchange function, macros
ms.assetid: c1bc5e79-2307-43d2-9d10-3a62ffadf473
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0bc12c48ef628a42c309c44ce0fc37abda9b6690
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="registry-data-exchange-macros"></a>登錄資料交換巨集
這些巨集執行登錄資料交換作業。  
  
|||  
|-|-|  
|[BEGIN_RDX_MAP](#begin_rdx_map)|標記登錄資料交換對應的開頭。|  
|[END_RDX_MAP](#end_rdx_map)|登錄資料交換對應結束標記。|  
|[RDX_BINARY](#rdx_binary)|將指定的登錄項目與指定的成員變數的型別為 BYTE 產生關聯。|  
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|將指定的登錄項目與 CString 類型的指定的成員變數產生關聯。|  
|[RDX_DWORD](#rdx_dword)|將指定的登錄項目與指定的成員變數的類型為 DWORD 產生關聯。|  
|[RDX_TEXT](#rdx_text)|將指定的登錄項目與 TCHAR 類型的指定的成員變數產生關聯。|  

## <a name="requirements"></a>需求  
 **標頭：** atlplus.h  
   
##  <a name="begin_rdx_map"></a>BEGIN_RDX_MAP  
 標記登錄資料交換對應的開頭。  
  
```
BEGIN_RDX_MAP
```  
  
### <a name="remarks"></a>備註  
 在登錄資料交換模式會使用下列巨集，來讀取和寫入系統登錄中的項目：  
  
|巨集|描述|  
|-----------|-----------------|  
|[RDX_BINARY](#rdx_binary)|將指定的登錄項目與指定的成員變數的型別為 BYTE 產生關聯。|  
|[RDX_DWORD](#rdx_dword)|將指定的登錄項目與指定的成員變數的類型為 DWORD 產生關聯。|  
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|將指定的登錄項目與 CString 類型的指定的成員變數產生關聯。|  
|[RDX_TEXT](#rdx_text)|將指定的登錄項目與 TCHAR 類型的指定的成員變數產生關聯。|  
  
 全域函式[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)，或成員函式所建立的相同名稱的`BEGIN_RDX_MAP`和`END_RDX_MAP`巨集，應該用於您的程式碼需要系統登錄之間交換資料時，RDX 對應所指定的變數。  
  
##  <a name="end_rdx_map"></a>END_RDX_MAP  
 登錄資料交換對應結束標記。  
  
```
END_RDX_MAP
```  
  
##  <a name="rdx_binary"></a>RDX_BINARY  
 將指定的登錄項目與指定的成員變數的型別為 BYTE 產生關聯。  
  
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
 登錄機碼根目錄。  
  
 `subkey`  
 登錄子機碼。  
  
 `valuename`  
 登錄機碼。  
  
 `member`  
 要與指定的登錄項目相關的成員變數。  
  
 `member_size`  
 以位元組為單位的成員變數大小。  
  
### <a name="remarks"></a>備註  
 這個巨集用於搭配`BEGIN_RDX_MAP`和`END_RDX_MAP`巨集，以將成員變數與指定的登錄項目產生關聯。 全域函式[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)，或成員函式所建立的相同名稱的`BEGIN_RDX_MAP`和`END_RDX_MAP`巨集，應該用來執行的系統登錄與成員之間的資料交換RDX 對應中的變數。  
  
##  <a name="rdx_cstring_text"></a>RDX_CSTRING_TEXT  
 將指定的登錄項目與 CString 類型的指定的成員變數產生關聯。  
  
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
 登錄機碼根目錄。  
  
 `subkey`  
 登錄子機碼。  
  
 `valuename`  
 登錄機碼。  
  
 `member`  
 要與指定的登錄項目相關的成員變數。  
  
 `member_size`  
 以位元組為單位的成員變數大小。  
  
### <a name="remarks"></a>備註  
 這個巨集用於搭配`BEGIN_RDX_MAP`和`END_RDX_MAP`巨集，以將成員變數與指定的登錄項目產生關聯。 全域函式[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)，或成員函式所建立的相同名稱的`BEGIN_RDX_MAP`和`END_RDX_MAP`巨集，應該用來執行的系統登錄與成員之間的資料交換RDX 對應中的變數。  
  
##  <a name="rdx_dword"></a>RDX_DWORD  
 將指定的登錄項目與指定的成員變數的類型為 DWORD 產生關聯。  
  
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
 登錄機碼根目錄。  
  
 `subkey`  
 登錄子機碼。  
  
 `valuename`  
 登錄機碼。  
  
 `member`  
 要與指定的登錄項目相關的成員變數。  
  
 `member_size`  
 以位元組為單位的成員變數大小。  
  
### <a name="remarks"></a>備註  
 這個巨集用於搭配`BEGIN_RDX_MAP`和`END_RDX_MAP`巨集，以將成員變數與指定的登錄項目產生關聯。 全域函式[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)，或成員函式所建立的相同名稱的`BEGIN_RDX_MAP`和`END_RDX_MAP`巨集，應該用來執行的系統登錄與成員之間的資料交換RDX 對應中的變數。  
  
##  <a name="rdx_text"></a>RDX_TEXT  
 將指定的登錄項目與 TCHAR 類型的指定的成員變數產生關聯。  
  
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
 登錄機碼根目錄。  
  
 `subkey`  
 登錄子機碼。  
  
 `valuename`  
 登錄機碼。  
  
 `member`  
 要與指定的登錄項目相關的成員變數。  
  
 `member_size`  
 以位元組為單位的成員變數大小。  
  
### <a name="remarks"></a>備註  
 這個巨集用於搭配`BEGIN_RDX_MAP`和`END_RDX_MAP`巨集，以將成員變數與指定的登錄項目產生關聯。 全域函式[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)，或成員函式所建立的相同名稱的`BEGIN_RDX_MAP`和`END_RDX_MAP`巨集，應該用來執行的系統登錄與成員之間的資料交換RDX 對應中的變數。  
  
## <a name="see-also"></a>請參閱  
 [巨集](../../atl/reference/atl-macros.md)   
 [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)







