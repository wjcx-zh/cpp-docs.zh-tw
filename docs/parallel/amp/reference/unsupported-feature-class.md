---
title: "unsupported_feature 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amprt/Concurrency::unsupported_feature
dev_langs:
- C++
helpviewer_keywords:
- unsupported_feature class
ms.assetid: 6b1ab917-df13-48c7-9648-7cb2465a0ff5
caps.latest.revision: 12
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
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: 191678e0802696e7200945f96dc1f2bbd379cf57
ms.lasthandoff: 02/24/2017

---
# <a name="unsupportedfeature-class"></a>unsupported_feature 類別
使用不支援的功能時，會擲回例外狀況。  
  
## <a name="syntax"></a>語法  
  
```  
class unsupported_feature : public runtime_exception;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[unsupported_feature 建構函式](#ctor)|建構的新執行個體`unsupported_feature`例外狀況。|  

  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `exception`  
  
 `runtime_exception`  
  
 `unsupported_feature`  
  
## <a name="a-nameunsupportedfeaturectora-unsupportedfeature"></a><a name="unsupported_feature__ctor"></a>unsupported_feature 

  建構 unsupported_feature 例外狀況的新執行個體。  
  
### <a name="syntax"></a>語法  
  
```  
explicit unsupported_feature(  
    const char * _Message ) throw();  
  
unsupported_feature() throw();  
```  
  
### <a name="parameters"></a>參數  
 `_Message`  
 錯誤的描述。  
  
### <a name="return-value"></a>傳回值  
 `unsupported_feature` 物件。  
  
## <a name="requirements"></a>需求  
 **標頭︰** amprt.h  
  
 **命名空間：** 並行  
  
## <a name="see-also"></a>另請參閱  
 [Concurrency 命名空間 (c + + AMP)](concurrency-namespace-cpp-amp.md)

