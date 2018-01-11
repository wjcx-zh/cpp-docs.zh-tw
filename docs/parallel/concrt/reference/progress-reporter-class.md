---
title: "progress_reporter 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- progress_reporter
- PPLTASKS/concurrency::progress_reporter
- PPLTASKS/concurrency::progress_reporter::progress_reporter
- PPLTASKS/concurrency::progress_reporter::report
dev_langs: C++
helpviewer_keywords: progress_reporter class
ms.assetid: b836efab-2d05-4649-b6fa-d15236f1f813
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1dcdba2e5242dcd750eea42b61575ebea921d7b6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="progressreporter-class"></a>progress_reporter 類別
進度報告程式類別允許報告特定類型的進度通知。 每個 progress_reporter 物件都會繫結至特定非同步動作或作業。  
  
## <a name="syntax"></a>語法  
  
```
template<typename _ProgressType>
class progress_reporter;
```  
  
#### <a name="parameters"></a>參數  
 `_ProgressType`  
 透過進度報告程式報告之每個進度通知的承載類型。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[progress_reporter](#ctor)||  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[報表](#report)|將進度報告傳送至這個進度報告程式所繫結的非同步動作或作業。|  
  
## <a name="remarks"></a>備註  
 這個類型只供 Windows 市集應用程式使用。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `progress_reporter`  
  
## <a name="requirements"></a>需求  
 **標頭：** ppltasks.h  
  
 **命名空間：** concurrency  
  
##  <a name="ctor"></a>progress_reporter 

```
progress_reporter();
```  
  
##  <a name="report"></a>報表 

 將進度報告傳送至這個進度報告程式所繫結的非同步動作或作業。  
  
```
void report(const _ProgressType& val) const;
```  
  
### <a name="parameters"></a>參數  
 `val`  
 透過進度通知的報表內容。  
  
## <a name="see-also"></a>請參閱  
 [concurrency 命名空間](concurrency-namespace.md)
