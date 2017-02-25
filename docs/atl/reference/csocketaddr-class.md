---
title: "CSocketAddr Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSocketAddr"
  - "ATL.CSocketAddr"
  - "ATL::CSocketAddr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSocketAddr class"
ms.assetid: 2fb2d8a7-899e-4a36-a342-cc9f4fcdd68c
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CSocketAddr Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供轉換主機名稱提供方法讓主應用程式支援 IPv4 位址，以及 IPV6 格式。  
  
## 語法  
  
```  
  
class CSocketAddr  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CSocketAddr::CSocketAddr](../Topic/CSocketAddr::CSocketAddr.md)|建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CSocketAddr::FindAddr](../Topic/CSocketAddr::FindAddr.md)|呼叫這個方法會將提供的主機名稱加入至主機位址。|  
|[CSocketAddr::FindINET4Addr](../Topic/CSocketAddr::FindINET4Addr.md)|呼叫這個方法會轉換 IPv4 主機名稱加入至主機位址。|  
|[CSocketAddr::FindINET6Addr](../Topic/CSocketAddr::FindINET6Addr.md)|呼叫這個方法會轉換 IPv6 主機名稱加入至主機位址。|  
|[CSocketAddr::GetAddrInfo](../Topic/CSocketAddr::GetAddrInfo.md)|呼叫這個方法會傳回指標在 **addrinfo** 清單中的特定項目。|  
|[CSocketAddr::GetAddrInfoList](../Topic/CSocketAddr::GetAddrInfoList.md)|呼叫這個方法會傳回指標 **addrinfo** 清單。|  
  
## 備註  
 這個類別會提供搜尋網址為搭配 Windows Sockets API 函式和通訊端包裝函式提供一種 IP 版本無關的方法在程式庫中。  
  
 用來搜尋網址這個類別的成員使用 Win32 API 函式 [getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520)。  
  
 這個類別支援兩個 andIPv6 IPv4 位址。  
  
## 需求  
 **Header:** atlsocket.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)