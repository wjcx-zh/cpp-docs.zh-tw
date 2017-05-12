---
title: "Platform::AccessDeniedException 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::AccessDeniedException"
  - "Platform/Platform::AccessDeniedException::AccessDeniedException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::AccessDeniedException"
ms.assetid: 6ae2155b-7b16-4587-8d2d-da05eab4c7e9
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 5
---
# Platform::AccessDeniedException 類別
當存取資源或功能遭拒時擲回。  
  
## 語法  
  
```cpp  
public ref class AccessDeniedException : COMException,    IException,    IPrintable,   IEquatable  
```  
  
## 備註  
 如果您遇到此例外狀況，請確定您已要求適當的功能，並且已在應用程式的封裝資訊清單中執行必要的宣告。 如需詳細資訊，請參閱[使用資訊清單設計工具設定 Windows 8.1 應用程式套件](http://msdn.microsoft.com/library/24c58b7f-9c6d-41c3-b385-c1e8497d5b2d)與 [COMException](../cppcx/platform-comexception-class.md) 類別。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **中繼資料：**platform.winmd  
  
## 請參閱  
 [Platform::COMException 類別](../cppcx/platform-comexception-class.md)