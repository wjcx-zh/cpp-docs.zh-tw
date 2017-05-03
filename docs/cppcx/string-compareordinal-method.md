---
title: "String::CompareOrdinal 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String::CompareOrdinal"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::String::CompareOrdinal"
ms.assetid: dd4a7acc-fd23-4f1e-af85-64b9086f63f8
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# String::CompareOrdinal 方法
評估物件所代表之兩個字串值中的對應字元數值，藉以比較兩個 `String` 物件。  
  
## 語法  
  
```cpp  
  
int CompareOrdinal(  
           String^ str1,   
           String^ str2)  
  
```  
  
#### 參數  
 `str1`  
 第一個 String 物件。  
  
 `str2`  
 第二個 String 物件。  
  
## 傳回值  
 整數，表示兩個比較元 \(Comparand\) 之間的語彙關係。 下表列出可能的傳回值。  
  
|值|條件|  
|-------|--------|  
|\-1|`str1` 小於 `str2`。|  
|0|`str1` 等於 `str2`。|  
|1|`str1` 大於 `str2`。|  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **中繼資料：**vccorlib.h  
  
## 請參閱  
 [Platform::String 類別](../cppcx/platform-string-class.md)