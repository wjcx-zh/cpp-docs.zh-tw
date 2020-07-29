---
title: /Zc:trigraphs (三併詞替代)
description: 一種 Microsoft c + + 編譯器選項，可控制三並詞的一致性支援。
ms.date: 07/25/2020
f1_keywords:
- /Zc:trigraphs
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Conformance compiler options
- Zc compiler options (C++)
ms.assetid: e3d6058f-400d-4966-a3aa-800cfdf69cbf
ms.openlocfilehash: e24f3d2f0064c3acc04b4c3774f47f6e442d5ddd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211849"
---
# <a name="zctrigraphs-trigraphs-substitution"></a>`/Zc:trigraphs`（三並詞替代）

當 **`/Zc:trigraphs`** 指定時，編譯器會使用對應的標點符號字元來取代三並詞字元序列。

## <a name="syntax"></a>語法

> **`/Zc:trigraphs`**[**`-`**]

## <a name="remarks"></a>備註

*三並詞*包含兩個連續的問號（ **`??`** ），後面接著唯一的第三個字元。 C 語言標準支援三並詞原始程式檔，這些來源檔案使用的字元集不含某些標點符號字元的方便圖形表示。 例如，啟用三並詞時，編譯器會 **`??=`** 使用字元來取代三並詞 **`#`** 。 透過 c + + 14，支援三並詞，如 C 所示。C + + 17 標準會移除 c + + 語言的三並詞。 在 c + + 程式碼中， **`/Zc:trigraphs`** 編譯器選項可讓您依對應的標點符號字元來替代三並詞序列。 **`/Zc:trigraphs-`** 停用三並詞替代。

此 **`/Zc:trigraphs`** 選項預設為關閉，而且在指定選項時，不會影響此選項 [`/permissive-`](permissive-standards-conformance.md) 。

如需 C/c + + 三並詞的清單，以及顯示如何使用三並詞的範例，請參閱[三並詞](../../c-language/trigraphs.md)。

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**] [  >  **c/c + +**  >  **命令列**] 屬性頁。

1. 修改 [**其他選項**] 屬性以包含 **`/Zc:trigraphs`** 或 **`/Zc:trigraphs-`** ，然後選擇 **[確定]**。

## <a name="see-also"></a>另請參閱

[`/Zc`標準](zc-conformance.md)<br/>
[三併詞](../../c-language/trigraphs.md)
