---
title: 專案和方案檔
ms.date: 11/04/2016
f1_keywords:
- vc.files.projectandsolution
helpviewer_keywords:
- project files [C++]
- file types [C++], makefiles
- .sdf, browsing database file
- Makefile projects
- browsing database file, .sdf
- file types [C++], project files
ms.assetid: 5823b954-36cf-42d3-8fd5-25bab3ef63d9
ms.openlocfilehash: 8b84c28db2afb914a73a0cb4d0d778c99cfd6635
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50616633"
---
# <a name="project-and-solution-files"></a>專案和方案檔

當您在 Visual Studio 中建立專案時，會建立下列檔案。 它們可用來管理方案中的專案檔案。

|Filename|目錄位置|方案總管位置|描述|
|--------------|------------------------|--------------------------------|-----------------|
|*Solname*.sln|*Projname*|不會顯示在方案總管中|*「方案」* 檔。 它會將專案的所有項目或多個專案組織成一個方案。|
|*Projname*.suo|*Projname*|不會顯示在方案總管中|「方案選項」檔。 它會儲存您的方案自訂，如此每當您在方案中開啟專案或檔案時，它會呈現您所要的外觀和行為。|
|*Projname*.vcxproj|*Projname*|不會顯示在方案總管中|「專案」檔。 它會儲存每個專案的特定資訊。 (在舊版中，這個檔案名為 *Projname*.vcproj 或 *Projname*.dsp。)如需 Visual C++ 專案檔的範例，請參閱[專案檔](../ide/project-files.md)。|
|*Projname*.vcxitems|*Projname*|不會顯示在方案總管中|「共用的項目專案」檔。 不會建置此專案。  相反地，此專案可由另一個 C++ 專案參考，而其檔案會變成參考專案建置程序的一部分。 此專案可用來與跨平台 C++ 專案共用通用程式碼。|
|*Projname*.sdf|*Projname*|不會顯示在方案總管中|「瀏覽資料庫」檔案。 它支援瀏覽和導覽功能，例如 [移至定義]、[尋找所有參考] 和 [類別檢視]。 會藉由剖析標頭檔來產生它。|
|*Projname.* vcxproj.filters|*Projname*|不會顯示在方案總管中|「篩選」檔。 它指定要在方案的哪個位置加入檔案。 例如，.h 檔案放置於 [標頭檔] 節點中。|
|*Projname.* vcxproj.user|*Projname*|不會顯示在方案總管中|「移轉使用者」檔案。 從 Visual Studio 2008 移轉專案之後，此檔案包含任何 .vsprops 檔案轉換的資訊。|
|*Projname*.idl|*Projname*|原始程式檔|(特定專案) 包含控制項類型程式庫的介面描述語言 (IDL) 原始程式碼。 Visual C++ 會使用這個檔案來產生類型程式庫。 產生的程式庫會向其他自動化用戶端公開控制項的介面。 如需詳細資訊，請參閱 Windows SDK 中的 [Interface Definition (IDL) File](/windows/desktop/Rpc/the-interface-definition-language-idl-file) (介面定義 (IDL) 檔)。|
|Readme.txt|*Projname*|專案|「讀我檔案」。 它是由應用程式精靈所產生，並說明專案中的檔案。|

## <a name="see-also"></a>請參閱

[為 Visual C++ 專案建立的檔案類型](../ide/file-types-created-for-visual-cpp-projects.md)