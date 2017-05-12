---
title: "Platform::Delegate 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Delegate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Delegate 類別"
ms.assetid: 82b21271-768f-4193-9ca2-be68ddfd546e
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 5
---
# Platform::Delegate 類別
表示函式物件。  
  
## 語法  
  
```cpp  
public delegate void delegate_name();  
```  
  
## 成員  
 委派類別具有衍生自 [Platform::Object 類別](../cppcx/platform-object-class.md) 的 Equals\(\)、GetHashCode\(\) 和 ToString\(\) 方法。  
  
## 備註  
 使用[委派](~/windows/delegate-cpp-component-extensions.md)關鍵字建立委派，請勿明確使用 Platform::Delegate。 如需詳細資訊，請參閱[委派](../cppcx/delegates-c-cx.md)。 如需如何建立和使用委派的範例，請參閱[在 C\+\+ 中建立 Windows 執行階段元件](http://msdn.microsoft.com/library/5b7251e6-4271-4f13-af80-c1cf5b1489bf)。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **中繼資料：**platform.winmd  
  
## 請參閱  
 [Platform 命名空間](../cppcx/platform-namespace-c-cx.md)