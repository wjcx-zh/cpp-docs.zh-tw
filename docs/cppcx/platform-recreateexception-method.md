---
title: "Platform::ReCreateException 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::ReCreateException"
dev_langs: 
  - "C++"
ms.assetid: fa73d1ab-86e4-4d26-a7d9-81938c1c7e77
caps.latest.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# Platform::ReCreateException 方法
這個方法僅供內部使用，使用者程式碼並不需要。 請改用 [Exception::CreateException 方法](../cppcx/exception-createexception-method.md)。  
  
## 語法  
  
```vb  
static Exception^ ReCreateException(int hr)  
```  
  
#### 參數  
  
## 屬性值\/傳回值  
 根據指定的 HRESULT 傳回新的 Platform::Exception^。  
  
## .NET Framework 對等用法  
  
## 需求