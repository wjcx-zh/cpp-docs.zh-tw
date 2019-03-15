---
title: /CLRIMAGETYPE (指定 CLR 映像類型)
ms.date: 11/04/2016
f1_keywords:
- /CLRIMAGETYPE
- VC.Project.VCLinkerTool.CLRImageType
helpviewer_keywords:
- /CLRIMAGETYPE linker option
- -CLRIMAGETYPE linker option
ms.assetid: 04c60ee6-9dd7-4391-bc03-6926ad0fa116
ms.openlocfilehash: b2a6df0f778ba079bffefeeacdad22cb398a529a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820672"
---
# <a name="clrimagetype-specify-type-of-clr-image"></a>/CLRIMAGETYPE (指定 CLR 映像類型)

設定 CLR 映像類型，連結的映像中。

## <a name="syntax"></a>語法

> **/CLRIMAGETYPE:**{**IJW**|**PURE**|**SAFE**|**SAFE32BITPREFERRED**}

## <a name="remarks"></a>備註

連結器接受原生物件，並也 MSIL 物件所編譯的使用[/clr](clr-common-language-runtime-compilation.md)。 **/Clr: pure**並 **/clr: safe**編譯器選項在 Visual Studio 2015 中已被取代，並不支援在 Visual Studio 2017。 在相同組建中傳遞混合物件時，所產生輸出檔案的可驗證性將預設為同等於輸入模組最低層級的可驗證性。 例如，如果您傳遞原生映像和混合的模式映像 (使用編譯 **/clr**)，產生的映像將會是混合的模式映像。

您可以使用 **/CLRIMAGETYPE**指定的可驗證性較低層級，如果您的需要。

如需如何判斷檔案之 CLR 映像類型的資訊，請參閱 [/CLRHEADER](clrheader.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 展開 [組態屬性] 節點。

1. 依序展開**連結器**節點。

1. 選取 **進階**屬性頁。

1. 修改**CLR 映像類型**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

1. 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRImageType%2A>。

## <a name="see-also"></a>另請參閱

- [MSVC 連結器參考](linking.md)
- [MSVC 連結器選項](linker-options.md)
