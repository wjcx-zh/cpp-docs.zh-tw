---
title: "Type::GetTypeCode 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Type::GetTypeCode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Type::GetTypeCode 方法"
ms.assetid: 20c30432-91a3-400e-b9d6-eba265daaefc
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Type::GetTypeCode 方法
擷取內建類型數值類型類別目錄。  
  
## 語法  
  
```cpp  
Platform::TypeCode GetTypeCode();  
```  
  
## 傳回值  
 其中一個 Platform::TypeCode 列舉值。  
  
## 備註  
 GetTypeCode \(\) 成員方法相當於 `typeid` 屬性。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **中繼資料：**platform.winmd  
  
## 請參閱  
 [Platform::ValueType 類別](../cppcx/platform-valuetype-class.md)