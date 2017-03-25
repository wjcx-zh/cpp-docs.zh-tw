---
title: "runtime_exception 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
ms.openlocfilehash: 399d2531c06285012df12d703b4cda6e18469c38
ms.lasthandoff: 03/17/2017

---
# <a name="runtimeexception-class"></a>runtime_exception 類別
C + + Accelerated Massive 平行處理原則 (AMP) 程式庫中的例外狀況的基底類型。  
  
### <a name="syntax"></a>語法  
  
```  
class runtime_exception : public std::exception;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
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
|[operator=](#operator_eq)|將指定的內容複製`runtime_exception`到這裡的物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `exception`  
  
 `runtime_exception`  
  
## <a name="requirements"></a>需求  
 **標頭︰** amprt.h  
  
 **命名空間：** 並行  

## <a name="runtime_exception__ctor"></a>runtime_exception 建構函式  
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
 造成例外狀況之錯誤的 HRESULT。  
  
 `_Other`  
 `runtime_exception`来複製物件。  
  
### <a name="return-value"></a>傳回值  
 `runtime_exception` 物件。  

## <a name="dtor"></a>~ runtime_exception 解構函式  
終結物件。  
  
### <a name="syntax"></a>語法  
  
```  
virtual ~runtime_exception() throw();  
```  
  
## <a name="runtime_exception__get_error_code"></a>get_error_code   
傳回造成例外狀況的錯誤碼。  
  
### <a name="syntax"></a>語法  
  
```  
HRESULT get_error_code() const throw();  
```  
  
### <a name="return-value"></a>傳回值  
 造成例外狀況之錯誤的 HRESULT。  
  
## <a name="runtime_exception__operator_eq"></a>  operator=   
  將指定的內容複製`runtime_exception`到這裡的物件。  
  
### <a name="syntax"></a>語法  
  
```  
runtime_exception & operator= (    const runtime_exception & _Other ) throw();  
```  
  
### <a name="parameters"></a>參數  
 `_Other`  
 `runtime_exception`来複製物件。  
  
### <a name="return-value"></a>傳回值  
 參考`runtime_exception`物件。  
  

  
## <a name="see-also"></a>另請參閱  
 [Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)

