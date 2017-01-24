---
title: "CUrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CUrl"
  - "CUrl"
  - "ATL::CUrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CUrl class"
ms.assetid: b3894d34-47b9-4961-9719-4197153793da
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CUrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別表示 URL。  它是否可以讓您獨立作業 URL 的每個項目會剖析現有的 URL 字串或從頭建置字串。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
class CUrl  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CUrl::CUrl](../Topic/CUrl::CUrl.md)|建構函式。|  
|[CUrl::~CUrl](../Topic/CUrl::~CUrl.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CUrl::Canonicalize](../Topic/CUrl::Canonicalize.md)|呼叫這個方法會將 URL 字串至標準格式。|  
|[CUrl::Clear](../Topic/CUrl::Clear.md)|呼叫這個方法會清除所有的 URL。|  
|[CUrl::CrackUrl](../Topic/CUrl::CrackUrl.md)|呼叫這個方法會解碼並解析 URL。|  
|[CUrl::CreateUrl](../Topic/CUrl::CreateUrl.md)|呼叫這個方法會建立 URL。|  
|[CUrl::GetExtraInfo](../Topic/CUrl::GetExtraInfo.md)|呼叫這個方法會取得額外資訊 \(例如?*文字* 或 \#text\) 從 URL。|  
|[CUrl::GetExtraInfoLength](../Topic/CUrl::GetExtraInfoLength.md)|呼叫這個方法會取得額外資訊的長度 \(例如? \) 擷取的*文字* 或 \#text 從 URL。|  
|[CUrl::GetHostName](../Topic/CUrl::GetHostName.md)|呼叫這個方法會從 URL 取得主機名稱。|  
|[CUrl::GetHostNameLength](../Topic/CUrl::GetHostNameLength.md)|呼叫這個方法會取得主機名稱的長度。|  
|[CUrl::GetPassword](../Topic/CUrl::GetPassword.md)|呼叫這個方法會從 URL 取得密碼。|  
|[CUrl::GetPasswordLength](../Topic/CUrl::GetPasswordLength.md)|呼叫這個方法會取得密碼的長度。|  
|[CUrl::GetPortNumber](../Topic/CUrl::GetPortNumber.md)|呼叫這個方法會取得通訊埠編號是以 ATL\_URL\_PORT。|  
|[CUrl::GetScheme](../Topic/CUrl::GetScheme.md)|呼叫這個方法會取得 URL 計劃。|  
|[CUrl::GetSchemeName](../Topic/CUrl::GetSchemeName.md)|呼叫這個方法會取得 URL 配置名稱。|  
|[CUrl::GetSchemeNameLength](../Topic/CUrl::GetSchemeNameLength.md)|呼叫這個方法會取得 URL 配置名稱的長度。|  
|[CUrl::GetUrlLength](../Topic/CUrl::GetUrlLength.md)|呼叫這個方法會取得 URL 長度。|  
|[CUrl::GetUrlPath](../Topic/CUrl::GetUrlPath.md)|呼叫這個方法會取得 URL 路徑。|  
|[CUrl::GetUrlPathLength](../Topic/CUrl::GetUrlPathLength.md)|呼叫這個方法會取得 URL 路徑長度。|  
|[CUrl::GetUserName](../Topic/CUrl::GetUserName.md)|呼叫這個方法會從 URL 取得使用者名稱。|  
|[CUrl::GetUserNameLength](../Topic/CUrl::GetUserNameLength.md)|呼叫這個方法會取得使用者名稱的長度。|  
|[CUrl::SetExtraInfo](../Topic/CUrl::SetExtraInfo.md)|呼叫這個方法會將額外資訊 \(例如?*文字* 或 \#text\) URL。|  
|[CUrl::SetHostName](../Topic/CUrl::SetHostName.md)|呼叫這個方法會設定主機名稱。|  
|[CUrl::SetPassword](../Topic/CUrl::SetPassword.md)|呼叫這個方法會設定密碼。|  
|[CUrl::SetPortNumber](../Topic/CUrl::SetPortNumber.md)|呼叫這個方法會設定通訊埠編號是以 ATL\_URL\_PORT。|  
|[CUrl::SetScheme](../Topic/CUrl::SetScheme.md)|呼叫這個方法會設定 URL 計劃。|  
|[CUrl::SetSchemeName](../Topic/CUrl::SetSchemeName.md)|呼叫這個方法會設定 URL 配置名稱。|  
|[CUrl::SetUrlPath](../Topic/CUrl::SetUrlPath.md)|呼叫這個方法會設定 URL 路徑。|  
|[CUrl::SetUserName](../Topic/CUrl::SetUserName.md)|呼叫這個方法會設定使用者名稱。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CUrl::operator \=](../Topic/CUrl::operator%20=.md)|指派給目前 `CUrl` 物件中指定的 `CUrl` 物件。|  
  
## 備註  
 `CUrl` 允許您操作之 URL 的欄位，例如路徑或通訊埠編號。  `CUrl` 了解下列格式的 URL:  
  
 \<Scheme\>:\<UserName\>\/:\<Password\>@\<HostName\>:\<PortNumber\>\/\<UrlPath\>\<ExtraInfo\>  
  
 \(某些欄位是選擇性的\)。例如，請考慮下列 URL:  
  
 http:\/\/someone:secret@www.microsoft.com:80\/visualc\/stuff.htm\#contents  
  
 [CUrl::CrackUrl](../Topic/CUrl::CrackUrl.md) 解決如下所示:  
  
-   計劃:「http」或 [ATL\_URL\_SCHEME\_HTTP](../Topic/ATL_URL_SCHEME.md)  
  
-   使用者名稱:「有」  
  
-   密碼:「密碼」  
  
-   主機名稱:「www.microsoft.com」  
  
-   PortNumber:80  
  
-   UrlPath:「visualc\/stuff.htm」  
  
-   ExtraInfo:「\#contents」  
  
 若要管理 UrlPath 欄位 \(例如\)，您可以使用 [GetUrlPath](../Topic/CUrl::GetUrlPath.md)、 [GetUrlPathLength](../Topic/CUrl::GetUrlPathLength.md)和 [SetUrlPath](../Topic/CUrl::SetUrlPath.md)。  您可以使用 [CreateUrl](../Topic/CUrl::CreateUrl.md) 建立完整的 URL 字串。  
  
## 需求  
 **Header:** 函式  
  
## 請參閱  
 [類別](../../atl/reference/atl-classes.md)