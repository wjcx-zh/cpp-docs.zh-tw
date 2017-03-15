---
title: "為 CLR 專案建立的檔案 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - ".NET 應用程式, C++"
  - "Visual C++ 專案, CLR 程式設計"
ms.assetid: 59ae9020-5f26-4ad0-bbdd-97c2e2023a20
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 為 CLR 專案建立的檔案
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您使用 Visual C\+\+ 樣板建立專案時，系統會依據您使用的樣板建立一些檔案。  下列資料表列出專案樣板為 .NET Framework 專案建立的所有檔案。  
  
|檔案名稱|檔案說明|  
|----------|----------|  
|AssemblyInfo.cpp|包含修改專案組件中繼資料的資訊 \(亦即屬性、檔案、資源、型別、版本資訊、簽章資訊等\) 的檔案。  如需詳細資訊，請參閱[組件概念](../Topic/Assembly%20Contents.md)。|  
|*projname*.asmx|參考封裝 XML Web Service 功能之 Managed 類別的文字檔。|  
|*projname*.cpp|Visual Studio 為您建立的主要原始程式檔 \(Source File\) 與應用程式的進入點。  識別專案 .dll 檔案及專案命名空間。  在這個檔案中提供個人的程式碼。|  
|*projname*.vsdisco|包含說明 XML Web Service 的其他資源連結之 XML 部署檔。|  
|*projname*.h|專案的主要 Include 檔，其中包含所有的宣告、全域符號和其他標頭檔的 `#include` 指示詞。|  
|*projname*.sln|在開發環境中使用的方案檔，可將您專案的所有項目組織成單一方案。|  
|*projname*.suo|開發環境內使用的方案選項檔案。|  
|*projname.vcxproj*|在開發環境中使用的專案檔，可儲存此專案的特定資訊。|  
|ReadMe.txt|描述使用樣板建立之實際檔名的專案中的每個檔案之檔案。|