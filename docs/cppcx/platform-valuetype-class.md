---
title: "Platform::ValueType 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "02/03/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::ValueType"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::ValueType 類別"
ms.assetid: 79aa8754-b140-4974-a5b1-be046938a10a
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 2
---
# Platform::ValueType 類別
實值類型執行個體的基底類別。  
  
## 語法  
  
```cpp  
public ref class ValueType : Object  
```  
  
## 備註  
 ValueType 類別用以建構值類型。 具有基本成員的 ValueType 衍生自物件。 不過，編譯器會中斷基本成員和衍生自 ValueType 類別之值類型的連結。 當值類型經過方塊化處理後，編譯器會重新附加這些基本成員。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **中繼資料：**platform.winmd  
  
## 請參閱  
 [Platform 命名空間](../cppcx/platform-namespace-c-cx.md)