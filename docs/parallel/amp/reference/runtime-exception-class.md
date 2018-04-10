---
title: runtime_exception 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- runtime_exception
- AMPRT/runtime_exception
- AMPRT/Concurrency::runtime_exception
- AMPRT/Concurrency::runtime_exception::get_error_code
dev_langs:
- C++
helpviewer_keywords:
- runtime_exception class
ms.assetid: 8fe3ce2c-3d4c-4b9c-95e8-e592f37adefd
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 678f0a93577a6e30afbc5e0c6d83aca6b6a7bedc
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/10/2018
---
# <a name="runtimeexception-class"></a>runtime_exception 類別
C + + Accelerated Massive Parallelism (AMP) 程式庫中的例外狀況的基底類型。  
  
### <a name="syntax"></a>語法  
  
```  
class runtime_exception : public std::exception;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[runtime_exception 建構函式](#ctor)|初始化 `runtime_exception` 類別的新執行個體。|  
|[~ runtime_exception 解構函式](#dtor)|終結`runtime_exception`物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[get_error_code](#runtime_exception__get_error_code)|傳回造成例外狀況的錯誤碼。|  

  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[operator=](#operator_eq)|將指定的內容複製`runtime_exception`成這一個物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `exception`  
  
 `runtime_exception`  
  
## <a name="requirements"></a>需求  
 **標頭：** amprt.h  
  
 **命名空間：** 並行  

## <a name="runtime_exception__ctor"></a>  runtime_exception 建構函式  
初始化類別的新執行個體。  
  
### <a name="syntax"></a>語法  
  
```  
runtime_exception(  
    const char * _Message,  
    HRESULT _Hresult ) throw();  
  
explicit runtime_exception(  
    HRESULT _Hresult ) throw();  
  
runtime_exception(  
    const runtime_exception & _Other ) throw();  
```  
  
### <a name="parameters"></a>參數  
 `_Message`  
 造成例外狀況之錯誤的描述。  
  
 `_Hresult`  
 造成例外狀況的錯誤的 HRESULT。  
  
 `_Other`  
 `runtime_exception`来複製物件。  
  
### <a name="return-value"></a>傳回值  
 `runtime_exception` 物件。  

## <a name="dtor"></a>  ~runtime_exception Destructor  
物件已遭終結。  
  
### <a name="syntax"></a>語法  
  
```  
virtual ~runtime_exception() throw();  
```  
  
## <a name="runtime_exception__get_error_code"></a>  get_error_code   
傳回造成例外狀況的錯誤碼。  
  
### <a name="syntax"></a>語法  
  
```  
HRESULT get_error_code() const throw();  
```  
  
### <a name="return-value"></a>傳回值  
 造成例外狀況的錯誤的 HRESULT。  
  
## <a name="runtime_exception__operator_eq"></a>  operator=   
  將指定的內容複製`runtime_exception`成這一個物件。  
  
### <a name="syntax"></a>語法  
  
```  
runtime_exception & operator= (    const runtime_exception & _Other ) throw();  
```  
  
### <a name="parameters"></a>參數  
 `_Other`  
 `runtime_exception`来複製物件。  
  
### <a name="return-value"></a>傳回值  
 此參考`runtime_exception`物件。  
  

  
## <a name="see-also"></a>另請參閱  
 [Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
