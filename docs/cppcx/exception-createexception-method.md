---
title: "Exception::CreateException 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Exception::CreateException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Exception::CreateException 方法"
ms.assetid: 70e72bb4-3fec-478d-af3d-9ec8762d2825
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Exception::CreateException 方法
從指定的 HRESULT 值建立 Platform::Exception^。  
  
## 語法  
  
```cpp  
Exception^ CreateException(int32 hr)  
Exception^ CreateException(int32 hr, Platform::String^ message)  
```  
  
## 參數  
 hr  
 HRESULT 值，通常從 COM 方法的呼叫中取得。 如果值為 0 \(等於 S\_OK\)，這個方法會擲回 [Platform::InvalidArgumentException](../cppcx/platform-invalidargumentexception-class.md)，因為成功的 COM 方法不可擲回例外狀況。  
  
 訊息  
 描述錯誤的字串。  
  
## 傳回值  
 表示錯誤 HRESULT 的例外狀況。  
  
## 備註  
 使用這個方法，從傳回的 HRESULT \(例如從 COM 介面方法的呼叫中取得\) 建立例外狀況。 您可以使用可接受 String^ 參數的多載，提供自訂訊息。  
  
 強烈建議使用 CreateException 建立強型別的例外狀況，而不建立只包含 HRESULT 的 [Platform::COMException](../cppcx/platform-comexception-class.md)。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **中繼資料：**platform.winmd  
  
## 請參閱  
 [Platform 命名空間](../cppcx/platform-namespace-c-cx.md)