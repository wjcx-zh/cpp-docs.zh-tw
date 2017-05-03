---
title: "Object::GetHashCode 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Object::GetHashCode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform, Object::GetHashCode"
ms.assetid: 403a60e9-be1d-4702-b14d-27fa4b2a043b
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Object::GetHashCode 方法
傳回這個執行個體的 [IUnknown](../atl/iunknown.md)\* 識別值 \(如果它是 COM 物件\)，或計算的雜湊值 \(如果它不是 COM 物件\)。  
  
## 語法  
  
```cpp  
public:int GetHashCode()  
```  
  
## 傳回值  
 可唯一識別這個物件的數值。  
  
## 備註  
 您可以使用 GetHashCode，在對應中建立物件的索引鍵。 您可以使用 [Object::Equals 方法](../cppcx/object-equals-method.md) 來比較雜湊碼。 如果程式碼路徑非常重要，而且 `GetHashCode` 和 `Equals` 不夠快，您可以下拉到基礎 COM 層，並且進行原生 [IUnknown](../atl/iunknown.md) 指標比較。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **標頭：**vccorlib.h  
  
## 請參閱  
 [Platform::Object 類別](../cppcx/platform-object-class.md)