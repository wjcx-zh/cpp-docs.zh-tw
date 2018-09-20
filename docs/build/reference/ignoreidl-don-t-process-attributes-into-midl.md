---
title: -IGNOREIDL (Don&#39;t 屬性處理至 MIDL) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.IgnoreEmbeddedIDL
- /ignoreidl
dev_langs:
- C++
helpviewer_keywords:
- IGNOREIDL linker option
- -IGNOREIDL linker option
- /IGNOREIDL linker option
ms.assetid: 29514098-6a1c-4317-af2f-1dc268972780
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9c06e06633e6d0a990c72ebb65a4bd999df45a55
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46406668"
---
# <a name="ignoreidl-don39t-process-attributes-into-midl"></a>/IGNOREIDL (Don&#39;t 屬性處理至 MIDL)

```
/IGNOREIDL
```

## <a name="remarks"></a>備註

/IGNOREIDL 選項指定任何[IDL 屬性](../../windows/idl-attributes.md)來源中的程式碼不應處理到.idl 檔。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 **連結器**資料夾。

1. 按一下 **內嵌 IDL**屬性頁。

1. 修改**忽略內嵌 IDL**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreEmbeddedIDL%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)<br/>
[/IDLOUT (命名 MIDL 輸出檔)](../../build/reference/idlout-name-midl-output-files.md)<br/>
[/TLBOUT (命名 .TLB 檔)](../../build/reference/tlbout-name-dot-tlb-file.md)<br/>
[/MIDL (指定 MIDL 命令列選項)](../../build/reference/midl-specify-midl-command-line-options.md)<br/>
[建置屬性化程式](../../windows/building-an-attributed-program.md)