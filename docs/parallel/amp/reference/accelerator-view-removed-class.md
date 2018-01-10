---
title: "accelerator_view_removed 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- accelerator_view_removed
- AMPRT/accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed:accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed:get_view_removed_reason
dev_langs: C++
helpviewer_keywords: AMPRT/Concurrency::accelerator_view_removed:accelerator_view_removed Class
ms.assetid: 262446de-311c-454e-a5ed-e2aaced0d88a
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 68b770acd41956ec255718ee2e2db1c5ee556b9d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="acceleratorviewremoved-class"></a>accelerator_view_removed 類別
由於 Windows 逾時偵測與復原機制的基礎的 DirectX 呼叫失敗時擲回例外狀況。  
  
## <a name="syntax"></a>語法  
  
```  
class accelerator_view_removed : public runtime_exception;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[accelerator_view_removed 建構函式](#ctor)|初始化 `accelerator_view_removed` 類別的新執行個體。|  

### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[get_view_removed_reason](#get_view_removed_reason)|傳回指出原因的 HRESULT 錯誤碼`accelerator_view`物件移除。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `exception`  
  
 `runtime_exception`  
  
 `out_of_memory`  
  
## <a name="requirements"></a>需求  
 **標頭：** amprt.h  
  
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
 表示移除的原因的 HRESULT 錯誤碼`accelerator_view`物件。  
  
### <a name="return-value"></a>傳回值  
 Accelerator_view_removed 類別的新執行個體。  
  
## <a name="get_view_removed_reason_method"></a>get_view_removed_reason 

傳回指出原因的 HRESULT 錯誤碼`accelerator_view`物件移除。  
  
### <a name="syntax"></a>語法  
  
```  
HRESULT get_view_removed_reason() const throw();  
```  
  
 
## <a name="see-also"></a>請參閱  
 [Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
