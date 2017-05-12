---
title: "Platform::WrongThreadException 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::WrongThreadException"
  - "Platform/Platform::WrongThreadException::WrongThreadException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::WrongThreadException"
ms.assetid: c193f97e-0392-4535-a4c4-0711e4e4a836
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 5
---
# Platform::WrongThreadException 類別
當執行緒透過不屬於執行緒 Apartment 的 Proxy 物件的介面指標來呼叫時擲回。  
  
## 語法  
  
```cpp  
public ref class WrongThreadException : COMException,    IException,    IPrintable,    IEquatable  
```  
  
## 備註  
 如需詳細資訊，請參閱 [COMException](../cppcx/platform-comexception-class.md)。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **中繼資料：**platform.winmd  
  
## 請參閱  
 [Platform::COMException 類別](../cppcx/platform-comexception-class.md)