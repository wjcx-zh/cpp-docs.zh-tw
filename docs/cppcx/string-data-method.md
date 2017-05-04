---
title: "String::Data 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String::Data"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::String::Data"
ms.assetid: 9be4e015-dfb8-431e-a252-8498bd833f03
caps.latest.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# String::Data 方法
傳回物件資料緩衝區開頭的指標當做 `char16` \(`wchar_t`\) 元素的 C\-style 陣列。  
  
## 語法  
  
```  
const char16* Data()  
```  
  
## 傳回值  
 Unicode 字元的 `const``char16` 陣列開頭的指標 \(`char16` 是 `wchar_t` 的 typedef\)。  
  
## 備註  
 使用這個方法可從 `Platform::String^` 轉換為 `wchar_t*`。 當 `String` 物件超出範圍時，資料指標不再保證有效。 若要儲存超出原始 `String` 物件存留期的資料，請使用 [wcscpy\_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) 將陣列複製到您自行配置的記憶體中。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **中繼資料：**vccorlib.h  
  
## 請參閱  
 [Platform::String 類別](../cppcx/platform-string-class.md)   
 [String::Begin 方法](../cppcx/string-begin-method.md)