---
title: runtime_exception 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ff10cb3958ffa82e3ef2bb70d8370d1a52c4a929
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695742"
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

## <a name="dtor"></a>  ~ runtime_exception 解構函式  
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
