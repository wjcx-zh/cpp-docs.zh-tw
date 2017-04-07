---
title: "accelerator_view_removed 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- accelerator_view_removed
- AMPRT/accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed:accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed:get_view_removed_reason
dev_langs:
- C++
helpviewer_keywords:
- AMPRT/Concurrency::accelerator_view_removed:accelerator_view_removed Class
ms.assetid: 262446de-311c-454e-a5ed-e2aaced0d88a
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: c45eb8192266999c8771f6788de16859fe7a12c8
ms.lasthandoff: 03/17/2017

---
# <a name="acceleratorviewremoved-class"></a>accelerator_view_removed 類別
由於 Windows 逾時偵測與復原機制的基礎的 DirectX 呼叫失敗時擲回例外狀況。  
  
## <a name="syntax"></a>語法  
  
```  
class accelerator_view_removed : public runtime_exception;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[accelerator_view_removed 建構函式](#ctor)|初始化 `accelerator_view_removed` 類別的新執行個體。|  

### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[get_view_removed_reason](#get_view_removed_reason)|傳回指出原因的 HRESULT 錯誤碼`accelerator_view`物件移除。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `exception`  
  
 `runtime_exception`  
  
 `out_of_memory`  
  
## <a name="requirements"></a>需求  
 **標頭︰** amprt.h  
  
 **命名空間：** 並行  

## <a name="ctor"></a>accelerator_view_removed 

初始化的新執行個體[accelerator_view_removed](accelerator-view-removed-class.md)類別。  
  
### <a name="syntax"></a>語法  
  
```  
explicit accelerator_view_removed(  
    const char * _Message,  
    HRESULT _View_removed_reason ) throw();  
  
explicit accelerator_view_removed(  
    HRESULT _View_removed_reason ) throw();  
```  
  
### <a name="parameters"></a>參數  
 `_Message`  
 錯誤的描述。  
  
 `_View_removed_reason`  
 指出原因的移除 HRESULT 錯誤碼`accelerator_view`物件。  
  
### <a name="return-value"></a>傳回值  
 Accelerator_view_removed 類別的新執行個體。  
  
## <a name="get_view_removed_reason_method"></a>get_view_removed_reason 

傳回指出原因的 HRESULT 錯誤碼`accelerator_view`物件移除。  
  
### <a name="syntax"></a>語法  
  
```  
HRESULT get_view_removed_reason() const throw();  
```  
  
 
## <a name="see-also"></a>另請參閱  
 [Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)

