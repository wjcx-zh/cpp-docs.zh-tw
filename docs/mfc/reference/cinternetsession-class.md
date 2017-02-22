---
title: "CInternetSession Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CInternetSession"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CInternetSession class"
  - "Internet sessions"
ms.assetid: ef54feb4-9d0f-4e65-a45d-7a4cf6c40e51
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CInternetSession Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

建立和初始化單一或多個同時的網際網路工作階段，然後，如果需要，描述，將 Proxy 伺服器的連接。  
  
## 語法  
  
```  
class CInternetSession : public CObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CInternetSession::CInternetSession](../Topic/CInternetSession::CInternetSession.md)|建構 `CInternetSession` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CInternetSession::Close](../Topic/CInternetSession::Close.md)|在網際網路工作階段結束時，關閉網際網路連線。|  
|[CInternetSession::EnableStatusCallback](../Topic/CInternetSession::EnableStatusCallback.md)|建立狀態回呼常式。|  
|[CInternetSession::GetContext](../Topic/CInternetSession::GetContext.md)|在網際網路工作階段結束時，關閉網際網路連線。|  
|[CInternetSession::GetCookie](../Topic/CInternetSession::GetCookie.md)|指定 URL 和它的所有父 URL 的傳回 Cookie。|  
|[CInternetSession::GetCookieLength](../Topic/CInternetSession::GetCookieLength.md)|擷取指定 Cookie 的長度變數儲存在緩衝區中。|  
|[CInternetSession::GetFtpConnection](../Topic/CInternetSession::GetFtpConnection.md)|開始使用 FTP 伺服器上的工作階段。  登入使用者。|  
|[CInternetSession::GetGopherConnection](../Topic/CInternetSession::GetGopherConnection.md)|開啟嘗試開啟連接的應用程式建立 Gopher 伺服器。|  
|[CInternetSession::GetHttpConnection](../Topic/CInternetSession::GetHttpConnection.md)|開啟嘗試開啟連接的應用程式中的 HTTP 伺服器。|  
|[CInternetSession::OnStatusCallback](../Topic/CInternetSession::OnStatusCallback.md)|狀態時，就會啟用回呼時，更新作業的狀態。|  
|[CInternetSession::OpenURL](../Topic/CInternetSession::OpenURL.md)|剖析並開啟 URL。|  
|[CInternetSession::SetCookie](../Topic/CInternetSession::SetCookie.md)|設定指定之 URL 的 Cookie。|  
|[CInternetSession::SetOption](../Topic/CInternetSession::SetOption.md)|設定網際網路工作階段的選項。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CInternetSession::operator HINTERNET](../Topic/CInternetSession::operator%20HINTERNET.md)|對目前網際網路工作階段的控制代碼。|  
  
## 備註  
 如果必須在應用程式執行期間維護您的網際網路連線，您可以建立類別的 [CWinApp](../../mfc/reference/cwinapp-class.md)`CInternetSession` 成員。  
  
 一旦建立了網際網路工作階段，您可以呼叫 [OpenURL](../Topic/CInternetSession::OpenURL.md)。  `CInternetSession` 藉由呼叫全域函式會剖析您的 URL [AfxParseURL](../Topic/AfxParseURL.md)。  不論通訊協定類型， `CInternetSession` 說明 URL 並處理它。  它可以處理要求本機檔案識別與 URL 資源「file:\/\/」。  `OpenURL` 會傳回指標 [CStdioFile](../../mfc/reference/cstdiofile-class.md) 物件名稱可以是本機檔案。  
  
 使用 `OpenURL`，如果在網際網路伺服器的 URL，您可以讀取整個網站的資訊。  如果您要對位於伺服器上之檔案的 Service 特定 \(例如， HTTP、FTP 或 Gopher\) 動作，您必須建立與伺服器的連接。  若要開啟特定類型連接直接與特定服務，請使用下列其中一個成員函式:  
  
-   開啟 Gopher 伺服器連接的[GetGopherConnection](../Topic/CInternetSession::GetGopherConnection.md) 。  
  
-   開啟與 HTTP 服務之連接的[GetHttpConnection](../Topic/CInternetSession::GetHttpConnection.md) 。  
  
-   開啟與 FTP 伺服器的連接[GetFtpConnection](../Topic/CInternetSession::GetFtpConnection.md) 。  
  
 [SetOption](../Topic/CInternetSession::SetOption.md) 這個元件允許您設定工作階段的查詢選項，例如逾時值，再測試的數值，依此類推。  
  
 `CInternetSession` 成員函式 [SetCookie](../Topic/CInternetSession::SetCookie.md)、 [GetCookie](../Topic/CInternetSession::GetCookie.md)和 [GetCookieLength](../Topic/CInternetSession::GetCookieLength.md) 提供處理 Win32 Cookie 資料庫，伺服器和指令碼會維護有關用戶端工作站的狀態資訊。  
  
 如需基本網際網路程式設計工作的詳細資訊，請參閱本文 [網際網路第一個步驟:WinInet](../../mfc/wininet-basics.md)。  如需使用 MFC WinInet 類別的一般資訊，請參閱本文 [Office 方案中使用 WinInet 的網際網路](../../mfc/win32-internet-extensions-wininet.md)。  
  
> [!NOTE]
>  `CInternetSession` 會擲回不支援的服務型別的 [AfxThrowNotSupportedException](../Topic/AfxThrowNotSupportedException.md) 。  只有下列服務型別目前支援:FTP、HTTP、Gopher 和檔案。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CInternetSession`  
  
## 需求  
 **Header:** afxinet.h  
  
## 請參閱  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CInternetConnection Class](../../mfc/reference/cinternetconnection-class.md)   
 [CHttpConnection Class](../../mfc/reference/chttpconnection-class.md)   
 [CFtpConnection Class](../../mfc/reference/cftpconnection-class.md)   
 [CGopherConnection Class](../../mfc/reference/cgopherconnection-class.md)