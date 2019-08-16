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
ms.openlocfilehash: 43239efe70cc555d1a7e03c5d67e99e40ccd480e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492699"
---
# <a name="manifestdependency-specify-manifest-dependencies"></a>/MANIFESTDEPENDENCY (指定資訊清單相依性)

```
/MANIFESTDEPENDENCY:manifest_dependency
```

## <a name="remarks"></a>備註

/MANIFESTDEPENDENCY 可讓您指定將放入\<資訊清單檔之相依性 > 區段的屬性。

如需如何建立資訊清單檔的詳細資訊, 請參閱[/MANIFEST (建立並存組件資訊清單)](manifest-create-side-by-side-assembly-manifest.md) 。

如需資訊清單檔案\<之相依性 > 區段的詳細資訊, 請參閱[發行者設定檔](/windows/win32/SbsCs/publisher-configuration-files)。

/MANIFESTDEPENDENCY 資訊可以透過下列兩種方式的其中一種傳遞至連結器:

- 直接在命令列上 (或在回應檔中) 使用/MANIFESTDEPENDENCY。

- 透過[comment](../../preprocessor/comment-c-cpp.md) pragma。

下列範例顯示透過 pragma 傳遞的/MANIFESTDEPENDENCY 批註,

```cpp
#pragma comment(linker, "\"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"")
```

這會產生資訊清單檔中的下列專案:

```xml
<dependency>
  <dependentAssembly>
    <assemblyIdentity type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*' />
  </dependentAssembly>
</dependency>
```

您可以在命令列上傳遞相同的/MANIFESTDEPENDENCY 批註, 如下所示:

```cmd
"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"
```

連結器會收集/MANIFESTDEPENDENCY 批註、排除重複的專案, 然後將產生的 XML 字串新增至資訊清單檔。  如果連結器找到衝突的專案, 資訊清單檔案會變成損毀, 且應用程式將無法啟動 (可能會將專案新增至事件記錄檔, 指出失敗的來源)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定] [**屬性** > ] [**連結器** > **資訊清單**檔案] 屬性頁。

1. 修改 [**其他資訊清單**相依性] 屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

1. 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalManifestDependencies%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
