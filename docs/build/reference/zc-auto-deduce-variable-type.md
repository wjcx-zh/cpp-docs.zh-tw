---
title: /Zc:auto (推算變數類型)
ms.date: 02/28/2018
f1_keywords:
- /Zc:auto
helpviewer_keywords:
- -Zc compiler options (C++)
- Deduce variable type (C++)
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 5f5bc102-44c3-4688-bbe1-080594dcee5c
ms.openlocfilehash: 6bb1c8f2b14c483cbd46ecb6534a33db020e23e0
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502827"
---
# <a name="zcauto-deduce-variable-type"></a>`/Zc:auto` (推算變數類型) 

**`/Zc:auto`** 編譯器選項會指示編譯器如何使用[ `auto` 關鍵字](../../cpp/auto-cpp.md)來宣告變數。 如果您指定預設選項， **`/Zc:auto`** 則編譯器會從其初始化運算式會推算宣告變數的類型。 如果指定 **`/Zc:auto-`** ，則編譯器會將變數配置給自動儲存類別。

## <a name="syntax"></a>Syntax

> **`/Zc:auto`**[**`-`**]

## <a name="remarks"></a>備註

C + + 標準針對關鍵字定義了原始和修訂的意義 **`auto`** 。 在 Visual Studio 2010 之前，關鍵字會在自動儲存類別中宣告變數;也就是具有本機存留期的變數。 從 Visual Studio 2010 開始，關鍵字會從宣告的初始化運算式會推算變數的型別。 使用 **`/Zc:auto`** 編譯器選項，告訴編譯器使用修改過的關鍵字的意義 **`auto`** 。 此 **`/Zc:auto`** 選項預設為開啟。 [`/permissive-`](permissive-standards-conformance.md)選項不會變更的預設設定 **`/Zc:auto`** 。

如果您使用 **`auto`** 關鍵字與目前的編譯器選項相衝突，則編譯器會發出適當的診斷訊息 **`/Zc:auto`** 。 如需詳細資訊，請參閱[ `auto` 關鍵字](../../cpp/auto-cpp.md)。 如需 Visual C++ 之一致性問題的詳細資訊，請參閱 [非標準行為](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-visual-studio"></a>在 Visual Studio 中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**  >  **C/c + +**  >  **命令列**] 屬性頁。

1. 將 **`/Zc:auto`** 或新增 **`/Zc:auto-`** 至 **其他選項：** 窗格。

## <a name="see-also"></a>另請參閱

[`/Zc` (一致性) ](zc-conformance.md)<br/>
[`auto` 關鍵 字](../../cpp/auto-cpp.md)
