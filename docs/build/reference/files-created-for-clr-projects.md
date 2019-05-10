---
title: 為 CLR 專案建立的檔案
ms.date: 11/04/2016
helpviewer_keywords:
- Visual Studio C++ projects, CLR programming
- .NET applications, C++
ms.assetid: 59ae9020-5f26-4ad0-bbdd-97c2e2023a20
ms.openlocfilehash: e41544adb040175fc8e53ab0e6bc4f8275891580
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446323"
---
# <a name="files-created-for-clr-projects"></a>為 CLR 專案建立的檔案

當您使用 Visual C++ 範本建立專案時，會根據您使用的範本建立數個檔案。 下表列出由 .NET Framework 專案的專案範本建立的所有檔案。

|檔案名稱|檔案描述|
|---------------|----------------------|
|AssemblyInfo.cpp|此檔案包含用於修改專案組件中繼資料的資訊 (亦即屬性、檔案、資源、類型、版本設定資訊、簽章資訊等)。 如需詳細資訊，請參閱[組件概念](/dotnet/framework/app-domains/assembly-contents)。|
|*projname*.asmx|文字檔，參考封裝 XML Web Service 功能的受控類別。|
|*projname*.cpp|Visual Studio 為您建立的主要原始程式檔和應用程式進入點。 識別專案 .dll 檔案及專案命名空間。 在這個檔案中提供您自己的程式碼。|
|*projname*.vsdisco|XML 部署檔，其中包含描述 XML Web Service 之其他資源的連結。|
|*projname*.h|專案的主要 Include 檔，其中包含所有宣告、全域符號及其他標頭檔的 `#include` 指示詞。|
|*projname*.sln|用於開發環境的方案檔，可將您專案的所有項目組織成單一方案。|
|*projname*.suo|用於開發環境的方案選項檔。|
|*projname*.vcxproj|用於開發環境的專案檔，可儲存此專案特定的資訊。|
|ReadMe.txt|此檔案使用範本建立的實際檔名來描述您專案中的每個檔案。|