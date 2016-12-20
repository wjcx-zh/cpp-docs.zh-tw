---
title: "CAccessToken Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATLSECURITY/CAccessToken"
  - "ATL.CAccessToken"
  - "CAccessToken"
  - "ATL::CAccessToken"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAccessToken class"
ms.assetid: bb5c5945-56a5-4083-b442-76573cee83ab
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAccessToken Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別是存取語彙基元的包裝函式。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
class CAccessToken  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAccessToken::~CAccessToken](../Topic/CAccessToken::~CAccessToken.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAccessToken::Attach](../Topic/CAccessToken::Attach.md)|呼叫這個方法會允許存取擁有權語彙基元控制代碼。|  
|[CAccessToken::CheckTokenMembership](../Topic/CAccessToken::CheckTokenMembership.md)|呼叫這個方法會判斷指定的 SID。 `CAccessToken` 物件啟用。|  
|[CAccessToken::CreateImpersonationToken](../Topic/CAccessToken::CreateImpersonationToken.md)|呼叫這個方法會建立新的模擬存取語彙基元。|  
|[CAccessToken::CreatePrimaryToken](../Topic/CAccessToken::CreatePrimaryToken.md)|呼叫這個方法會建立新的主要語彙基元。|  
|[CAccessToken::CreateProcessAsUser](../Topic/CAccessToken::CreateProcessAsUser.md)|呼叫這個方法會執行方式 `CAccessToken` 物件所表示的使用者安全性內容的處理序。|  
|[CAccessToken::CreateRestrictedToken](../Topic/CAccessToken::CreateRestrictedToken.md)|呼叫這個方法會建立新的， `CAccessToken` 限制的物件。|  
|[CAccessToken::Detach](../Topic/CAccessToken::Detach.md)|呼叫這個方法會移除存取語彙基元的擁有權。|  
|[CAccessToken::DisablePrivilege](../Topic/CAccessToken::DisablePrivilege.md)|呼叫這個方法會停用 `CAccessToken` 物件的一個使用權限。|  
|[CAccessToken::DisablePrivileges](../Topic/CAccessToken::DisablePrivileges.md)|呼叫這個方法會停用 `CAccessToken` 物件的一或多個權限。|  
|[CAccessToken::EnablePrivilege](../Topic/CAccessToken::EnablePrivilege.md)|呼叫這個方法會啟用 `CAccessToken` 物件的一個使用權限。|  
|[CAccessToken::EnablePrivileges](../Topic/CAccessToken::EnablePrivileges.md)|呼叫這個方法會啟用 `CAccessToken` 物件的一或多個權限。|  
|[CAccessToken::GetDefaultDacl](../Topic/CAccessToken::GetDefaultDacl.md)|呼叫這個方法會傳回物件的預設 `CAccessToken` DACL。|  
|[CAccessToken::GetEffectiveToken](../Topic/CAccessToken::GetEffectiveToken.md)|呼叫這個方法實際上取得 `CAccessToken` 物件等於存取語彙基元目前執行緒的。|  
|[CAccessToken::GetGroups](../Topic/CAccessToken::GetGroups.md)|呼叫這個方法會傳回物件的 `CAccessToken` 語彙基元群組。|  
|[CAccessToken::GetHandle](../Topic/CAccessToken::GetHandle.md)|呼叫這個方法會擷取控制代碼存取語彙基元。|  
|[CAccessToken::GetImpersonationLevel](../Topic/CAccessToken::GetImpersonationLevel.md)|呼叫這個方法會取得存取語彙基元模擬等級。|  
|[CAccessToken::GetLogonSessionId](../Topic/CAccessToken::GetLogonSessionId.md)|呼叫這個方法會取得登入工作階段 ID 與 `CAccessToken` 物件。|  
|[CAccessToken::GetLogonSid](../Topic/CAccessToken::GetLogonSid.md)|呼叫這個方法會取得登入 SID 與 `CAccessToken` 物件。|  
|[CAccessToken::GetOwner](../Topic/CAccessToken::GetOwner.md)|呼叫這個方法會取得擁有者與 `CAccessToken` 物件。|  
|[CAccessToken::GetPrimaryGroup](../Topic/CAccessToken::GetPrimaryGroup.md)|呼叫這個方法會取得主要群組與 `CAccessToken` 物件。|  
|[CAccessToken::GetPrivileges](../Topic/CAccessToken::GetPrivileges.md)|呼叫這個方法會取得權限與 `CAccessToken` 物件。|  
|[CAccessToken::GetProcessToken](../Topic/CAccessToken::GetProcessToken.md)|呼叫這個方法會初始化具有存取語彙基元的 `CAccessToken` 從指定的處理序。|  
|[CAccessToken::GetProfile](../Topic/CAccessToken::GetProfile.md)|呼叫這個方法會取得指向使用者設定檔的控制代碼與 `CAccessToken` 物件。|  
|[CAccessToken::GetSource](../Topic/CAccessToken::GetSource.md)|呼叫這個方法會取得 `CAccessToken` 物件的來源。|  
|[CAccessToken::GetStatistics](../Topic/CAccessToken::GetStatistics.md)|呼叫這個方法會取得資訊與 `CAccessToken` 物件。|  
|[CAccessToken::GetTerminalServicesSessionId](../Topic/CAccessToken::GetTerminalServicesSessionId.md)|呼叫這個方法會取得終端機服務工作階段 ID 與 `CAccessToken` 物件。|  
|[CAccessToken::GetThreadToken](../Topic/CAccessToken::GetThreadToken.md)|呼叫這個方法會使用語彙基元的 `CAccessToken` 從指定的執行緒。|  
|[CAccessToken::GetTokenId](../Topic/CAccessToken::GetTokenId.md)|呼叫這個方法會取得語彙基元 ID 與 `CAccessToken` 物件。|  
|[CAccessToken::GetType](../Topic/CAccessToken::GetType.md)|呼叫這個方法會取得 `CAccessToken` 物件的型別。|  
|[CAccessToken::GetUser](../Topic/CAccessToken::GetUser.md)|呼叫這個方法會識別使用者與 `CAccessToken` 物件。|  
|[CAccessToken::HKeyCurrentUser](../Topic/CAccessToken::HKeyCurrentUser.md)|呼叫這個方法會取得指向使用者設定檔的控制代碼與 `CAccessToken` 物件。|  
|[CAccessToken::Impersonate](../Topic/CAccessToken::Impersonate.md)|呼叫這個方法會指派模擬 `CAccessToken` 到執行緒。|  
|[CAccessToken::ImpersonateLoggedOnUser](../Topic/CAccessToken::ImpersonateLoggedOnUser.md)|呼叫這個方法允許呼叫執行緒模擬已登入使用者的安全性內容。|  
|[CAccessToken::IsTokenRestricted](../Topic/CAccessToken::IsTokenRestricted.md)|如果 `CAccessToken` 物件包含有限的 SID 清單，請呼叫這個方法會測試。|  
|[CAccessToken::LoadUserProfile](../Topic/CAccessToken::LoadUserProfile.md)|呼叫這個方法會載入使用者設定檔與 `CAccessToken` 物件。|  
|[CAccessToken::LogonUser](../Topic/CAccessToken::LogonUser.md)|呼叫這個方法會建立使用者的登入工作階段與指定的認證。|  
|[CAccessToken::OpenCOMClientToken](../Topic/CAccessToken::OpenCOMClientToken.md)|呼叫這個方法會處理來自用戶端的 COM 伺服器的內部呼叫一次初始化時存取語彙基元的 `CAccessToken` 從 COM 用戶端。|  
|[CAccessToken::OpenNamedPipeClientToken](../Topic/CAccessToken::OpenNamedPipeClientToken.md)|呼叫這個方法會取得具名管道伺服器的內部要求使用存取語彙基元的 `CAccessToken` 從用戶端。|  
|[CAccessToken::OpenRPCClientToken](../Topic/CAccessToken::OpenRPCClientToken.md)|呼叫這個方法會處理來自 RPC 用戶端的伺服器內部的呼叫使用存取語彙基元的 `CAccessToken` 從用戶端。|  
|[CAccessToken::OpenThreadToken](../Topic/CAccessToken::OpenThreadToken.md)|呼叫這個方法會設定模擬等級然後初始化使用語彙基元 `CAccessToken` 從指定的執行緒。|  
|[CAccessToken::PrivilegeCheck](../Topic/CAccessToken::PrivilegeCheck.md)|呼叫這個方法會判斷指定的一組權限是否在 **CAccessToken** 物件啟用。|  
|[CAccessToken::Revert](../Topic/CAccessToken::Revert.md)|呼叫這個方法會停止使用模擬語彙基元的執行緒。|  
|[CAccessToken::SetDefaultDacl](../Topic/CAccessToken::SetDefaultDacl.md)|呼叫這個方法會設定物件的預設 `CAccessToken` DACL。|  
|[CAccessToken::SetOwner](../Topic/CAccessToken::SetOwner.md)|呼叫這個方法會設定 `CAccessToken` 物件的擁有人。|  
|[CAccessToken::SetPrimaryGroup](../Topic/CAccessToken::SetPrimaryGroup.md)|呼叫這個方法會設定 `CAccessToken` 物件的主要群組。|  
  
## 備註  
 [存取語彙基元](http://msdn.microsoft.com/library/windows/desktop/aa374909) 是描述處理序或執行緒的安全性內容的物件和配置給每一位使用者都會記錄在 Windows NT 或 Windows 2000 系統上。  
  
 如需存取控制模型會在  視窗，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [存取控制](http://msdn.microsoft.com/library/windows/desktop/aa374860) 。  
  
## 需求  
 **Header:** atlsecurity.h  
  
## 請參閱  
 [ATLSecurity 範例](../../top/visual-cpp-samples.md)   
 [Access Tokens](http://msdn.microsoft.com/library/windows/desktop/aa374909)   
 [Class Overview](../../atl/atl-class-overview.md)