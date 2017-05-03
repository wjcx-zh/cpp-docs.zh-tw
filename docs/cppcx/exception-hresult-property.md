---
title: "Exception::HResult 屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Exception::HResult"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Exception::HResult 屬性"
ms.assetid: 24ef008d-6884-4b8b-9556-41bfa6e1edf1
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Exception::HResult 屬性
對應於例外狀況的 HRESULT。  
  
## 語法  
  
```cpp  
public:property int HResult {    int get();}  
```  
  
## 屬性值  
 HRESULT 值。  
  
## 備註  
 大部分的例外狀況都是以 HRESULT 值傳回的 COM 錯誤開始。 C\+\+\/CX 會將這些值轉換為 Platform::Exception^ 物件，這個屬性儲存原始錯誤碼的值。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **中繼資料：**platform.winmd  
  
## 請參閱  
 [Platform::Exception 類別](../cppcx/platform-exception-class.md)