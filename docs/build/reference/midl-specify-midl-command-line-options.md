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
ms.openlocfilehash: ca172428943d2446490eeb10741966f5e8c9ea85
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492713"
---
# <a name="midl-specify-midl-command-line-options"></a>/MIDL (指定 MIDL 命令列引數的選項)

指定 MIDL 命令列選項的回應檔

## <a name="syntax"></a>語法

> **/MIDL:\@**  <em>file</em>

## <a name="arguments"></a>引數

*file*<br/>
包含[MIDL 命令列選項](/windows/win32/Midl/general-midl-command-line-syntax)之檔案的名稱。

## <a name="remarks"></a>備註

將 IDL 檔案轉換成 TLB 檔案的所有選項, 都必須在檔案中提供。無法在連結器的命令列上指定 MIDL 命令列選項。 如果未指定/MIDL, 則會叫用 MIDL 編譯器, 只使用 IDL 檔案名, 沒有其他選項。

檔案每行應該包含一個 MIDL 命令列選項。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性** > **連結器** > **內嵌 IDL**屬性] 頁面。

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
