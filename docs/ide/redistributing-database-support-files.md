---
title: 轉散發資料庫支援檔案 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- redistributing database support files
- database support files [C++], redistributing
ms.assetid: d80cffe0-177c-4515-9de7-fbf0517eb8d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a51697367480569e2d27a4cb67791f5fe4d39a8f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323871"
---
# <a name="redistributing-database-support-files"></a>轉散發資料庫支援檔案
您可以轉散發資料存取物件 (DAO) 的支援檔案，以及 Microsoft Data Access SDK 中資料庫技術的支援檔案。  
  
## <a name="installing-dao-support-files"></a>安裝 DAO 支援檔案  
 若要取得最新版的 DAO，請參閱 Microsoft 技術支援網站上的[文章 239114：如何取得 Microsoft Jet 4.0 資料庫引擎的最新版 Service Pack](http://go.microsoft.com/fwlink/p/?linkid=198014)。  
  
## <a name="installing-microsoft-data-access-sdk-support-files"></a>安裝 Microsoft Data Access SDK 支援檔案  
 使用 Mdac_typ.exe 可安裝 ODBC、OLE DB、ActiveX Data Objects (ADO) 和遠端資料服務 (RDS) 的支援。 Mdac_typ.exe 位於在 Visual Studio 安裝媒體中的 ..\WCU\MDAC28\ 資料夾。 您也可自 [Microsoft 下載中心](http://go.microsoft.com/fwlink/p/?linkid=198015)網站下載 Mdac_typ.exe。  
  
 如需詳細資訊，請在 [MSDN](http://go.microsoft.com/fwlink/p/?linkid=198016) 網站，搜尋 "Redistributing MDAC 2.8 SP1"。 如果您使用 Visual Studio 安裝程式專案來部署您的應用程式，請參閱[部署和相依性](http://msdn.microsoft.com/en-us/49e9b84d-bd6a-4388-b9ac-46ea79cf0733)。  
  
## <a name="see-also"></a>請參閱  
 [轉散發 Visual C++ 檔案](../ide/redistributing-visual-cpp-files.md)