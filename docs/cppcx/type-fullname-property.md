---
title: "Type::FullName 屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Type::get_FullName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Type::get_FullName 屬性"
ms.assetid: b5a12d8f-4404-4659-b4af-e7d23a1e44b7
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Type::FullName 屬性
以 "Namespace.Type" 的格式取得目前類型的完整名稱。  
  
## 語法  
  
```cpp  
String^ FullName();  
```  
  
## 傳回值  
 型別的名稱。  
  
## 範例  
  
```  
  
//  namespace is TestApp MainPage::MainPage() { InitializeComponent(); Type^ t = this->GetType(); auto s = t->FullName; // returns “TestApp.MainPage” auto s2 = t->ToString(); //also returns “TestApp.MainPage” }  
```  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **中繼資料：**platform.winmd  
  
## 請參閱  
 [Platform::ValueType 類別](../cppcx/platform-valuetype-class.md)