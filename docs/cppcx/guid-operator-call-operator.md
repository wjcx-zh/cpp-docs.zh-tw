---
title: "Guid::operator() 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Guid::operator()"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Guid::operator()"
  - "平台, Guid::operator()"
ms.assetid: 5df51e6a-11c0-414c-8613-06b45a952828
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Guid::operator() 運算子
隱含地將 [GUID 結構](http://msdn.microsoft.com/library/windows/desktop/aa373931\(v=vs.85\).aspx) GUID 轉換為 Platform::Guid。  
  
## 語法  
  
```cpp  
Platform::Guid operator()  
```  
  
## 傳回值  
 Guid 結構。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **中繼資料：**platform.winmd  
  
## 請參閱  
 [Platform::Guid 實值類別](../cppcx/platform-guid-value-class.md)