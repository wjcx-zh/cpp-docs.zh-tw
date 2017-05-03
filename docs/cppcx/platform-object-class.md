---
title: "Platform::Object 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Object"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Object 類別"
ms.assetid: 709e84a8-0bff-471b-bc14-63e424080b5a
caps.latest.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 9
---
# Platform::Object 類別
為 Windows 市集應用程式中的 ref 類別或 ref 結構提供一般行為。 所有 ref 類別和 ref 結構執行個體都會隱含轉換為 Platform::Object^，而且也都能覆寫其虛擬 ToString 方法。  
  
## 語法  
  
```scr  
public ref class Object : Object  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[Object::Object 建構函式](../cppcx/object-object-constructor.md)|初始化 Object 類別的新執行個體。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[Object::Equals 方法](../cppcx/object-equals-method.md)|判斷指定的物件是否等於目前的物件。|  
|[Object::GetHashCode 方法](../cppcx/object-gethashcode-method.md)|傳回這個執行個體的雜湊碼。|  
|[Object::ReferenceEquals 方法](../cppcx/object-referenceequals-method.md)|判斷指定的物件執行個體是否為相同的執行個體。|  
|[ToString 方法](../cppcx/object-tostring-method-c-cx.md)|傳回代表目前物件的字串。 可以被覆寫。|  
|[GetType 方法](../cppcx/object-gettype-method.md)|取得可描述目前執行個體的 [Platform::Type](../cppcx/platform-type-class.md)。|  
  
## 繼承階層  
 `Object`  
  
 `Object`  
  
## 需求  
 **標頭：**vccorlib.h  
  
 **命名空間：**Platform  
  
## 請參閱  
 [\(NOTINBUILD\) Platform 命名空間](http://msdn.microsoft.com/zh-tw/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)