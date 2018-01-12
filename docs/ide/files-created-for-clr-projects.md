---
title: "為 CLR 專案建立的檔案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Visual C++ projects, CLR programming
- .NET applications, C++
ms.assetid: 59ae9020-5f26-4ad0-bbdd-97c2e2023a20
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a4abf5415e9b252a7cc92408fb273d226106fc16
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="files-created-for-clr-projects"></a>為 CLR 專案建立的檔案
當您使用 Visual c + + 範本來建立您的專案時，會建立數個檔案，在您使用根據哪一個範本。 下表列出.NET Framework 專案的專案範本所建立的所有檔案。  
  
|檔案名稱|檔案描述|  
|---------------|----------------------|  
|AssemblyInfo.cpp|包含的檔案資訊 （也就是屬性、 檔案、 資源、 類型、 版本設定資訊、 簽章的資訊等等） 修改專案的組件中繼資料。 如需詳細資訊，請參閱[組件概念](/dotnet/framework/app-domains/assembly-contents)。|  
|*projname*.asmx|參考 managed 類別來封裝的 XML Web 服務功能的文字檔。|  
|*projname*.cpp|主要原始程式檔和進入點到應用程式為您建立 Visual Studio。 識別專案.dll 檔案，以及專案命名空間。 在這個檔案中提供您自己的程式碼。|  
|*projname*.vsdisco|包含描述的 XML Web 服務的其他資源連結的 XML 部署檔案。|  
|*projname*.h|主要的 include 檔的專案，包含所有的宣告，全域符號，以及`#include`其他標頭檔的指示詞。|  
|*projname*.sln|方案檔，在開發環境中用來將您的專案的所有項目組織成單一方案。|  
|*projname*.suo|在開發環境中使用的方案選項檔。|  
|*projname*.vcxproj|儲存此專案的特定資訊的開發環境中使用專案檔。|  
|ReadMe.txt|描述使用範本所建立的實際檔名在專案中的每個檔案的檔案。|