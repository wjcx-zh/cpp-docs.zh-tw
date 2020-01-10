---
title: Managed 資源屬性頁
ms.date: 08/28/2019
f1_keywords:
- VC.Project.VCManagedResourceCompilerTool.ResourceFileName
- VC.Project.VCManagedResourceCompilerTool.OutputFileName
- VC.Project.VCManagedResourceCompilerTool.DefaultLocalizedResources
helpviewer_keywords:
- Managed Resources property page
ms.assetid: 80b80384-ee55-494d-9f0e-907bb98cfc19
ms.openlocfilehash: 14802996e63392bfb5fcc22096ef5f3d9db197c2
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177521"
---
# <a name="managed-resources-property-page"></a>Managed 資源屬性頁

在/Cli 程式中C++使用 .net 資源時, [**受控資源**] 屬性頁會公開 managed 資源編譯器[resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator)的下列屬性:

- **資源邏輯名稱**

   指定所產生之中繼 .resources 檔案的「邏輯名稱」。 邏輯名稱是用來載入資源的名稱。 如果未指定任何邏輯名稱，則會使用資源檔 (.resx) 名稱作為邏輯名稱。

- **輸出檔名稱**

   指定資源檔 (.resx) 所提供的最後輸出檔的名稱。

- **預設的當地語系化資源**

   指定給定的 .resx 檔案是提供預設的資源或附屬 .dll。

如需如何存取 [**受控資源**] 屬性頁的詳細資訊, 請參閱[Visual Studio 中的C++設定編譯器和組建屬性](../working-with-project-properties.md)。

## <a name="see-also"></a>另請參閱

[使用 RC (RC 命令列)](/windows/win32/menurc/using-rc-the-rc-command-line-)<br>
[C++專案屬性頁參考](property-pages-visual-cpp.md)<br>
[/ASSEMBLYRESOURCE (內嵌 Managed 資源)](assemblyresource-embed-a-managed-resource.md)
