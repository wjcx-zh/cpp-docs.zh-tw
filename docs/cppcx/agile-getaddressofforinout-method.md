---
title: "Agile::GetAddressOfForInOut 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "agile/Platform::Agile::GetAddressOfForInOut"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Agile::GetAddressOfForInOut"
ms.assetid: 8bb27b4c-c325-49ee-91db-9adf87c530c4
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Agile::GetAddressOfForInOut 方法
傳回目前 Agile 物件所代表的物件的控制代碼位址。  
  
## 語法  
  
```cpp  
  
       T^* GetAddressOfForInOut()   
throw();  
  
```  
  
#### 參數  
 `T`  
 樣板 typename 參數指定的類型。  
  
## 傳回值  
 目前 Agile 物件所代表的物件的控制代碼位址。  
  
## 備註  
 這個作業取得目前執行緒的內容，然後傳回基礎物件的控制代碼位址。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **標頭：**vccorlib.h  
  
## 請參閱  
 [Platform::Agile 類別](../cppcx/platform-agile-class.md)