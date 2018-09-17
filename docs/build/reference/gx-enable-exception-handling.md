---
title: -GX （啟用例外狀況處理） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /gx
dev_langs:
- C++
helpviewer_keywords:
- exception handling, enabling
- /GX compiler option [C++]
- -GX compiler option [C++]
- cl.exe compiler, exception handling
- enable exception handling compiler option [C++]
- GX compiler option [C++]
ms.assetid: 933b43ba-de77-4ff8-a48b-7074de90bc1c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 095db3db73f2be4012efe39f3b8cd8e645ad46c3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718317"
---
# <a name="gx-enable-exception-handling"></a>/GX (啟用例外狀況處理)

已取代。 啟用同步例外狀況處理使用函式假設宣告可透過`extern "C"`絕不會擲回例外狀況。

## <a name="syntax"></a>語法

```
/GX
```

## <a name="remarks"></a>備註

**/GX**已被取代。 使用對等[/EHsc](../../build/reference/eh-exception-handling-model.md)選項。 如需已被取代的編譯器選項的清單，請參閱 <<c0>  **已取代及移除的編譯器選項**一節[依分類排列的編譯器選項](../../build/reference/compiler-options-listed-by-category.md)。

根據預設， **/EHsc**，則相當於 **/GX**，是使用 Visual Studio 開發環境進行編譯時作用中。 使用命令列工具時，會指定沒有例外狀況處理。 這相當於 **/GX-**。

如需詳細資訊，請參閱 < [c + + 例外狀況處理](../../cpp/cpp-exception-handling.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 在 [導覽] 窗格中，選擇**組態屬性**， **C/c + +**，**命令列**。

1. 在 [其他選項]  方塊中，輸入編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)<br/>
[/EH (例外狀況處理模型)](../../build/reference/eh-exception-handling-model.md)