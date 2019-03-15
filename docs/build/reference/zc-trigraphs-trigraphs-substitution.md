---
title: /Zc:trigraphs (三併詞替代)
ms.date: 03/06/2018
f1_keywords:
- /Zc
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Conformance compiler options
- Zc compiler options (C++)
ms.assetid: e3d6058f-400d-4966-a3aa-800cfdf69cbf
ms.openlocfilehash: 7a20123603030dfe719cd8990018f795df137981
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57814261"
---
# <a name="zctrigraphs-trigraphs-substitution"></a>/Zc:trigraphs (三併詞替代)

當 **/zc: trigraphs**指定，則編譯器會使用對應的標點符號字元取代三併詞的字元序列。

## <a name="syntax"></a>語法

> **/Zc:trigraphs**[**-**]

## <a name="remarks"></a>備註

A*三併詞*組成兩個連續的問號 ("？") 後面接著唯一的第三個字元。 C 語言標準支援三併詞使用的字元集不含某些標點符號字元的方便圖形表示的原始程式檔。 例如，當啟用三併詞時，編譯器會取代"??="使用 '#' 字元的三併詞。 透過 C + + 14，三併詞支援做為 in c。C + + 17 標準 c + + 語言中移除三併詞。 在 c + + 程式碼中， **/zc: trigraphs**編譯器選項啟用對應的標點符號字元取代三併詞序列。 **/Zc:trigraphs-** 停用三併詞替代。

**/Zc: trigraphs**選項預設為關閉，且選項不會受到影響時[/permissive--](permissive-standards-conformance.md)指定選項。

如需 C/c + + 三併詞和範例，示範如何使用三併詞的清單，請參閱 <<c0> [ 三併詞](../../c-language/trigraphs.md)。

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 **組態屬性** > **C/c + +** > **命令列**屬性頁。

1. 修改**其他選項**屬性，以包括 **/zc: trigraphs**或是 **/Zc:trigraphs-** ，然後選擇 **確定**。

## <a name="see-also"></a>另請參閱

[/Zc (一致性)](zc-conformance.md)<br/>
[三併詞](../../c-language/trigraphs.md)<br/>
