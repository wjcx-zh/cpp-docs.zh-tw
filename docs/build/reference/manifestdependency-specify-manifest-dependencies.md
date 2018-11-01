---
title: /MANIFESTDEPENDENCY (指定資訊清單相依性)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.AdditionalManifestDependencies
helpviewer_keywords:
- MANIFESTDEPENDENCY linker option
- /MANIFESTDEPENDENCY linker option
- -MANIFESTDEPENDENCY linker option
ms.assetid: e4b68313-33a2-4c3e-908e-ac2b9f7d6a73
ms.openlocfilehash: aba4bd1b36bfda35be9e567851596fbedecf38ca
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50654908"
---
# <a name="manifestdependency-specify-manifest-dependencies"></a>/MANIFESTDEPENDENCY (指定資訊清單相依性)

```
/MANIFESTDEPENDENCY:manifest_dependency
```

## <a name="remarks"></a>備註

/MANIFESTDEPENDENCY 可讓您指定將放入的屬性\<相依性 > 區段的資訊清單檔案。

請參閱[/MANIFEST （建立-並存組件資訊清單）](../../build/reference/manifest-create-side-by-side-assembly-manifest.md)如需如何建立資訊清單檔案的詳細資訊。

如需詳細資訊\<相依性 > 區段的資訊清單檔案中，請參閱[發行者組態檔](/windows/desktop/SbsCs/publisher-configuration-files)。

/MANIFESTDEPENDENCY 資訊可以傳遞給連結器在兩種方式之一：

- 直接在命令列上 （或在回應檔案中） 與 /MANIFESTDEPENDENCY。

- 透過[註解](../../preprocessor/comment-c-cpp.md)pragma。

下列範例示範 /MANIFESTDEPENDENCY 註解 pragma，透過傳遞

```cpp
#pragma comment(linker, "\"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"")
```

這會導致資訊清單檔中的下列項目：

```xml
<dependency>
  <dependentAssembly>
    <assemblyIdentity type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*' />
  </dependentAssembly>
</dependency>
```

相同的 /MANIFESTDEPENDENCY 註解可以傳遞在命令列，如下所示：

```cmd
"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"
```

連結器會收集 /MANIFESTDEPENDENCY 註解、 排除重複的項目，並再將產生的 XML 字串新增至資訊清單檔案。  如果連結器找到衝突的項目，資訊清單檔案會變成損毀，而且應用程式將無法啟動 （項目可能會新增至事件記錄檔，表示失敗的來源）。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **組態屬性** > **連結器** > **資訊清單檔案**屬性頁。

1. 修改**額外的資訊清單相依性**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

1. 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalManifestDependencies%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)