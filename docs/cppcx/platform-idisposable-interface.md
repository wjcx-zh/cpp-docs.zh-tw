---
title: "Platform::IDisposable 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "02/03/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::IDisposable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::IDisposable 介面"
ms.assetid: f4344056-7030-42ed-bc98-b140edffddcd
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 2
---
# Platform::IDisposable 介面
用來釋放 Unmanaged 資源。  
  
## 語法  
  
```cpp  
public interface class IDisposable  
```  
  
## 屬性  
 **GuidAttribute**\("de0cbaea\-8065\-4a45\-b196\-c9d443f9bab3"\)  
  
 **VersionAttribute**\(NTDDI\_WIN8\)  
  
## Members  
 IDisposable 介面繼承自 IUnknown 介面。 IDisposable 也有下列類型的成員：  
  
 **方法**  
  
 IDisposable 介面具有下列方法。  
  
|方法|描述|  
|--------|--------|  
|Dispose \(超連結 "http:\/\/msdnpreview.redmond.corp.microsoft.com\/en\-us\/library\/windows\/apps\/platform.idisposable.dispose.aspx"\)|用來釋放 Unmanaged 資源。|  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform