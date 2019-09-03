---
title: 一般屬性頁 (檔案)
ms.date: 08/30/2019
f1_keywords:
- VC.Project.VCFileConfiguration.ExcludedFromBuild
- VC.Project.VCFileConfiguration.Tool
ms.assetid: 26e3711e-9e7d-4e8d-bc4c-2474538efdad
ms.openlocfilehash: 41366e2eae479c3d00f79cc47da9100b22129d50
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218192"
---
# <a name="general-property-page-file"></a>一般屬性頁 (檔案)

本主題適用于 Windows 專案。 若是非 Windows 專案, 請參閱[Linux C++屬性頁參考](../../linux/prop-pages-linux.md)。

當您以滑鼠右鍵按一下**方案總管**的檔案節點時, [設定**屬性**] 節點底下的 [**一般**] 屬性頁隨即開啟。 其中包含下列屬性:

- **從組建排除**

   指定檔案是否應該在目前組態的組建中。

   若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCFileConfiguration.ExcludedFromBuild%2A>。

- **內容**(僅適用于 UWP 應用程式)。指定檔案是否包含要包含在應用程式套件中的內容。

- **專案類型**

   **專案類型**會指定在建立進程期間用來處理檔案的工具。 [已知其副檔名](/visualstudio/extensibility/visual-cpp-project-extensibility?view=vs-2019#project-items)的檔案 Visual Studio 在此屬性中具有預設值。 如果您有自訂檔案類型, 或想要覆寫已知檔案類型的預設工具, 則可以在此指定自訂工具。 請參閱[指定自訂建置工具](../specifying-custom-build-tools.md)以取得詳細資訊。 您也可以使用此屬性頁來指定檔案不是組建進程的一部分。

   下圖顯示 *.cpp*檔案的屬性頁。 這種檔案的預設**專案類型**是**C/C++編譯器**(*cl .exe*), 而屬性頁會公開只能套用至此檔案的各種編譯器設定。

   ![專案專案的一般屬性頁](media/file-general-item-type.png "專案類型選擇")

    下表列出預設專案類型:

    |副檔名|項目類型|預設工具|
    |-|-|-|
    |.appx|XAML 應用程式定義|[應用程式封裝工具](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |hlsl,. cso|HLSL 編譯器|[fxc .exe](/windows/win32/direct3dtools/fxc)|
    |.h|C/C++標頭|[C/C++ 前置處理器](../../preprocessor/c-cpp-preprocessor-reference.md)|
    |N/A|不參與組建|N/A|
    |.xml、xslt、.xsl|Xml|[XML 編輯器](/visualstudio/xml-tools/xml-editor)|
    |. .resw、. resjson|PRI 資源 (UWP 應用程式)|[MakePri .exe](/windows/uwp/app-resources/compile-resources-manually-with-makepri)|
    ||媒體 (UWP)|[應用程式封裝工具](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |.xsd|XML 資料產生器工具|[XML 架構定義工具 (xsd.exe)](/dotnet/standard/serialization/xml-schema-definition-tool-xsd-exe)(需要 .NET 工作負載。 不包含在 MSVC 中)。|
    ||資訊清單工具|[mt .exe](/windows/win32/sbscs/mt-exe)|
    |.rc|Resource|[Windows 資源編譯器 (rc .exe)](/windows/win32/menurc/resource-compiler)|
    |. package.appxmanifest.xml|應用程式套件資訊清單|[應用程式封裝工具](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |.obj|Object|[C/C++連結器 (連結 .exe)](cl-invokes-the-linker.md)|
    |. .ttf|字型|N/A|
    |.txt|文字|N/A|
    |N/A|自訂群組建工具|使用者定義|
    |N/A|複製檔案|N/A|
    |. app.packagelayout|應用程式套件版面配置|[應用程式封裝工具](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |.resx|編譯器管理的資源|[Resgen.exe (資源檔產生器)](/dotnet/framework/tools/resgen-exe-resource-file-generator)|
    |. natvis|C++偵錯工具視覺效果檔案|[Natvis 架構](/visualstudio/debugger/create-custom-views-of-native-objects)|
    |.jpg、.bmp、.ico 等等。|Image|以應用程式類型為基礎的資源編譯器。|
    |.cpp|C/C++編譯器|cl .exe|

   若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCFileConfiguration.Tool%2A>。

如需如何存取 [設定**屬性**] 節點下 [**一般**] 屬性頁的詳細資訊, 請參閱[Visual Studio 中的設定C++編譯器和組建屬性](../working-with-project-properties.md)。

## <a name="see-also"></a>另請參閱

[C++專案屬性頁參考](property-pages-visual-cpp.md)