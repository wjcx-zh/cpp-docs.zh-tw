---
title: "Platform:: stathreadattribute 類別 |Microsoft 文件"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COLLECTION/Platform::Platform
- COLLECTION/Platform::Platform::STAThreadAttribute constructor 1
- COLLECTION/Platform::Platform::STAThreadAttribute::Equals
- COLLECTION/Platform::Platform::STAThreadAttribute::GetHashCode
- COLLECTION/Platform::Platform::STAThreadAttribute::ToString
dev_langs: C++
helpviewer_keywords: Platform::STAThreadAttribute Class
ms.assetid: f97960fc-e673-4d9e-910a-54c8415411c4
caps.latest.revision: "3"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b1c2b8c38d672b6bd3ecd0fcafb54a9b6e723202
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="platformstathreadattribute-class"></a>Platform::STAThreadAttribute 類別
指出應用程式的執行緒模型為單一執行緒 Apartment (STA)。  
  
## <a name="syntax"></a>語法  
  
```  
public ref class STAThreadAttribute sealed : Attribute  
```  
  
### <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[STAThreadAttribute 建構函式 1](#ctor)|初始化類別的新執行個體。|  
  
### <a name="public-methods"></a>公用方法  
 STAThreadAttribute 屬性繼承自[platform:: object 類別](../cppcx/platform-object-class.md)。 STAThreadAttribute 也會多載或具有下列成員：  
  
|名稱|描述|  
|----------|-----------------|  
|[STAThreadAttribute::Equals](#equals)|判斷指定的物件是否等於目前的物件。|  
|[STAThreadAttribute::GetHashCode](#gethashcode)|傳回這個執行個體的雜湊碼。|  
|[STAThreadAttribute::ToString](#tostring)|傳回代表目前物件的字串。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `Platform`  
  
### <a name="requirements"></a>需求  
 **標頭：** collection.h  
  
 **命名空間：** Platform  



## <a name="ctor"></a> STAThreadAttribute constructor
初始化 STAThreadAttribute 類別的新執行個體。  
  
### <a name="syntax"></a>語法  
  
```cpp  
public:STAThreadAttribute()  
```  
  


## <a name="equals"></a>STAThreadAttribute::Equals
判斷指定的物件是否等於目前的物件。  
  
### <a name="syntax"></a>語法  
  
```cpp  
public:virtual override bool Equals(  Object^ obj)  
```  
  
### <a name="parameters"></a>參數  
 obj  
 要比較的物件。  
  
### <a name="return-value"></a>傳回值  
 如果物件相等則為 `true`，否則為 `false`。  
  


## <a name="gethashcode"></a>STAThreadAttribute::GetHashCode
傳回這個執行個體的雜湊碼。  
  
### <a name="syntax"></a>語法  
  
```cpp  
public:int GetHashCode()  
```  
  
### <a name="return-value"></a>傳回值  
 這個執行個體的雜湊碼。  
  


## <a name="tostring"></a>STAThreadAttribute::ToString
傳回代表目前物件的字串。  
  
### <a name="syntax"></a>語法  
  
```cpp  
public:String^ ToString()  
```  
  
### <a name="return-value"></a>傳回值  
 表示目前物件的字串。  
  

  
## <a name="see-also"></a>請參閱  
 [Platform 命名空間](platform-namespace-c-cx.md)