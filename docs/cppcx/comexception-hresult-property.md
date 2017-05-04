---
title: "COMException::HResult 屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::COMException::HResult"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COMException::HResult 屬性"
ms.assetid: 53762ab5-ce71-4397-b7b4-8175741c838f
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# COMException::HResult 屬性
對應於例外狀況的 HRESULT。  
  
## 語法  
  
```cpp  
public:property int HResult {    int get();}  
```  
  
## 屬性值  
 指定錯誤的 HRESULT 值。  
  
## 備註  
 如需如何解譯 HRESULT 值的詳細資訊，請參閱 [COM 錯誤碼的結構](http://go.microsoft.com/fwlink/p/?LinkId=262045)。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **標頭：**vccorlib.h  
  
## 小節標題  
  
## 請參閱  
 [Platform::COMException 類別](../cppcx/platform-comexception-class.md)