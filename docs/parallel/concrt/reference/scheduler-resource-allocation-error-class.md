---
title: scheduler_resource_allocation_error 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error::scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error::get_error_code
dev_langs:
- C++
helpviewer_keywords:
- scheduler_resource_allocation_error class
ms.assetid: 8b40449a-7abb-4d0a-bb85-c0e9a495ae97
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c3b11a548bc98c44697de45c628205dc3e720971
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686681"
---
# <a name="schedulerresourceallocationerror-class"></a>scheduler_resource_allocation_error 類別
這個類別描述因無法在並行執行階段中取得關鍵來源而擲回的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```
class scheduler_resource_allocation_error : public std::exception;
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[scheduler_resource_allocation_error](#ctor)|多載。 建構 `scheduler_resource_allocation_error` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[get_error_code](#get_error_code)|傳回造成例外狀況的錯誤碼。|  
  
## <a name="remarks"></a>備註  
 從並行執行階段內的作業系統呼叫失敗時，通常會擲回這個例外狀況。 通常會從呼叫 Win32 方法 `GetLastError` 傳回的錯誤碼會轉換成 `HRESULT` 類型的值，並且可以使用 `get_error_code` 方法擷取。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `exception`  
  
 `scheduler_resource_allocation_error`  
  
## <a name="requirements"></a>需求  
 **標頭：** concrt.h  
  
 **命名空間：** concurrency  
  
##  <a name="get_error_code"></a> get_error_code 

 傳回造成例外狀況的錯誤碼。  
  
```
HRESULT get_error_code() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 `HRESULT`錯誤造成的例外狀況的值。  
  
##  <a name="ctor"></a> scheduler_resource_allocation_error 

 建構 `scheduler_resource_allocation_error` 物件。  
  
```
scheduler_resource_allocation_error(
    _In_z_ const char* _Message,
    HRESULT _Hresult) throw();

explicit _CRTIMP scheduler_resource_allocation_error(
    HRESULT _Hresult) throw();
```  
  
### <a name="parameters"></a>參數  
 `_Message`  
 錯誤的描述性訊息。  
  
 `_Hresult`  
 `HRESULT`錯誤造成的例外狀況的值。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)
