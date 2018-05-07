---
title: XML 文件產生器工具屬性頁 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCXDCMakeTool.ValidateIntelliSense
- VC.Project.VCXDCMakeTool.SuppressStartupBanner
- VC.Project.VCXDCMakeTool.DocumentLibraryDependencies
- VC.Project.VCXDCMakeTool.OutputDocumentFile
- VC.Project.VCXDCMakeTool.AdditionalDocumentFiles
dev_langs:
- C++
ms.assetid: 645912b5-197a-4c36-ba58-64df09444ca0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 772e9dc6a296873ef27171676ebca0c185c1771c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="xml-document-generator-tool-property-pages"></a>XML 文件產生器工具屬性頁
XML 文件產生器工具屬性頁公開 xdcmake.exe 的功能。 xdcmake.exe.xdc 檔至.xml 檔案時合併您的原始程式碼包含文件註解和[/doc （處理文件註解） （C/c + +）](../build/reference/doc-process-documentation-comments-c-cpp.md)已指定。 請參閱[建議的文件註解標記](../ide/recommended-tags-for-documentation-comments-visual-cpp.md)如需將文件註解加入至原始碼的資訊。  
  
> [!NOTE]
>  在命令列使用 xdcmake.exe 時的選項不同 xdcmake.exe 選項，在開發環境 （屬性頁）。 如需使用 xdcmake.exe 在命令列的資訊，請參閱[XDCMake 參考](../ide/xdcmake-reference.md)。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **隱藏程式啟始資訊**  
 隱藏著作權訊息。  
  
 **其他文件檔案**  
 您想在其中尋找.xdc 檔案的專案系統的其他目錄。 xdcmake 一律會尋找專案所產生的.xdc 檔。 您可以指定多個目錄。  
  
 **輸出文件檔**  
 .Xml 輸出檔案名稱與目錄位置。 請參閱[建置命令和屬性的一般巨集](../ide/common-macros-for-build-commands-and-properties.md)如需使用巨集來指定目錄位置。  
  
 **文件程式庫相依性**  
 如果您的專案具有相依性.lib 方案的專案中，您可以處理.xdc 檔從.lib 專案到目前專案的.xml 檔案。  
  
## <a name="see-also"></a>另請參閱  
 [屬性頁](../ide/property-pages-visual-cpp.md)   
 [屬性頁](../ide/property-pages-visual-cpp.md)