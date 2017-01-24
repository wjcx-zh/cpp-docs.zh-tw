---
title: "轉散發資料庫支援檔案 | Microsoft Docs"
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
  - "資料庫支援檔案 [C++], 轉散發"
  - "轉散發資料庫支援檔案"
ms.assetid: d80cffe0-177c-4515-9de7-fbf0517eb8d6
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 轉散發資料庫支援檔案
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以針對資料存取物件 \(DAO\) 以及 Microsoft Data Access SDK 中的資料庫技術來轉散發支援檔案。  
  
## 安裝 DAO 支援檔案  
 若要取得最新版的 DAO，請參閱[Microsoft 技術支援網站上的文件 239114：如何取得 Microsoft Jet 4.0 資料庫引擎的最新版](http://go.microsoft.com/fwlink/?LinkId=198014) 在Microsoft 支援的網站上。  
  
## 安裝 Microsoft Data Access SDK 支援檔案  
 使用 Mdac\_typ.exe 來安裝 ODBC、OLE DB、ActiveX Data Objects \(ADO\) 和遠端資料服務 \(Remote Data Services，RDS\) 的支援。  Mdac\_typ.exe 位於在 Visual Studio 安裝媒體中 ...\\ WCU \\ MDAC28 \\資料夾。  您也可自[Microsoft 下載中心](http://go.microsoft.com/fwlink/?LinkId=198015)下載 Mdac\_typ.exe。  
  
 如需詳細資訊，如 [MSDN](http://go.microsoft.com/fwlink/?LinkId=198016) 網站，搜尋「Redistributing MDAC 2.8 SP1」。  如果您要使用 Visual Studio 安裝專案來部署應用程式，請參閱[Deployment and Dependencies](http://msdn.microsoft.com/zh-tw/49e9b84d-bd6a-4388-b9ac-46ea79cf0733)。  
  
## 請參閱  
 [轉散發 Visual C\+\+ 檔案](../ide/redistributing-visual-cpp-files.md)