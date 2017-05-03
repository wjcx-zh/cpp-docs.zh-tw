---
title: "Platform::InvalidArgumentException 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::InvalidArgumentException"
  - "Platform/Platform::InvalidArgumentException::InvalidArgumentException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::InvalidArgumentException"
ms.assetid: 1a8d860b-3bcb-41a9-9346-6610616a0b46
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 3
---
# Platform::InvalidArgumentException 類別
當其中一個提供給方法的引數無效時擲回。  
  
## 語法  
  
```cpp  
public ref class InvalidArgumentException : COMException,    IException,    IPrintable,    IEquatable  
```  
  
## 備註  
 如需詳細資訊，請參閱 [COMException](../cppcx/platform-comexception-class.md) 類別。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **中繼資料：**platform.winmd  
  
## 請參閱  
 [Platform::COMException 類別](../cppcx/platform-comexception-class.md)