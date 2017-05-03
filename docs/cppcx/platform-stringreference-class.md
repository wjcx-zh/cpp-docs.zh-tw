---
title: "Platform::StringReference 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::StringReference"
dev_langs: 
  - "C++"
ms.assetid: 2d09c7ec-0f16-458e-83ed-7225a1b9221e
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# Platform::StringReference 類別
可以用來從 `Platform::String^` 輸入參數將字串資料傳遞給其他方法的最佳化類型，可將複製作業減至最少。  
  
## 語法  
  
```cpp  
class StringReference  
```  
  
## 備註  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[StringReference::StringReference 建構函式](../cppcx/stringreference-stringreference-constructor.md)|用來建立 `StringReference` 執行個體的兩個建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[StringReference::Data 方法](../cppcx/stringreference-data-method.md)|傳回字串資料當做 char16 值的陣列。|  
|[StringReference::Length 方法](../cppcx/stringreference-length-method.md)|傳回字串中的字元數。|  
|[StringReference::GetHSTRING 方法](../cppcx/stringreference-gethstring-method.md)|傳回字串資料當做 HSTRING。|  
|[StringReference::GetString 方法](../cppcx/stringreference-getstring-method.md)|傳回字串資料當做 `Platform::String^`。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|`StringReference::operator=`|將 `StringReference` 指定給新的 `StringReference` 執行個體。|  
|`StringReference::operator()`|將 `StringReference` 轉換成 `Platform::String^`。|  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **標頭：**vccorlib.h  
  
## 請參閱  
 [Platform::StringReference Class](../cppcx/platform-stringreference-class.md)