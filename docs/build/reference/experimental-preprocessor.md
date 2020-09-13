---
title: '/experimental：預處理器 (啟用預處理器一致性模式) '
description: 使用/experimental：預處理器編譯器選項可針對標準的符合預處理器啟用實驗性編譯器支援。
ms.date: 09/10/2020
f1_keywords:
- preprocessor
- /experimental:preprocessor
helpviewer_keywords:
- preprocessor conformance
- /experimental:preprocessor
- Enable preprocessor conformance mode
ms.openlocfilehash: 9a98289434e7154d2ec8b8753d990876a8218acf
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90042091"
---
# <a name="experimentalpreprocessor-enable-preprocessor-conformance-mode"></a>`/experimental:preprocessor` (啟用預處理器一致性模式) 

此選項自 Visual Studio 2019 16.5 版開始已淘汰，並由 [`/Zc:preprocessor`](zc-preprocessor.md) 編譯器選項取代。 **`/experimental:preprocessor`** 啟用以權杖為基礎的實驗性，更緊密符合 c + + 11 標準，包括 C99 預處理器功能。 如需詳細資訊，請參閱 [MSVC 新的預處理器總覽](../../preprocessor/preprocessor-experimental-overview.md)。

## <a name="syntax"></a>語法

> **`/experimental:preprocessor`**\[**`-`**]

## <a name="remarks"></a>備註

使用 **`/experimental:preprocessor`** 編譯器選項可啟用實驗性合格的預處理器。 您可以使用 **`/experimental:preprocessor-`** 選項來明確指定傳統的預處理器。

**`/experimental:preprocessor`** 從 Visual Studio 2017 15.8 版開始，可以使用此選項。 從 Visual Studio 2019 16.5 版開始，新的預處理器已完成，並可在 [`/Zc:preprocessor`](zc-preprocessor.md) 編譯器選項下取得。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**  >  **C/c + +**  >  **命令列**] 屬性頁。

1. 修改 [ **其他選項** ] 屬性以包含 *`/experimental:preprocessor`* ，然後選擇 **[確定]**。

## <a name="see-also"></a>另請參閱

[/Zc (一致性)](zc-conformance.md)
