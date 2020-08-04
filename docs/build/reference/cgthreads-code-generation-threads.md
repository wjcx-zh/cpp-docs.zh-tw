---
title: /cgthreads (程式碼產生執行緒)
ms.date: 07/31/2020
f1_keywords:
- /cgthreads
helpviewer_keywords:
- /cgthreads compiler option (C++)
- -cgthreads compiler option (C++)
- cgthreads compiler option (C++)
- cgthreads
ms.assetid: 64bc768c-6caa-4baf-9dea-7cfa1ffb01c2
ms.openlocfilehash: 319a42ab68f02df6019ff283f1039ef3d561c4a0
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520871"
---
# <a name="cgthreads-code-generation-threads"></a>`/cgthreads`（程式碼產生執行緒）

設定 cl.exe 執行緒的數目，以用於最佳化及程式碼產生。

## <a name="syntax"></a>語法

> **`/cgthreads1`**\
> **`/cgthreads2`**\
> **`/cgthreads3`**\
> **`/cgthreads4`**\
> **`/cgthreads5`**\
> **`/cgthreads6`**\
> **`/cgthreads7`**\
> **`/cgthreads8`**

## <a name="arguments"></a>引數

**`cgthreadsN`**\
cl.exe 要使用的執行緒數目上限，其中*N*是介於1到8之間的數位。

## <a name="remarks"></a>備註

**`cgthreads`** 選項會指定在編譯的優化和程式碼產生階段，cl.exe 平行使用的執行緒數目上限。 請注意， **`cgthreads`** 和*number*引數之間不能有空格。 根據預設，cl.exe 會使用四個執行緒，如同指定的一樣 **`/cgthreads4`** 。 如果有更多的處理器核心可供使用，*較大的數值可以*改善組建時間。 此選項與結合[ `/GL` （整個程式優化）](gl-whole-program-optimization.md)時特別有用。

可以為組建指定多個平行處理層級。 msbuild.exe 參數 **`/maxcpucount`** 會指定可平行執行的 MSBuild 進程數目。 [ `/MP` （使用多個進程建立）](mp-build-with-multiple-processes.md)編譯器旗標會指定同時編譯原始程式檔的 cl.exe 進程數目。 **`cgthreads`** 選項會指定每個 cl.exe 進程所使用的執行緒數目。 處理器每次只能執行與處理器核心數目相同的執行緒。 同時為所有這些選項指定較大的值並不實用，而且可以敵對。 如需如何平行建立專案的詳細資訊，請參閱[以平行方式建立多個專案](/visualstudio/msbuild/building-multiple-projects-in-parallel-with-msbuild)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**] [  >  **c/c + +**  >  **命令列**] 屬性頁。

1. 將 [**其他選項**] 屬性修改為 [包含 **`cgthreadsN`** ]，其中 *`N`* 是介於1到8的值，然後選取 **[確定]**。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜ <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> ＞。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
