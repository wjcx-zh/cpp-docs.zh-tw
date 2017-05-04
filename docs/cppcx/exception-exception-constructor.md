---
title: "Exception::Exception 建構函式 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Exception::Exception"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Exception::Exception 建構函式"
ms.assetid: 173b434e-e3a8-41f5-904e-0e8fc0f21950
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Exception::Exception 建構函式
初始化 Exception 類別的新執行個體。  
  
## 語法  
  
```cpp  
  
Exception(int32 hresult)  
Exception(int32 hresult, ::Platform::String^ message)  
```  
  
#### 參數  
 `hresult`  
 由例外狀況表示的錯誤 HRESULT。  
  
 `message`  
 使用者指定的訊息 \(例如規範文字\)，與例外狀況關聯。 通常您應該最好使用第二個多載，以提供有關發生錯誤的情形和原因、盡可能詳細的描述性訊息。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **中繼資料：**platform.winmd  
  
## 請參閱  
 [Platform 命名空間](../cppcx/platform-namespace-c-cx.md)