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
ms.openlocfilehash: 3f1b6526f51e5aaa48008792361d3e63249d9f16
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502852"
---
# <a name="midl-specify-midl-command-line-options"></a>/MIDL (指定 MIDL 命令列引數的選項)

指定 MIDL 命令列選項的回應檔

## <a name="syntax"></a>Syntax

> **/MIDL： \@ **<em>file</em>檔案

## <a name="arguments"></a>引數

*file*<br/>
包含 [MIDL 命令列選項](/windows/win32/Midl/general-midl-command-line-syntax)的檔案名。

## <a name="remarks"></a>備註

將 IDL 檔案轉換成 TLB 檔案的所有選項都必須在 *file*中提供;無法在連結器的命令列上指定 MIDL 命令列選項。 如果未指定/MIDL，則會叫用 MIDL 編譯器，但僅包含 IDL 檔案名和其他選項。

檔案應該每行包含一個 MIDL 命令列選項。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**  >  **連結器**  >  **內嵌 IDL** ] 屬性頁。

1. 修改 **MIDL 命令** 屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MidlCommandFile%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)<br/>
[/IDLOUT (將 MIDL 輸出檔命名) ](idlout-name-midl-output-files.md)<br/>
[/IGNOREIDL (不會將屬性處理至 MIDL) ](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/TLBOUT (名稱。TLB 檔案) ](tlbout-name-dot-tlb-file.md)<br/>
[建置屬性化程式](../../windows/attributes/cpp-attributes-com-net.md)
