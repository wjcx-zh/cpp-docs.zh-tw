---
title: /Zc:externConstexpr (啟用 extern constexpr 變數)
ms.date: 02/28/2018
f1_keywords:
- /Zc:externConstexpr
helpviewer_keywords:
- -Zc:externConstexpr compiler option (C++)
- extern constexpr variables (C++)
ms.assetid: 4da5e33a-2e4d-4ed2-8616-bd8f43265c27
ms.openlocfilehash: db5a8892bcc11538c3ff883a0e9a3a27db0ee14f
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502800"
---
# <a name="zcexternconstexpr-enable-extern-constexpr-variables"></a>`/Zc:externConstexpr` (啟用 extern constexpr 變數) 

**`/Zc:externConstexpr`** 編譯器選項會指示編譯器符合 c + + 標準，並允許變數的外部連結 **`constexpr`** 。 根據預設， **`constexpr`** 即使您指定關鍵字，Visual Studio 一律會提供變數內部連結 **`extern`** 。

## <a name="syntax"></a>Syntax

> **`/Zc:externConstexpr`**[**`-`**]

## <a name="remarks"></a>備註

**`/Zc:externConstexpr`** 編譯器選項會讓編譯器將外部連結套用至使用所宣告的變數 `extern constexpr` 。 在舊版 Visual Studio 中，如果 **`/Zc:externConstexpr-`** 指定了，Visual Studio 會將內部連結套用至 **`constexpr`** 變數，即使 **`extern`** 使用關鍵字也是一樣。 **`/Zc:externConstexpr`** 從 Visual Studio 2017 Update 15.6 開始，可以使用此選項。 和預設為關閉。 [`/permissive-`](permissive-standards-conformance.md)選項不會啟用 **`/Zc:externConstexpr`** 。

如果標頭檔包含宣告的變數 `extern constexpr` ，則必須標記，以便將 [`__declspec(selectany)`](../../cpp/selectany.md) 重複的宣告合併到連結二進位檔中的單一實例。 否則，您可能會看到連結器錯誤，例如 LNK2005，以違反單一定義規則。

### <a name="to-set-this-compiler-option-in-visual-studio"></a>在 Visual Studio 中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**  >  **C/c + +**  >  **命令列**] 屬性頁。

1. 將 **`/Zc:externConstexpr`** 或新增 **`/Zc:externConstexpr-`** 至 **其他選項：** 窗格。

## <a name="see-also"></a>另請參閱

[`/Zc` (一致性) ](zc-conformance.md)<br/>
[`auto` 關鍵 字](../../cpp/auto-cpp.md)
