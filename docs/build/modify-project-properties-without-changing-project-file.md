---
title: HOW TO：修改C++專案屬性和目標，而不需要變更專案檔
ms.date: 11/28/2018
helpviewer_keywords:
- project properties [C++], modifying outside project file
ms.openlocfilehash: ad527d8ee69a1786be7d325571f9c9ac4f9a8574
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273335"
---
# <a name="how-to-modify-c-project-properties-and-targets-without-changing-the-project-file"></a>HOW TO：修改C++專案屬性和目標，而不需要變更專案檔

您可以從 MSBuild 命令提示字元覆寫專案屬性和目標，而不需變更專案檔。 當您想要暫時或偶爾套用某些屬性時，這非常有用。 它會假設需要一些 MSBuild 知識。 如需詳細資訊，請參閱 [MSBUild](https://docs.microsoft.com/visualstudio/msbuild/msbuild)。

> [!IMPORTANT]
> 您可以使用 Visual Studio 的 XML 編輯器或任何文字編輯器來建立 .props 或 .targets 檔案。 請勿使用此案例中的 [屬性管理員]，因為它會將屬性新增至專案檔。

若要覆寫專案屬性：

1. 建立 .props 檔案，以指定您想要覆寫的屬性。

1. 從命令提示字元：設定 ForceImportBeforeCppTargets="C:\sources\my_props.props"

若要覆寫專案目標：

1. 建立具有其實作或特定目標的 .targets 檔案

2. 從命令提示字元：設定 ForceImportAfterCppTargets ="C:\sources\my_target.targets"

您也可以使用 /p: 選項，在 msbuild 命令列上設定其中一個選項：

```cmd
> msbuild myproject.sln /p:ForceImportBeforeCppTargets="C:\sources\my_props.props"
> msbuild myproject.sln /p:ForceImportAfterCppTargets="C:\sources\my_target.targets"
```

以這種方式覆寫屬性和目標，相當於將下列匯入項目新增至方案中的所有 .vcxproj 檔案：

```cmd
<Import Project=="C:\sources\my_props.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
<Import Project==" C:\sources\my_target.targets"" />
```
