---
title: '/IGNOREIDL (Don&#39;t 將屬性處理至 MIDL) '
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.IgnoreEmbeddedIDL
- /ignoreidl
helpviewer_keywords:
- IGNOREIDL linker option
- -IGNOREIDL linker option
- /IGNOREIDL linker option
ms.assetid: 29514098-6a1c-4317-af2f-1dc268972780
ms.openlocfilehash: eac6209e0c34562254117d6ab9db5f47545037ea
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506884"
---
# <a name="ignoreidl-don39t-process-attributes-into-midl"></a>/IGNOREIDL (Don&#39;t 將屬性處理至 MIDL) 

```
/IGNOREIDL
```

## <a name="remarks"></a>備註

/IGNOREIDL 選項會指定不應將原始程式碼中的任何 [IDL 屬性](../../windows/attributes/idl-attributes.md) 處理到 .idl 檔。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 **Linker** 資料夾。

1. 按一下 [ **內嵌 IDL** ] 屬性頁。

1. 修改 [ **忽略內嵌 IDL** ] 屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreEmbeddedIDL%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)<br/>
[/IDLOUT (將 MIDL 輸出檔命名) ](idlout-name-midl-output-files.md)<br/>
[/TLBOUT (名稱。TLB 檔案) ](tlbout-name-dot-tlb-file.md)<br/>
[/MIDL (指定 MIDL 命令列選項) ](midl-specify-midl-command-line-options.md)<br/>
[建置屬性化程式](../../windows/attributes/cpp-attributes-com-net.md)
