---
title: '/Zc：預處理器 (啟用預處理器一致性模式) '
description: 使用/Zc：預處理器編譯器選項可針對標準的符合預處理器啟用編譯器支援。
ms.date: 09/10/2020
f1_keywords:
- preprocessor
- /Zc:preprocessor
helpviewer_keywords:
- preprocessor conformance
- /Zc:preprocessor
- Enable preprocessor conformance mode
ms.openlocfilehash: 356434e4892966b9a9304021dd5d8770dcc2f8b1
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90042899"
---
# <a name="zcpreprocessor-enable-preprocessor-conformance-mode"></a>`/Zc:preprocessor` (啟用預處理器一致性模式) 

此選項會啟用以權杖為基礎的預處理器，其符合 C99 和 c + + 11 及更新的標準。 如需詳細資訊，請參閱 [MSVC 新的預處理器總覽](../../preprocessor/preprocessor-experimental-overview.md)。

## <a name="syntax"></a>語法

> **`/Zc:preprocessor`**[**-**]

## <a name="remarks"></a>備註

使用 **`/Zc:preprocessor`** 編譯器選項來啟用符合規範的預處理器。 您可以使用 **`/Zc:preprocessor-`** 選項明確指定傳統 (不符合規範) 預處理器。

**`/Zc:preprocessor`** 從 Visual Studio 2019 16.5 版開始，可以使用此選項。 從 Visual Studio 2017 15.8 版開始的 Visual Studio 版本中，提供了較早、不完整的新預處理器選項版本。 如需詳細資訊，請參閱 [`/experimental:preprocessor`](experimental-preprocessor.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**  >  **C/c + +**  >  **命令列**] 屬性頁。

1. 修改 [ **其他選項** ] 屬性以包含 *`/Zc:preprocessor`* ，然後選擇 **[確定]**。

## <a name="see-also"></a>另請參閱

[/Zc (一致性)](zc-conformance.md)
