---
title: /GX (啟用例外狀況處理)
ms.date: 11/04/2016
f1_keywords:
- /gx
helpviewer_keywords:
- exception handling, enabling
- /GX compiler option [C++]
- -GX compiler option [C++]
- cl.exe compiler, exception handling
- enable exception handling compiler option [C++]
- GX compiler option [C++]
ms.assetid: 933b43ba-de77-4ff8-a48b-7074de90bc1c
ms.openlocfilehash: 43be8f6d0f080f0d85568ce5b089751fc68f0e8e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291999"
---
# <a name="gx-enable-exception-handling"></a>/GX (啟用例外狀況處理)

已取代。 啟用同步例外狀況處理使用函式假設宣告可透過`extern "C"`絕不會擲回例外狀況。

## <a name="syntax"></a>語法

```
/GX
```

## <a name="remarks"></a>備註

**/GX**已被取代。 使用對等[/EHsc](eh-exception-handling-model.md)選項。 如需已被取代的編譯器選項的清單，請參閱 <<c0>  **已取代及移除的編譯器選項**一節[依分類排列的編譯器選項](compiler-options-listed-by-category.md)。

根據預設， **/EHsc**，則相當於 **/GX**，是使用 Visual Studio 開發環境進行編譯時作用中。 使用命令列工具時，會指定沒有例外狀況處理。 這相當於 **/GX-**。

如需詳細資訊，請參閱 < [ C++例外狀況處理](../../cpp/cpp-exception-handling.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 在 [導覽] 窗格中，選擇**組態屬性**， **C /C++**，**命令列**。

1. 在 [其他選項]  方塊中，輸入編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[/EH (例外狀況處理模型)](eh-exception-handling-model.md)
