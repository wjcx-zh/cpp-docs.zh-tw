---
title: '/Zc: externconstexpr （啟用 extern constexpr 變數）'
ms.date: 02/28/2018
f1_keywords:
- /Zc:externConstexpr
helpviewer_keywords:
- -Zc:externConstexpr compiler option (C++)
- extern constexpr variables (C++)
ms.assetid: 4da5e33a-2e4d-4ed2-8616-bd8f43265c27
ms.openlocfilehash: a9efa2fa191cbdda99e057ac9329d79bc598743c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50510691"
---
# <a name="zcexternconstexpr-enable-extern-constexpr-variables"></a>/Zc: externconstexpr （啟用 extern constexpr 變數）

**/Zc: externconstexpr**編譯器選項會告知編譯器符合 c + + 標準，並允許外部連結的`constexpr`變數。 根據預設，Visual Studio 一律提供`constexpr`變數內部連結，即使您指定`extern`關鍵字。

## <a name="syntax"></a>語法

> **/Zc:externConstexpr**[**-**]

## <a name="remarks"></a>備註

**/Zc: externconstexpr**編譯器選項可讓編譯器將外部連結所宣告的變數至`extern constexpr`。 在舊版的 Visual Studio，並依預設或如果 **/Zc:externConstexpr-** 指定時，Visual Studio 會套用到的內部連結`constexpr`變數，即使`extern`使用關鍵字。 **/Zc: externconstexpr**選項是從 Visual Studio 2017 Update 15.6 中推出。 和預設為關閉。 [/Permissive--](permissive-standards-conformance.md)選項不會啟用 **/zc: externconstexpr**。

如果標頭檔包含宣告的變數`extern constexpr`，它必須標示[__declspec （selectany)](../../cpp/selectany.md)才能合併連結二進位檔中的單一執行個體中的重複的宣告。 否則，您可能會看到連結器錯誤，例如 LNK2005，一個定義規則的違規。

### <a name="to-set-this-compiler-option-in-visual-studio"></a>在 Visual Studio 中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **組態屬性** > **C/c + +** > **命令列**屬性頁。

1. 新增 **/zc: externconstexpr**或是 **/Zc:externConstexpr-** 來**其他選項：** 窗格。

## <a name="see-also"></a>另請參閱

[/Zc (一致性)](../../build/reference/zc-conformance.md)<br/>
[auto 關鍵字](../../cpp/auto-keyword.md)