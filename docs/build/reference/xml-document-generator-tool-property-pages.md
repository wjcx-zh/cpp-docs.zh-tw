---
title: XML 文件產生器工具屬性頁
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCXDCMakeTool.ValidateIntelliSense
- VC.Project.VCXDCMakeTool.SuppressStartupBanner
- VC.Project.VCXDCMakeTool.DocumentLibraryDependencies
- VC.Project.VCXDCMakeTool.OutputDocumentFile
- VC.Project.VCXDCMakeTool.AdditionalDocumentFiles
ms.assetid: 645912b5-197a-4c36-ba58-64df09444ca0
ms.openlocfilehash: 9f10ddf98c238120750e72644779a6ad74af2d1e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171628"
---
# <a name="xml-document-generator-tool-property-pages"></a>XML 文件產生器工具屬性頁

XML 文件產生器工具屬性頁會公開 xdcmake.exe 的功能。 當您的原始程式碼包含文件註解並指定 [/doc (處理文件註解) (C/C++)](doc-process-documentation-comments-c-cpp.md) 時，xdcmake.exe 會將多個 .xdc 檔案合併成一個 .xml 檔案。 如需將文件註解新增至原始程式碼的資訊，請參閱[建議使用的文件註解標籤](recommended-tags-for-documentation-comments-visual-cpp.md)。

> [!NOTE]
>  開發環境 (屬性頁) 中的 xdcmake.exe 選項與用於命令列中的 xdcmake.exe 選項不同。 如需在命令列使用 xdcmake.exe 的資訊，請參閱 [XDCMake 參考](xdcmake-reference.md)。

## <a name="uielement-list"></a>UIElement 清單

- **隱藏啟動橫幅**

   隱藏著作權訊息。

- **其他文件檔**

   您想要專案系統在其中尋找 .xdc 檔案的其他目錄。 xdcmake 一律會尋找專案所產生的 .xdc 檔案。 您可以指定多個目錄。

- **輸出文件檔**

   .xml 輸出檔的名稱和目錄位置。 如需使用宏來指定目錄位置的相關資訊，請參閱[組建命令和屬性的一般宏](common-macros-for-build-commands-and-properties.md)。

- **文件庫相依性**

   如果您的專案相依於方案中的 .lib 專案，您可以將 .lib 專案中的 .xdc 檔案處理到目前專案中的 .xml 檔案。

## <a name="see-also"></a>另請參閱

[C++專案屬性頁參考](property-pages-visual-cpp.md)
