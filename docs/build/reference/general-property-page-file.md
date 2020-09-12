---
title: 一般屬性頁 (檔案)
ms.date: 08/30/2019
f1_keywords:
- VC.Project.VCFileConfiguration.ExcludedFromBuild
- VC.Project.VCFileConfiguration.Tool
ms.assetid: 26e3711e-9e7d-4e8d-bc4c-2474538efdad
ms.openlocfilehash: 7626e161e6f59de32d426b558827c423a0bb050d
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041376"
---
# <a name="general-property-page-file"></a>一般屬性頁 (檔案)

本主題適用于 Windows 專案。 若是非 Windows 專案，請參閱 [Linux C++ 屬性頁參考](../../linux/prop-pages-linux.md)。

當您以滑鼠右鍵按一下檔案節點**方案總管**時，[設定**屬性**] 節點底下的 [**一般**] 屬性頁面會隨即開啟。 它包含下列屬性：

- **從組建中排除**

   指定檔案是否應該在目前組態的組建中。

   若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCFileConfiguration.ExcludedFromBuild%2A>。

- **Content** (僅適用于 UWP 應用程式。 ) 指定檔案是否包含要包含在應用程式套件中的內容。

- **專案類型**

   **專案類型**會指定在建立程式期間用來處理檔案的工具。 [已知 Visual Studio 副檔名](/visualstudio/extensibility/visual-cpp-project-extensibility#project-items) 的檔案，在這個屬性中具有預設值。 如果您有自訂檔案類型，或是想要覆寫已知檔案類型的預設工具，您可以在這裡指定自訂工具。 請參閱[指定自訂建置工具](../specifying-custom-build-tools.md)以取得詳細資訊。 您也可以使用這個屬性頁，指定檔案不是組建進程的一部分。

   下圖顯示 *.cpp* 檔的屬性頁。 這種檔案的預設 **專案類型** 是 **C/c + + 編譯器** (*cl.exe*) 而且屬性頁會公開只能套用至這個檔案的各種編譯器設定。

   ![專案專案的一般屬性頁](media/file-general-item-type.png "專案類型選擇")

    下表列出預設的專案類型：

    |副檔名|項目類型|預設工具|
    |-|-|-|
    |.appx|XAML 應用程式定義|[應用程式封裝工具](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |hlsl，cso|HLSL 編譯器|[fxc.exe](/windows/win32/direct3dtools/fxc)|
    |.h|C/c + + 標頭|[C/c + + 預處理器](../../preprocessor/c-cpp-preprocessor-reference.md)|
    |n/a|未參與組建|n/a|
    |.xml、xslt、.xsl|Xml|[XML 編輯器](/visualstudio/xml-tools/xml-editor)|
    |.resw、. resources.resjson| (UWP 應用程式) 的 PRI 資源|[MakePri.exe](/windows/uwp/app-resources/compile-resources-manually-with-makepri)|
    ||Media (UWP) |[應用程式封裝工具](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |.xsd|XML 資料產生器工具|[XML 架構定義工具 ( # A0) ](/dotnet/standard/serialization/xml-schema-definition-tool-xsd-exe) (需要 .net 工作負載。 不包含在 MSVC 中。 ) |
    ||資訊清單工具|[mt.exe](/windows/win32/sbscs/mt-exe)|
    |.rc|資源|[Windows 資源編譯器 ( # A0) ](/windows/win32/menurc/resource-compiler)|
    |. package.appxmanifest|應用程式套件資訊清單|[應用程式封裝工具](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |.obj|Object|[C/c + + 連結器 ( # A0) ](cl-invokes-the-linker.md)|
    |.ttf|字型|n/a|
    |.txt|Text|n/a|
    |n/a|自訂群組建工具|使用者定義|
    |n/a|複製檔案|n/a|
    |.packagelayout|應用程式套件配置|[應用程式封裝工具](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |.resx|編譯器管理的資源|[ 資源檔產生器Resgen.exe () ](/dotnet/framework/tools/resgen-exe-resource-file-generator)|
    |. natvis|C + + 偵錯工具視覺化檔案|[Natvis 架構](/visualstudio/debugger/create-custom-views-of-native-objects)|
    |.jpg、.bmp、.ico 等等。|映像|以應用程式類型為基礎的資源編譯器。|
    |.cpp|C/c + + 編譯器|cl.exe|

   若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCFileConfiguration.Tool%2A>。

如需如何存取 [設定**屬性**] 節點下 [**一般**] 屬性頁的詳細資訊，請參閱[Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

## <a name="see-also"></a>另請參閱

[C + + 專案屬性頁參考](property-pages-visual-cpp.md)
