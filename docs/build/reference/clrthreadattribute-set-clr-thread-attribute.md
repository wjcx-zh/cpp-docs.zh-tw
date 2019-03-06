---
title: /CLRTHREADATTRIBUTE (設定 CLR 執行緒屬性)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.CLRThreadAttribute
helpviewer_keywords:
- /CLRTHREADATTRIBUTE linker option
- -CLRTHREADATTRIBUTE linker option
ms.assetid: 4907e9ef-5031-446c-aecf-0a0b32fae1e8
ms.openlocfilehash: f1a637f74cf1da608149779821a25340d35f8739
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417147"
---
# <a name="clrthreadattribute-set-clr-thread-attribute"></a>/CLRTHREADATTRIBUTE (設定 CLR 執行緒屬性)

明確指定 CLR 程式進入點的執行緒屬性。

## <a name="syntax"></a>語法

```
/CLRTHREADATTRIBUTE:{STA|MTA|NONE}
```

#### <a name="parameters"></a>參數

**MTA**<br/>
套用 MTAThreadAttribute 屬性至您的程式進入點。

**NONE**<br/>
與不指定 /CLRTHREADATTRIBUTE 相同。  可讓 Common Language Runtime (CLR) 設定預設的執行緒屬性。

**STA**<br/>
套用 STAThreadAttribute 屬性至您的程式進入點。

## <a name="remarks"></a>備註

設定執行緒屬性才有效時建置的.exe，因為它影響到主執行緒的進入點。

如果您使用的預設進入點 （main 或 wmain，例如） 執行緒模型使用指定 /CLRTHREADATTRIBUTE 或加上就會忽略執行緒屬性 （STAThreadAttribute 或 MTAThreadAttribute） 上的預設進入函式。

如果您使用非預設進入點時，指定使用 /CLRTHREADATTRIBUTE，或放置執行緒非預設項目函式屬性，然後再指定非預設進入點的執行緒模型[/ENTRY](../../build/reference/entry-entry-point-symbol.md).

如果指定 /CLRTHREADATTRIBUTE 的執行緒模型不一致的原始程式碼中指定的執行緒模型，連結器將會忽略 /CLRTHREADATTRIBUTE，並套用在原始程式碼中指定的執行緒模型。

它可能需要您使用單一執行緒，比方說，如果您的 CLR 程式裝載會使用單一執行緒 COM 物件。  如果您的 CLR 程式使用多執行緒處理，它將無法裝載使用單一執行緒的 COM 物件。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 展開 [組態屬性] 節點。

1. 依序展開**連結器**節點。

1. 選取 **進階**屬性頁。

1. 修改**CLR 執行緒屬性**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

1. 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRThreadAttribute%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)
