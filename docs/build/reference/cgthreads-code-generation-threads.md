---
title: -cgthreads （程式碼產生執行緒） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /cgthreads
dev_langs:
- C++
helpviewer_keywords:
- /cgthreads compiler option (C++)
- -cgthreads compiler option (C++)
- cgthreads compiler option (C++)
- cgthreads
ms.assetid: 64bc768c-6caa-4baf-9dea-7cfa1ffb01c2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bb6849a4b30e903d05b5ac3d37fce558074110a5
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45719618"
---
# <a name="cgthreads-code-generation-threads"></a>/cgthreads (程式碼產生執行緒)

設定 cl.exe 執行緒的數目，以用於最佳化及程式碼產生。

## <a name="syntax"></a>語法

```
/cgthreads[1-8]
```

## <a name="arguments"></a>引數

*數字*<br/>
cl.exe 要使用的執行緒數目上限，範圍在 1 到 8 之間。

## <a name="remarks"></a>備註

**/Cgthreads**選項指定 cl.exe 執行緒的最大數目應使用以平行方式進行最佳化及程式碼產生階段的編譯。 請注意，可能會有之間沒有空格 **/cgthreads**而`number`引數。 根據預設，cl.exe 使用四個執行緒，如同 **/cgthreads4**所指定。 如果可以使用更多處理器核心，則較大的 `number` 值可以改善建置時間。 此選項會特別有用，當它結合[/GL （整個程式最佳化）](../../build/reference/gl-whole-program-optimization.md)。

針對建置可以指定多個層級的平行處理原則。 Msbuild.exe 參數 **/maxcpucount**指定可以平行執行的 MSBuild 處理序數目。 [/MP （使用多個處理序建置）](../../build/reference/mp-build-with-multiple-processes.md)編譯器旗標會指定同時編譯原始程式檔的 cl.exe 處理序數目。 **/Cgthreads**選項會指定每個 cl.exe 處理序所使用的執行緒數目。 由於處理器可同時執行的執行緒數目最多只能與處理器核心數目相同，因此同時針對所有這些選項指定較大的值不僅沒有什麼用處，反而可能適得其反。 如需如何平行建置專案的詳細資訊，請參閱[同時建置多個專案](/visualstudio/msbuild/building-multiple-projects-in-parallel-with-msbuild)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **組態屬性**， **C/c + +** 資料夾。

1. 選取 **命令列**屬性頁。

1. 修改**其他選項**屬性，以包括 **/cgthreads**`N`，其中`N`是從 1 到 8 的值，然後選取**確定**。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)