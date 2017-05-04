---
title: "String::IsFastPass 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String::IsFastPass"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::String::IsFastPass"
ms.assetid: 0a8c2db7-e44f-45fe-9570-3dc82fbbacdd
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# String::IsFastPass 方法
指出目前 String 物件是否參與「*快速傳遞*」\(Fast Pass\) 作業。 在快速傳遞作業時，參考計數會暫停。  
  
## 語法  
  
```cpp  
  
bool IsFastPass();  
```  
  
## 傳回值  
 如果目前 String 物件是快速傳遞則為 `true`，否則為 `false`。  
  
## 備註  
 在呼叫函式時如果參考計數的物件是參數，而被呼叫的函式只讀取該物件，則編譯器可以安全地暫停參考計數，改善呼叫效能。 您的程式碼不需要處理這個屬性， 系統會處理所有的細節。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **中繼資料：**vccorlib.h  
  
## 請參閱  
 [Platform::String 類別](../cppcx/platform-string-class.md)