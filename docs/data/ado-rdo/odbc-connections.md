---
title: "ODBC 連接 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ODBC 連接, 設定"
  - "ODBC, 連接"
ms.assetid: c9df2fa6-d9e2-4335-b885-724662968691
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ODBC 連接
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ODBC 連接是在系統 \[控制台\] 內做設定。  任何安裝 ODBC 驅動程式的資料來源都可進行 ODBC 連接。  Visual C\+\+ 6.0 \(含\) 以後版本隨附有文字檔、Access、FoxPro、Paradox、dBASE、Excel、SQL Server 和 Oracle 的驅動程式。  在建立 ODBC 連接時，它會自動接收資料來源的名稱 \(DSN\)。  接著，使用 DSN 來辨識資料控制項內的連接，例如，ADO 資料控制項和 RDO RemoteData 控制項。  
  
 **OLE DB 連接**：設定 OLE DB 連接不需任何其他的工作。  例如，如果已經建立 ODBC 資料來源，ODBC 的 OLE DB 提供者會自動偵測到它。  
  
### 若要設定 ODBC 資料來源的組態  
  
1.  按一下 \[**開始**\]，然後按一下 \[**設定**\]，接著再按 \[**控制台**\]。  
  
2.  在 \[控制台\] 內選取 \[32 位元 ODBC\] \(Windows 95 或 98\) 或 \[ODBC\] \(Windows NT 或 2000\)。  
  
3.  按一下 \[使用者資料來源名稱\] 或 \[系統資料來源名稱\] 索引標籤。  \[使用者資料來源名稱\] 可讓您建立使用者的相關資料來源名稱，而 \[系統資料來源名稱\] 則讓您建立所有使用者都可使用的資料來源。  
  
4.  按一下 \[新增\]，顯示本機所安裝的 ODBC 驅動程式清單。  
  
5.  選取對應到索引循序存取方法 \(ISAM\) 類型的驅動程式，或您想要連接的資料庫，然後按一下 \[完成\]。  
  
6.  依照指示指定至驅動程式。  關閉後，便可以使用資料來源名稱 \(DSN\)。  
  
 在針對一些 ODBC 驅動程式類型產生資料來源名稱時，需要知道實際檔案的位置。  例如，在建立 Access 資料來源名稱時，需要知道 .mdb 檔的位置。  此外，您應該擁有有效的使用者名稱和密碼。  例如，大多數 Access 系統的系統使用者名稱都是 *admin*。  
  
 在建立 [Oracle](../../data/ado-rdo/oracle-connections.md) 資料來源名稱時，您應該知道 SQL\*Net 連接字串 \(Connection String\)。  
  
## 請參閱  
 [建立資料庫連接](../../data/ado-rdo/creating-database-connections.md)