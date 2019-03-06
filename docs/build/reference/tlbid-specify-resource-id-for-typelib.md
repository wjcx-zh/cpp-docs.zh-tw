---
title: /TLBID (指定 TypeLib 的資源 ID)
ms.date: 11/04/2016
f1_keywords:
- /tlbid
- VC.Project.VCLinkerTool.TypeLibraryResourceID
helpviewer_keywords:
- tlb files, specifying resource ID
- -TLBID linker option
- .tlb files, specifying resource ID
- /TLBID linker option
- TLBID linker option
- type libraries, specifying resource ID
ms.assetid: 434b28a2-4656-4d52-ac82-8b18bf486fb2
ms.openlocfilehash: b65ef73e2c7802b960b8480fff83c96fbe869293
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426468"
---
# <a name="tlbid-specify-resource-id-for-typelib"></a>/TLBID (指定 TypeLib 的資源 ID)

```
/TLBID:id
```

## <a name="arguments"></a>引數

*id*<br/>
連結器建立的型別程式庫使用者指定的值。 它會覆寫預設的資源識別碼為 1。

## <a name="remarks"></a>備註

在編譯時使用屬性的程式，連結器會建立型別程式庫。 連結器會指派給類型程式庫的資源識別碼為 1。

如果此資源 ID 衝突與其中一個現有的資源，您可以使用 /TLBID 來指定另一個識別碼。 您可以傳遞給的值範圍`id`是 1 到 65535。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 **連結器**資料夾。

1. 按一下 **內嵌 IDL**屬性頁。

1. 修改**TypeLib 資源 ID**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

1. 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryResourceID%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)
