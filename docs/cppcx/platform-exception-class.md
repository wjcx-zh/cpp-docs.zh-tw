---
title: "Platform::Exception 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Exception"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Exception 類別"
ms.assetid: ca1d5a67-3a5a-48fe-8099-f9c38a2d2dce
caps.latest.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 6
---
# Platform::Exception 類別
代表應用程式執行期間所發生的錯誤。 自訂例外狀況類別不能衍生自 `Platform::Exception` 類別。 如果您需要自訂例外狀況，您可以使用 `Platform::COMException` 並指定應用程式特定的 HRESULT。  
  
## 語法  
  
```cpp  
public ref class Exception : Object,    IException,    IPrintable,    IEquatable  
```  
  
## Members  
 `Exception` 類別繼承自 `Object` 類別及 `IException`、`IPrintable` 和 `IEquatable` 介面。  
  
 `Exception` 類別也有下列幾種成員。  
  
### 建構函式  
  
|成員|描述|  
|--------|--------|  
|[Exception::Exception 建構函式](../cppcx/exception-exception-constructor.md)|初始化 `Exception` 類別的新執行個體。|  
  
### 方法  
 `Exception` 類別繼承 `Equals()` 的 `Finalize()`、`GetHashCode()`、`GetType()`、`MemberwiseClose()`、`ToString()` 和 [Platform::Object 類別](../cppcx/platform-object-class.md) 方法。`Exception` 類別也有下列方法。  
  
|成員|描述|  
|--------|--------|  
|[Exception::CreateException 方法](../cppcx/exception-createexception-method.md)|建立表示指定 HRESULT 值的例外狀況。|  
  
### 屬性  
 Exception 類別也有下列屬性。  
  
|成員|描述|  
|--------|--------|  
|[Exception::HResult 屬性](../cppcx/exception-hresult-property.md)|對應於例外狀況的 HRESULT。|  
|[Exception::Message 屬性](../cppcx/exception-message-property.md)|描述例外狀況的訊息。 此值是唯讀，在 `Exception` 建構之後就無法修改。|  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **中繼資料：**platform.winmd  
  
## 請參閱  
 [Platform 命名空間](../cppcx/platform-namespace-c-cx.md)