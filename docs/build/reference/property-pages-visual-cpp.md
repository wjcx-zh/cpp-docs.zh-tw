---
title: Windows C++專案屬性頁參考-Visual Studio
ms.date: 08/28/2019
helpviewer_keywords:
- project-file macro
- project properties [C++], default values
- user-defined values
- project properties [C++], setting
- macros, project-file
- property pages, project settings
- C++ projects, properties
- build macro
- user-defined macros
ms.assetid: 13ffe3ea-1bc3-4bee-be5e-053a8a99cce4
ms.openlocfilehash: c9fd4fc00e86e0660972fc0bd37b66b2fea02ee0
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177455"
---
# <a name="windows-c-project-property-page-reference"></a>Windows C++專案屬性頁參考

在 Visual Studio 中, 您可以透過專案的屬性頁, 指定編譯器和連結器選項、檔案路徑和其他組建設定。 可用的屬性和屬性頁面取決於專案類型。 例如, makefile 專案具有 [NMake] 屬性頁, 該頁面不會出現在 MFC 或 Win32 主控台專案中。 若要開啟**屬性頁**, 請從主功能表中選擇 [**專案** > **屬性**], 或以滑鼠右鍵按一下**方案總管**中的專案節點, 然後選擇 [**屬性**]。 個別檔案也有屬性頁, 可讓您只設定該檔案的編譯和建立選項。 下圖顯示 MFC 專案的屬性頁。

![專案的C++屬性頁](media/example-prop-page.png)

本節提供屬性頁本身的快速參考。 在屬性頁中公開的選項和設定, 會以更完整的方式記載在自己的主題中, 並從屬性頁主題進行連結。 如需專案屬性的詳細資訊, 請參閱[Visual Studio 中的設定C++編譯器和組建屬性](../working-with-project-properties.md)。

如需 Linux 專案中的屬性頁, 請參閱[linux C++屬性頁參考](../../linux/prop-pages-linux.md)。

## <a name="in-this-section"></a>本節內容

- [一般屬性頁面 (專案)](general-property-page-project.md)
- [一般屬性頁 (檔案)](general-property-page-file.md)
- [Advanced 屬性頁](advanced-property-page.md)
- [VC++ 目錄屬性頁](vcpp-directories-property-page.md)
- [連結器屬性頁](linker-property-pages.md)
- [資訊清單工具屬性頁](manifest-tool-property-pages.md)
- [HLSL 屬性頁](hlsl-property-pages.md)
- [命令列屬性頁](command-line-property-pages.md)
- [自訂建置步驟屬性頁：一般](custom-build-step-property-page-general.md)
- [新增參考](../adding-references-in-visual-cpp-projects.md)
- [Managed 資源屬性頁](managed-resources-property-page.md)
- [MIDL 屬性頁](midl-property-pages.md)
- [NMake 屬性頁](nmake-property-page.md)
- [資源屬性頁](resources-property-pages.md)
- [Web 參考屬性頁](web-references-property-page.md)
- [XML 資料產生器工具屬性頁](xml-data-generator-tool-property-page.md)
- [XML 文件產生器工具屬性頁](xml-document-generator-tool-property-pages.md)

## <a name="see-also"></a>另請參閱

[如何：建立及移除專案相依性](/visualstudio/ide/how-to-create-and-remove-project-dependencies)<br/>
[如何：建立及編輯組態](/visualstudio/ide/how-to-create-and-edit-configurations)<br/>
[Linux C++屬性頁參考](../../linux/prop-pages-linux.md)
