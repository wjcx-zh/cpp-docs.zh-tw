---
title: "Platform::ChangedStateException 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::ChangedStateException"
  - "Platform/Platform::ChangedStateException::ChangedStateException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::ChangedStateException"
ms.assetid: f894beac-9e80-4fac-ac25-89f1dbc0a6a4
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# Platform::ChangedStateException 類別
當物件的內部狀態已經變更時擲回，藉以讓方法的結果失效。  
  
## 語法  
  
```cpp  
public ref class ChangedStateException : COMException,    IException,    IPrintable,    IEquatable  
```  
  
## 備註  
 擲回這個例外狀況的一個例子是，在父集合變更後呼叫集合迭代器或集合檢視的方法時，藉以讓方法的結果失效。  
  
 如需詳細資訊，請參閱 [COMException](../cppcx/platform-comexception-class.md) 類別。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **中繼資料：**platform.winmd  
  
## 請參閱  
 [Platform::COMException 類別](../cppcx/platform-comexception-class.md)