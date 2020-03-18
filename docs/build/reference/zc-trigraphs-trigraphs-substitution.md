---
title: /Zc:trigraphs (三併詞替代)
ms.date: 03/06/2018
f1_keywords:
- /Zc:trigraphs
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Conformance compiler options
- Zc compiler options (C++)
ms.assetid: e3d6058f-400d-4966-a3aa-800cfdf69cbf
ms.openlocfilehash: 0e4c98e09551d39e3ff7978767b21f1d2c5bb318
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438660"
---
# <a name="zctrigraphs-trigraphs-substitution"></a>/Zc:trigraphs (三併詞替代)

當指定 **/zc：三並詞**時，編譯器會使用對應的標點符號字元來取代三並詞字元序列。

## <a name="syntax"></a>語法

> **/Zc：三並詞**[ **-** ]

## <a name="remarks"></a>備註

*三並詞*包含兩個連續的問號（"？？"），後面接著唯一的第三個字元。 C 語言標準支援三並詞原始程式檔，這些來源檔案使用的字元集不含某些標點符號字元的方便圖形表示。 例如，當啟用三並詞時，編譯器會取代 "？？= "使用 ' # ' 字元三並詞。 透過 c + + 14，支援三並詞，如 C 所示。C + + 17 標準會從C++語言中移除三並詞。 在C++程式碼中， **/zc：三並詞**編譯器選項可依據對應的標點符號字元來替代三並詞序列。 **/Zc：三並詞-** 停用三並詞替代。

**/Zc：三並詞**選項預設為關閉，而且當指定[/permissive-](permissive-standards-conformance.md)選項時，此選項不會受到影響。

如需 C/C++三並詞的清單，以及顯示如何使用三並詞的範例，請參閱[三並詞](../../c-language/trigraphs.md)。

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資訊，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [組態屬性] > [C/C++] > [命令列] 屬性頁。

1. 修改 [**其他選項**] 屬性以包含 **/zc：三並詞**或 **/zc：三並詞**，然後選擇 **[確定]** 。

## <a name="see-also"></a>另請參閱

[/Zc (一致性)](zc-conformance.md)<br/>
[三併詞](../../c-language/trigraphs.md)<br/>
