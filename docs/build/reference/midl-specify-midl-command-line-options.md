---
title: /MIDL (指定 MIDL 命令列引數的選項)
ms.date: 09/05/2018
f1_keywords:
- /midl
- VC.Project.VCLinkerTool.MidlCommandFile
helpviewer_keywords:
- -MIDL linker option
- MIDL
- /MIDL linker option
- MIDL linker option
- MIDL, command line options
ms.assetid: 22dc259e-b34c-4ed3-a380-4beb734482c1
ms.openlocfilehash: 584958ac51bdc491ad1bdd16117ecaad6e000ec7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321068"
---
# <a name="midl-specify-midl-command-line-options"></a>/MIDL (指定 MIDL 命令列引數的選項)

指定 MIDL 命令列選項的回應檔案

## <a name="syntax"></a>語法

> **/MIDL:\@**<em>file</em>

## <a name="arguments"></a>引數

*file*<br/>
包含的檔案名稱[MIDL 命令列選項](/windows/desktop/Midl/general-midl-command-line-syntax)。

## <a name="remarks"></a>備註

針對至 TLB 檔案的 IDL 檔案轉換的所有選項必須都列入*檔案*;連結器的命令列上，就無法指定 MIDL 命令列選項。 如果未指定 /MIDL，MIDL 編譯器會叫用的 IDL 檔名和任何其他選項。

此檔案應包含每行一個 MIDL 命令列選項。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 選取 **組態屬性** > **連結器** > **內嵌 IDL**屬性頁。

1. 修改**MIDL 命令**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MidlCommandFile%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)<br/>
[/IDLOUT (命名 MIDL 輸出檔)](idlout-name-midl-output-files.md)<br/>
[/IGNOREIDL (不要將屬性處理至 MIDL 中)](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/TLBOUT (命名 .TLB 檔)](tlbout-name-dot-tlb-file.md)<br/>
[建置屬性化程式](../../windows/building-an-attributed-program.md)
