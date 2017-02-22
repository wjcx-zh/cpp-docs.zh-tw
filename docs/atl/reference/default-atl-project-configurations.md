---
title: "預設的 ATL 專案組態 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 專案, 預設設定"
ms.assetid: 7e272722-41af-4330-b965-a6d74ec16880
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# 預設的 ATL 專案組態
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個主題將比較 Visual C\+\+ .NET 的預設 ATL 專案組態和 Visual C\+\+ 6.0 的預設專案組態。  
  
## Visual C\+\+ .NET 預設組態  
 在 Visual C\+\+ .NET 中的 ATL 專案精靈會依預設建立兩個專案組態。  
  
### Visual C\+\+ .NET 組態  
  
|組態|字元集|ATL 的使用|  
|--------|---------|-------------|  
|Release|MBCS|DLL|  
|偵錯|MBCS|DLL|  
  
 \[**字元集**\]、\[**ATL 用法**\] 都可以在 \[**專案設定**\] 對話方塊的 \[**一般**\] 索引標籤下進行變更。  您也可以使用組態管理員加入自己的組態。  如需詳細資訊，請參閱[組建組態](../Topic/Understanding%20Build%20Configurations.md)。  
  
## 6.0 版的預設組態  
 在 6.0 版的 Visual C\+\+ 中，ATL COM AppWizard \(現在稱為 ATL 專案精靈\) 依預設會建立六種專案組態。  這些組態在發行版本、偵錯版本、Unicode 版本，以及使用 CRT 和 ATL 設定上各有不同之處。  必要時，您也可以在 Visual C\+\+ .NET 使用組態管理員複製上述所有組態。  
  
### 6.0 版的組態  
  
|組態|字元集|ATL 的使用|  
|--------|---------|-------------|  
|偵錯|MBCS|Static|  
|偵錯 Unicode|UNICODE|Static|  
|發行版本最小相依性|MBCS|Static|  
|發行版本最小相依性 Unicode|UNICODE|Static|  
|發行版本最小大小|MBCS|DLL|  
|發行版本最小大小 Unicode|UNICODE|DLL|  
  
## 請參閱  
 [使用 ATL 和 C 執行階段程式碼進行程式設計](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [使用專案屬性](../../ide/working-with-project-properties.md)   
 [Configuration Manager Dialog Box](http://msdn.microsoft.com/zh-tw/fa182dca-282e-4ae5-bf37-e155344ca18b)   
 [Compiling and Building](../Topic/Compiling%20and%20Building%20in%20Visual%20Studio.md)