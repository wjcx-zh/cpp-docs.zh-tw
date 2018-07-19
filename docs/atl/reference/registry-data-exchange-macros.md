---
title: 登錄資料交換巨集 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7473bed5e4bf973dcea4d186e9b5b3367fb03ff1
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37880355"
---
# <a name="registry-data-exchange-macros"></a>登錄資料交換巨集
這些巨集執行登錄資料交換作業。  
  
|||  
|-|-|  
|[BEGIN_RDX_MAP](#begin_rdx_map)|將標記登錄資料交換對應的開頭。|  
|[END_RDX_MAP](#end_rdx_map)|將標記登錄資料交換 map 的結尾。|  
|[RDX_BINARY](#rdx_binary)|將指定的登錄項目與指定的成員變數的位元組類型產生關聯。|  
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|關聯類型 CString 的指定的成員變數中指定的登錄項目。|  
|[RDX_DWORD](#rdx_dword)|將指定的登錄項目與指定的成員變數 DWORD 型別產生關聯。|  
|[RDX_TEXT](#rdx_text)|關聯類型 TCHAR 的指定的成員變數中指定的登錄項目。|  

## <a name="requirements"></a>需求  
 **標頭：** atlplus.h  
   
##  <a name="begin_rdx_map"></a>  BEGIN_RDX_MAP  
 將標記登錄資料交換對應的開頭。  
  
```
BEGIN_RDX_MAP
```  
  
### <a name="remarks"></a>備註  
 下列巨集是在登錄資料交換模式來讀取和寫入系統登錄中的項目：  
  
|巨集|描述|  
|-----------|-----------------|  
|[RDX_BINARY](#rdx_binary)|將指定的登錄項目與指定的成員變數的位元組類型產生關聯。|  
|[RDX_DWORD](#rdx_dword)|將指定的登錄項目與指定的成員變數 DWORD 型別產生關聯。|  
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|關聯類型 CString 的指定的成員變數中指定的登錄項目。|  
|[RDX_TEXT](#rdx_text)|關聯類型 TCHAR 的指定的成員變數中指定的登錄項目。|  
  
 全域函式[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)，或當您的程式碼需要在系統登錄之間交換資料時，就應該使用 BEGIN_RDX_MAP 和 END_RDX_MAP 巨集，所建立之相同名稱的成員函式，RDX 對應中指定的變數。  
  
##  <a name="end_rdx_map"></a>  END_RDX_MAP  
 將標記登錄資料交換 map 的結尾。  
  
```
END_RDX_MAP
```  
  
##  <a name="rdx_binary"></a>  RDX_BINARY  
 將指定的登錄項目與指定的成員變數的位元組類型產生關聯。  
  
```
RDX_BINARY(
    rootkey, 
    subkey, 
    valuename, 
    member, 
    member_size )
```  
  
### <a name="parameters"></a>參數  
 *Rootkey*  
 登錄機碼的根目錄中。  
  
 *子機碼*  
 登錄子機碼。  
  
 *valuename*  
 登錄機碼。  
  
 *成員*  
 要與指定的登錄項目產生關聯的成員變數。  
  
 *member_size*  
 大小，以位元組為單位的成員變數。  
  
### <a name="remarks"></a>備註  
 這個巨集搭配 BEGIN_RDX_MAP 和 END_RDX_MAP 巨集用於指定的登錄項目相關聯的成員變數。 全域函式[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)，或 BEGIN_RDX_MAP 和 END_RDX_MAP 巨集，所建立之相同名稱的成員函式應該用來執行系統登錄與成員變數之間的資料交換在 RDX 對應。  
  
##  <a name="rdx_cstring_text"></a>  RDX_CSTRING_TEXT  
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
 *Rootkey*  
 登錄機碼的根目錄中。  
  
 *子機碼*  
 登錄子機碼。  
  
 *valuename*  
 登錄機碼。  
  
 *成員*  
 要與指定的登錄項目產生關聯的成員變數。  
  
 *member_size*  
 大小，以位元組為單位的成員變數。  
  
### <a name="remarks"></a>備註  
 這個巨集搭配 BEGIN_RDX_MAP 和 END_RDX_MAP 巨集用於指定的登錄項目相關聯的成員變數。 全域函式[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)，或 BEGIN_RDX_MAP 和 END_RDX_MAP 巨集，所建立之相同名稱的成員函式應該用來執行系統登錄與成員變數之間的資料交換在 RDX 對應。  
  
##  <a name="rdx_dword"></a>  RDX_DWORD  
 將指定的登錄項目與指定的成員變數 DWORD 型別產生關聯。  
  
```
RDX_DWORD(
    rootkey, 
    subkey, 
    valuename, 
    member, 
    member_size )
```  
  
### <a name="parameters"></a>參數  
 *Rootkey*  
 登錄機碼的根目錄中。  
  
 *子機碼*  
 登錄子機碼。  
  
 *valuename*  
 登錄機碼。  
  
 *成員*  
 要與指定的登錄項目產生關聯的成員變數。  
  
 *member_size*  
 大小，以位元組為單位的成員變數。  
  
### <a name="remarks"></a>備註  
 這個巨集搭配 BEGIN_RDX_MAP 和 END_RDX_MAP 巨集用於指定的登錄項目相關聯的成員變數。 全域函式[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)，或 BEGIN_RDX_MAP 和 END_RDX_MAP 巨集，所建立之相同名稱的成員函式應該用來執行系統登錄與成員變數之間的資料交換在 RDX 對應。  
  
##  <a name="rdx_text"></a>  RDX_TEXT  
 關聯類型 TCHAR 的指定的成員變數中指定的登錄項目。  
  
```
RDX_TEXT(
    rootkey, 
    subkey, 
    valuename, 
    member, 
    member_size )
```  
  
### <a name="parameters"></a>參數  
 *Rootkey*  
 登錄機碼的根目錄中。  
  
 *子機碼*  
 登錄子機碼。  
  
 *valuename*  
 登錄機碼。  
  
 *成員*  
 要與指定的登錄項目產生關聯的成員變數。  
  
 *member_size*  
 大小，以位元組為單位的成員變數。  
  
### <a name="remarks"></a>備註  
 這個巨集搭配 BEGIN_RDX_MAP 和 END_RDX_MAP 巨集用於指定的登錄項目相關聯的成員變數。 全域函式[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)，或 BEGIN_RDX_MAP 和 END_RDX_MAP 巨集，所建立之相同名稱的成員函式應該用來執行系統登錄與成員變數之間的資料交換在 RDX 對應。  
  
## <a name="see-also"></a>另請參閱  
 [巨集](../../atl/reference/atl-macros.md)   
 [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)







