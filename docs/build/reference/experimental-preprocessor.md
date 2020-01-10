---
title: /experimental：預處理器（啟用預處理器一致性模式）
description: 使用/experimental：預處理器編譯器選項，針對標準符合的預處理器啟用實驗性編譯器支援。
ms.date: 10/31/2019
f1_keywords:
- preprocessor
- /experimental:preprocessor
helpviewer_keywords:
- preprocessor conformance
- /experimental:preprocessor
- Enable preprocessor conformance mode
ms.openlocfilehash: cb1ac63d2c12083975139455d8625544cb419adf
ms.sourcegitcommit: 2362d15b5eb18d27773c3f7522da3d0eed9e2571
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73754050"
---
# <a name="experimentalpreprocessor-enable-preprocessor-conformance-mode"></a>/experimental：預處理器（啟用預處理器一致性模式）

此選項可讓實驗性的權杖型預處理器更緊密符合 c + + 11 標準，包括 C99 預處理器功能。 如需詳細資訊，請參閱[MSVC 實驗性預處理器總覽](../../preprocessor/preprocessor-experimental-overview.md)。

## <a name="syntax"></a>語法

> **/experimental：預處理器**[ **-** ]

## <a name="remarks"></a>備註

使用 **/experimental：預處理器**編譯器選項來啟用實驗性符合的預處理器。 您可以使用 **/experimental：預處理器-** 選項來明確指定傳統預處理器。

從 Visual Studio 2017 版15.8 開始，可以使用 **/experimental：預處理器**選項。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資訊，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [組態屬性] > [C/C++] > [命令列] 屬性頁。

1. 修改 [**其他選項**] 屬性以包含 **/experimental：預處理器**，然後選擇 **[確定]** 。

## <a name="see-also"></a>請參閱

[/Zc (一致性)](zc-conformance.md)
