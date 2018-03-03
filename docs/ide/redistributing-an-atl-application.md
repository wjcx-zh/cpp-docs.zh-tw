---
title: "轉散發 ATL 應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- ATL, redistributing
- redistributing ATL
- redistributing OLE DB templates
- OLE DB templates, redistributing
ms.assetid: 9a696b22-2345-43ec-826b-be7cb8cfd676
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3a9e4259c70aff53252cd91db217a96d9d5480a7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="redistributing-an-atl-application"></a>轉散發 ATL 應用程式
從 Visual Studio 2012 開始，Active Template Library (ATL) 是僅限標頭的程式庫。 ATL 專案不會動態連結至 ATL 選項。 可轉散發 ATL 程式庫不是必要的。  
  
 如果您轉散發 ATL 可執行的應用程式，即必須發出下列命令來註冊 .exe 檔案 (和其中所有控制項)：  
  
```  
filename /regserver  
```  
  
 其中 `filename` 是可執行檔案的名稱。  
  
 在 Visual Studio 2010 中，ATL 專案可以建置成 MinDependency 或 MinSize 組態。 MinDependency 組態是您會取得當您設定**ATL 用法**屬性**靜態連結 ATL**上**一般**屬性頁，並設定**執行階段程式庫**屬性**多執行緒 (/ MT)**上**程式碼產生**屬性頁 （C/c + + 資料夾）。  
  
 MinSize 組態是您會取得當您設定**ATL 用法**屬性**動態連結 ATL**上**一般**屬性頁上或組**執行階段程式庫**屬性**多執行緒 DLL (/ MD)**上**程式碼產生**屬性頁 （C/c + + 資料夾）。  
  
 MinSize 會讓輸出檔案一樣，但可能需要的小 ATL100.dll 和 Msvcr100.dll (如果您選取**多執行緒 DLL (/ MD)**選項) 會在目標電腦上。 ATL100.dll 應該在目標電腦上註冊，以確保所有 ATL 的功能都會出現。 ATL100.dll 包含 ANSI 和 Unicode 匯出。  
  
 如果為 MinDependency 目標建置 ATL 或 OLE DB 範本專案，目標電腦上不必安裝和註冊 ATL100.dll，雖然您可能會得到較大的程式映像。  
  
 如果您轉散發 ATL 可執行的應用程式，即必須發出下列命令來註冊 .exe 檔案 (和其中所有控制項)：  
  
```  
filename /regserver  
```  
  
 其中 `filename` 是可執行檔案的名稱。  
  
 至於 OLE DB 範本應用程式，請確定目標電腦有最新版的 Microsoft Data Access Components (MDAC) 檔案。 如需詳細資訊，請參閱[轉散發資料庫支援檔案](../ide/redistributing-database-support-files.md)。  
  
## <a name="see-also"></a>請參閱  
 [轉散發 Visual C++ 檔案](../ide/redistributing-visual-cpp-files.md)