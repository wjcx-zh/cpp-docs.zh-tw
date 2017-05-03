---
title: "Platform::Guid 實值類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Guid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Guid 結構"
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
caps.latest.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 6
---
# Platform::Guid 實值類別
代表 Windows 執行階段類型系統中的 [GUID](http://msdn.microsoft.com/library/windows/desktop/aa373931\(v=vs.85\).aspx) 類型。  
  
## 語法  
  
```cpp  
public value struct Guid  
```  
  
## 成員  
 GUID 具有 Equals\(\)、GetHashCode\(\) 和 ToString\(\) 方法 \(衍生自[Platform::Object 類別](../cppcx/platform-object-class.md)\)，以及 GetTypeCode\(\) 方法 \(衍生自[Platform::Type 類別](../cppcx/platform-type-class.md). Guid 也具有下列成員。  
  
|成員|描述|  
|--------|--------|  
|Guid|初始化 Guid 結構的新執行個體。|  
|operator\=\=|等於運算子。|  
|operator\!\=|不等於運算子。|  
|operator\(\)|將 Guid 轉換成 GUID。|  
  
## 備註  
 如需如何使用 Windows 函式 [CoCreateGuid](http://msdn.microsoft.com/library/windows/desktop/ms688568\(v=vs.85\).aspx) 產生新 Platform::Guid 的範例，請參閱[WinRT 元件：如何產生 GUID？](http://blogs.msdn.com/b/eternalcoding/archive/2013/03/25/winrt-component-how-to-generate-a-guid.aspx) \(英文\)  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **中繼資料：**platform.winmd  
  
## 請參閱  
 [Platform 命名空間](../cppcx/platform-namespace-c-cx.md)